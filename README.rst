Project description
django-ns-ratelimit is django app for limit requests using rate limit class, decorators and middleware.

Contents

1 Main features

2 Installation

2.1 macOS

2.2 Linux

2.3 Windows, etc.

2.4 Development version

2.5 Python version

3 Usage

3.1 Examples

4 HTTP method

5 Request URL

5.1 Querystring parameters

5.2 URL shortcuts for localhost

5.3 Custom default scheme

6 Request items

6.1 Escaping rules

7 JSON

7.1 Default behaviour

7.2 Explicit JSON

7.3 Non-string JSON fields

8 Forms

8.1 Regular forms

8.2 File upload forms

9 HTTP headers

9.1 Default request headers

9.2 Empty headers and header un-setting

10 Authentication

10.1 Basic auth

10.2 Digest auth

10.3 Password prompt

10.4 .netrc

10.5 Auth plugins

11 HTTP redirects

11.1 Follow Location

11.2 Showing intermediary redirect responses

11.3 Limiting maximum redirects followed

12 Proxies

12.1 Environment variables

12.2 SOCKS

13 HTTPS

13.1 Server SSL certificate verification

13.2 Custom CA bundle

13.3 Client side SSL certificate

13.4 SSL version

13.5 SNI (Server Name Indication)

14 Output options

14.1 What parts of the HTTP exchange should be printed

14.2 Viewing intermediary requests/responses

14.3 Conditional body download

15 Redirected Input

15.1 Request data from a filename

16 Terminal output

16.1 Colors and formatting

16.2 Binary data

17 Redirected output

18 Download mode

18.1 Downloaded file name

18.2 Piping while downloading

18.3 Resuming downloads

18.4 Other notes

19 Streamed responses

19.1 Disabling buffering

19.2 Examples use cases

20 Sessions

20.1 Named sessions

20.2 Anonymous sessions

20.3 Readonly session

21 Config

21.1 Config file location

21.2 Configurable options

21.2.1 default_options

21.2.2 __meta__

21.3 Un-setting previously specified options

22 Scripting

22.1 Best practices

23 Meta

23.1 Interface design

23.2 User support

23.3 Related projects

23.3.1 Dependencies

23.3.2 HTTPie friends

23.4 Contributing

23.5 Change log

23.6 Artwork

23.7 Licence

23.8 Authors

2 Installation

$ pip install -i https://test.pypi.org/simple/ django-ns-ratelimit==1.0


3 Usage

3.1 Periods in format:
    S: For seconds
    M: For minutes
    H: For hour
    D: For Day

    e.g: "10S" "1M" "1D"

3.2 Decorators
3.2.1 user_method_ratelimit:
Used for user specific request rate limiting for class base apis

$ class SampleView(APIView):
    @user_method_ratelimit(5, "1M")
    def get(self, request):
        pass

3.2.2 anon_method_ratelimit:
Used for Anonymous user requests rate limiting for class base apis

$ class SampleView(APIView):
    @anon_method_ratelimit(5, "1M")
    def get(self, request):
        pass

3.2.3 user_func_ratelimit:
Used for user specific request rate limiting for function base apis

$ class SampleView(APIView):
    @user_func_ratelimit(5, "1M")
    def get(self, request):
        pass

3.2.4 anon_func_ratelimit:
Used for Anonymous user requests rate limiting for function base apis

$ class SampleView(APIView):
    @anon_func_ratelimit(5, "1M")
    def get(self, request):
        pass

3.3 Middlewares

3.3.1 UserRateLimitMiddleware

Add this django settings Middlewares for User rate limiting
$ MIDDLEWARE = [
    .
    .
    .
    .
    "ratelimit.middleware.UserRateLimitMiddleware",
]

3.3.1 AnonRateLimitMiddleware

Add this django settings Middlewares for Anonymous rate limiting
$ MIDDLEWARE = [
    .
    .
    .
    .
    "ratelimit.middleware.AnonRateLimitMiddleware",
]
