# AFOAuth2Client

AFOAuth2Client is an extension for [AFNetworking](http://github.com/AFNetworking/AFNetworking/) that greatly simplifies the process of authenticating against an [OAuth 2](http://oauth.net/2/) provider.

This fork adds several simplifications to the API, including automatic caching and refreshing of access-tokens and renaming the methods to be closer to the terminology of the specification. This comes with some assumptions like that you're only connecting as one resource-owner to one token-endpoint with one instance of the client. If that's not your scenario, the master-branch contains the original version.

## Example Usage

``` objective-c
NSURL *url = [NSURL URLWithString:@"http://example.com/"];
AFOAuth2Client *oauthClient = [AFOAuth2Client clientWithBaseURL:url clientID:kClientID secret:kClientSecret tokenEndpointPath:@"/oauth/token"];

[oauthClient obtainAccessTokenUsingResourceOwnerPasswordCredentialsGrantWithUsername::@"username"
                                                                            password:@"password"
                                                                             success:^(AFOAuthCredential *credential) {
                                                                                 NSLog(@"I have a token! %@", credential.accessToken);
                                                                             }
                                                                             failure:^(NSError *error) {
                                                                                 NSLog(@"Error: %@", error);
                                                                             }];
```

## Contact

Mattt Thompson

- http://github.com/mattt
- http://twitter.com/mattt
- m@mattt.me

## License

AFOAuth2Client is available under the MIT license. See the LICENSE file for more info.
