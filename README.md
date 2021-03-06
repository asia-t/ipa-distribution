# ipa-distribution [![wercker status](https://app.wercker.com/status/6f5a01038313ff8de7506599ecf900c1/s/master "wercker status")](https://app.wercker.com/project/bykey/6f5a01038313ff8de7506599ecf900c1)

Simple service which track iOS application metadata and download link. Allow to generate manifest.plist for given application,
to simplify ad-hoc installation.

## Installation

1. Clone this repository
2. Start application using `npm start`

Set environment variable `BASE_URL` to address of service, like `BASE_URL=http://localhost:3000`.
You can do this by creating `.env` file or using env prefix of command `BASE_URL=http://localhost:3000 npm start`.

## Usage

API Methods

#### Get list of bundles
`GET /v1/bundles?page=<n>`

#### Create new bundle
`POST /v1/bundles`

payload:
```
{
  "app_id": "",
  "name": ""
  "version": ""
  "url": "<download_url>"
}
```

#### Get info about single bundle
`GET /v1/bundles/<id>`

sample output:

```
{
  "id": "de305d54-75b4-431b-adb2-eb6b9e546014",
  "app_id": "com.example.MyApp",
  "name": "MyApp",
  "version": "1.0.0",
  "url": "http://example.com/MyApp-1.0.0.ipa",
  "created_at": null,
  "updated_at": null,
  "manifest_url": "http://example.com/v1/bundles/de305d54-75b4-431b-adb2-eb6b9e546014/manifest.plist",
  "download_url": "itms-services://?action=download-manifest&url=http://example.com/v1/bundles/de305d54-75b4-431b-adb2-eb6b9e546014/manifest.plist"
}
```

#### Get manifest for single bundle
`GET /v1/bundles/<id>/manifest.plist`
