AFNetworking-RetryWhenReachableExtensions
=========================================

AFNetworking+RetryWhenReachable extension

```objc
- (AFHTTPRequestOperation *)retry_GET:(NSString *)URLString
                        parameters:(id)parameters
                        success:(void (^)(AFHTTPRequestOperation *operation, id responseObject))success
                        failure:(void (^)(AFHTTPRequestOperation *operation, NSError *error))failure;
                        
- (AFHTTPRequestOperation *)retry_POST:(NSString *)URLString
                        parameters:(id)parameters
                        success:(void (^)(AFHTTPRequestOperation *operation, id responseObject))success
                        failure:(void (^)(AFHTTPRequestOperation *operation, NSError *error))failure;
```

and other methods.

The request will retry the request when

1. The device is unreachable. => Retry when the device has connection.
2. The request fails with 503 error code. (Service Unavailable) => Retry with exponential backoff algorithm.

Note that it will not retry the request when it fails with 500 (Internal Server Error) error code.

####AFNetworking+RAC+RetryWhenReachable

```objc
- (RACSignal *)racretry_GET:(NSString *)URLString parameters:(id)parameters;
- (RACSignal *)racretry_POST:(NSString *)URLString parameters:(id)parameters;
```

and other methods.
