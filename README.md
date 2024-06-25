# phpipam_api_helper

A simple phpIPAM API helper script for finding possible subnets of the given IP address.

## Usage

1. Create `~/.ipam/token.json`
    ```
    {
      "ApiPath": "your-phpipam-api-url",
      "AppToken": "your-api-token"
    }
    ```

2. Install requirements
    ```
    # Optional: create and activate virtualenv
    virtualenv env
    . env/bin/activate

    pip install -r requirements.txt
    ```

3. To find possible subnets of an IP address
    ```
    python phpipam_api_helper.py --ip <ip_address>
    ```
    When running the script the first time, the script makes API request to the phpIPAM to retrieve info of all subnets, then save the data to `~/.ipam/data.json`. So when making subsequent calls, the scripts use the data in this local file instead of making API calls again.

4. To enforce making phpIPAM API calls instead of the local copy of IPAM data
    ```
    python phpipam_api_helper.py --ip <ip_address> --refresh
    ```

## Notes
1. To create App ID and token, see https://phpipam.net/api/api_curl_example/
2. Test access:
    ```
    curl -X GET https://<url>/api/<appname>/addresses/tags/ -i --header 'token: <app-token>' --insecure
    ```
3. `url_rewrite` is required for API to work. See https://phpipam.net/api-documentation/
4. See https://github.com/phpipam/phpipam/issues/2624
