Project Description

django-ns-ratelimit is django app for limit requests using rate limit class, decorators and middleware.

1 Installation

$ pip install -i https://test.pypi.org/simple/ django-ns-ratelimit==1.0


2 Usage

2.1 Periods in format:
    S: For seconds
    M: For minutes
    H: For hour
    D: For Day

    e.g: "10S" "1M" "1D"

2.2 Decorators
2.2.1 user_method_ratelimit:
Used for user specific request rate limiting for class base apis

$ class SampleView(APIView):
    @user_method_ratelimit(5, "1M")
    def get(self, request):
        pass

2.2.2 anon_method_ratelimit:
Used for Anonymous user requests rate limiting for class base apis

$ class SampleView(APIView):
    @anon_method_ratelimit(5, "1M")
    def get(self, request):
        pass

2.2.3 user_func_ratelimit:
Used for user specific request rate limiting for function base apis

$ class SampleView(APIView):
    @user_func_ratelimit(5, "1M")
    def get(self, request):
        pass

2.2.4 anon_func_ratelimit:
Used for Anonymous user requests rate limiting for function base apis

$ class SampleView(APIView):
    @anon_func_ratelimit(5, "1M")
    def get(self, request):
        pass

2.3 Middlewares

2.3.1 UserRateLimitMiddleware

Add this django settings Middlewares for User rate limiting
$ MIDDLEWARE = [
    .
    .
    .
    .
    "ratelimit.middleware.UserRateLimitMiddleware",
]

2.3.1 AnonRateLimitMiddleware

Add this django settings Middlewares for Anonymous rate limiting
$ MIDDLEWARE = [
    .
    .
    .
    .
    "ratelimit.middleware.AnonRateLimitMiddleware",
]
