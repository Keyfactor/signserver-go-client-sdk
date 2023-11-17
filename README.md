# Go Client SDK for Keyfactor SignServer

The Go Client SDK for Keyfactor SignServer enables management of SignServer resources utilizing the Go programming language.

# Support for the Keyfactor SignServer Go Client SDK
We welcome contributions.

The Keyfactor SignServer Go Client SDK is open source and community supported, meaning that there is **no SLA** applicable for these tools.

###### To report a problem or suggest a new feature, use the **[Issues](../../issues)** tab. If you want to contribute actual bug fixes or proposed enhancements, use the **[Pull requests](../../pulls)** tab.

## Installation

Install the Go Client SDK for Keyfactor SignServer using the `go get` command:

```shell
go get github.com/Keyfactor/signserver-go-client-sdk
```

Put the package under your project folder and add the following in import:

```golang
import "github.com/Keyfactor/signserver-go-client-sdk/api/signserver"
```

## Configuration

Communication with the SignServer REST API is authenticated using a client certificate. The client certificate
must be a PEM encoded X509v3 certificate with an unencrypted private key in PKCS#8 format. These fields can
be configured either using environment variables or with an `signserver.Configuration` struct. Configure
the configuration struct as shown below:

```go
configuration := signserver.NewConfiguration()
configuration.Host = "example.com"
configuration.ClientCertificatePath = "auth_cert.pem" // Path to client certificate. The private key can be in the same file or in a file specified by the ClientCertificateKeyPath
configuration.ClientCertificateKeyPath = "auth_key.pem"
```

The following environment variables can be used to configure the client as well:
```shell
export SignServer_HOSTNAME="example.com"
export SignServer_CLIENT_CERT_PATH="auth_cert.pem"
export SignServer_CLIENT_CERT_KEY_PATH="auth_key.key"
```

Configuration of the SignServer client via the `signserver.Configuration` struct will override values set in environment variables.

If the SignServer REST API uses a port other than 443, it can be configured with the `SignServer_HOSTNAME` or the `Host` field in the configuration struct by
adding `:port` to the end of the hostname.

## Documentation for API Endpoints

All URIs are relative to */signserver/rest/v1*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*WorkersAPI* | [**WorkersIdDelete**](docs/WorkersAPI.md#workersiddelete) | **Delete** /workers/{id} | Removing worker
*WorkersAPI* | [**WorkersIdPatch**](docs/WorkersAPI.md#workersidpatch) | **Patch** /workers/{id} | Submit data for update and delete worker properties
*WorkersAPI* | [**WorkersIdPost**](docs/WorkersAPI.md#workersidpost) | **Post** /workers/{id} | Submit data for adding a new worker from multiple properties
*WorkersAPI* | [**WorkersIdPut**](docs/WorkersAPI.md#workersidput) | **Put** /workers/{id} | Submit data for replace worker properties with the new properties
*WorkersAPI* | [**WorkersNameProcessPost**](docs/WorkersAPI.md#workersnameprocesspost) | **Post** /workers/{name}/process | Submit data for processing
*WorkersAPI* | [**WorkersPost**](docs/WorkersAPI.md#workerspost) | **Post** /workers | Create a new worker given a list of properties


## Documentation For Models

 - [DataEncoding](docs/DataEncoding.md)
 - [ErrorMessage](docs/ErrorMessage.md)
 - [ProcessRequest](docs/ProcessRequest.md)
 - [ProcessResponse](docs/ProcessResponse.md)
 - [WorkerRequest](docs/WorkerRequest.md)
 - [WorkerResponse](docs/WorkerResponse.md)


## Application Notes
This API client was generated by the [OpenAPI Generator](https://openapi-generator.tech) project.  By using the [OpenAPI-spec](https://www.openapis.org/) from a remote server, you can easily generate an API client.

- API version: 1.0
- Package version: 1.0.0
- Build package: org.openapitools.codegen.languages.GoClientCodegen
