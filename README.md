# DOCS
It is a documentation for my previous experience.

# Graph QL

BFF Steps

POST 

1. go to config.ts
2. export const STC_CONFIG_DEV STC_CONFIG_DEV change the value of bffBaseURL from https://api-bff-dev.stcplay.gg/graphql/ to http://localhost:3333/graphql/ NOTE: before PR revert to original URL. We are doing if just for testing
3. go to fe-api folder > endpoint.ts
4. update the endpoints ex. updatePreference: userBaseUrl + 'preference/update',
5. go to modules>crm then create preference folder
6. create folder preference. copy the component from existing folders. Edit the components.
7. Edit the update.gql
 create input in order.ts
8. Edit the update.service.ts
9. Go to typedef then create updatePreference.ts
10. Go to app.module.ts the import PreferenceUpdateModule from update.module.ts then add the module name below
11. type npm start fe-api
     create update.mutation.ts at libs>data-access>src>graphql>mutation>user
12. check http://localhost:3333/graphql on browser
13. Paste this to the HTTP HEADERS at lower left, update the token 

{
  "x-api-version":115,
  "x-api-lang":"en",
  "x-api-key":"yqjouAgiad1NsUrLV2ZsW6qhjWHnVcqf75CDoMkU",
  "x-api-token":"3cff2996a2ea8a79a53c7ac5216d6a94d3446841f",
  "x-api-endpoint":"web"
}

14. Paste to the first box on the local host

POST
mutation PreferenceUpdate($details: PreferenceUpdateInput!) {
  preferenceUpdate(details: $details) {
    is_successful
    error_msg
    error_code
  }
}

GET

query fetchCurrency {
            Currency {
                is_successful
                error_code
                error_msg
                app_code
                response {
                    rates {
                        currency_name
                        currency_rate
                    }
                }
            }
        }

{
  "x-api-version":115,
  "x-api-lang":"en",
  "x-api-key":"yqjouAgiad1NsUrLV2ZsW6qhjWHnVcqf75CDoMkU",
  "x-api-token":"323cd874c73bb8d2a18c6bfc65256efbad6673aff",
  "x-api-endpoint":"web"
}

sample geo.query.ts
 
this will be based on  my update.gql

15. Paste this to query variables lower left corner 

{
  "details": {
    "is_2FA_required": "1"
  }
}

16. This should be the response

{
  "data": {
    "preferenceUpdate": {
      "is_successful": true,
      "error_msg": "",
      "error_code": ""
    }
  }
}
then press play

17. Create Hooks
18. Go to libs >data-access>src>graphql>mutations> create folder user> preference> create update.mutation.ts
19. export to index.ts of the data-access export * from './graphql/mutations/user/preference/update.mutation';
20. libs>hooks>src> create folder usePreferenceUpdate
21. export to index.ts of hooks

# Redux

1. Create slicer in appStateSlice.ts
2.  use const dispatch = useDispatch(); on your hook
3.  dispatch(setUser({preferred_timezone:params.preferred_timezone, preferred_currency: params.preferred_currency} as UserModel), );
4. check on redux webkit
