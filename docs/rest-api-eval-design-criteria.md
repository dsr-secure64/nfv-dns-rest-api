# evaluation criteria

- idempotentcy
- security model
- error handling
- asynchronous POST operations
- structure of information
- documentation completeness

## DNS ReST API design considerations

- All API calls shall be atomic
- APIs shall be composable
- All APIs are intended for programmatic use
- Asynchronous API calls shall set an expectation as to when the operation will complete
- Error codes for back end operations shall accurately describe the
  resulting state of the end service
- APIs shall be organized around generic namespace rather than product specific
  namespaces
  - e. g. authority-server vs authdns
- APIs shall be extensible
- APIs shall be under version control
- The DNS API should be generic such that they could be implemented by any DNS service
  endpoint provider

### discussion

```

Back end service operations shall be decomposed as required,
e. g. requests for statistics shall provide the option to request a
single statistic rather than returning a single unstructured
representation of all statistics.

Composability should be understood as the orchestration of discrete
tasks for the purpose of realizing a higher level operation,
e. g. zone provisioning may require an update to the zone
configuration as well as the transfer of the zone file, and a server
restart.

```
## idempotency

A ReST API requires all HTTP operations, except POST and PATCH, to yield the
same result each time it is invoked. That said, an idempotent
operation may not always return the same result (error code).

For example, an initial DELETE operation will remove the requested
object, and receive an HTTP 200 (ok) or 204 (no content)
response. Subsequent requests may result in a 404 response indicating
the resource was not found and/or that the operation is already
scheduled.

## security model

The security model shall handle the authorization (user/role) and
authentication of clients as well as accounting.  Confidentiality and
integrity will not be addressed.

It is assumed that ALL requests to the server shall be over HTTPS.

It is assumed that each API call contain a header field to
authenticate and authorize the caller, be this a token and or
identifier:secret model.

API authorization and authentication may need to be integrated with
the broader ecosystem (cloud or NFV environment). This may require us
to integrate with a cloud service such as keystone and/or some other
OAuth based system.

## error handling

The primary error object is the HTTP result code.

A secondary error object will be added to capture and return the
status of the requested service endpoint operation.

The error handling shall clearly indicate when an operation is not
supported. 

### discussion

```

The secondary error code should indicate that an operation has succeeded,
failed, and/or been scheduled.

A concise understanding of an operation's result and the state of the
back end service is requisite for composability.

```

## asynchronous POST operations

In cases where an operation may be long running, the caller shall be
informed as to when the operation began and when to expect its
completion. See error code discussion in preceding section.

## structure of information

All information returned by the ReST API shall be structured (machine
readable).

We may have allowances for semi-structured information. Unstructured
information is to be avoided.

## documentation completeness

The documentation shall describe:

- all error conditions
- end service state for each error condition
- composability caveats

## extensibility and versioning

TBD

## service discoverability

TBD

## acronym definitions

ReST : Re-presentational State Transfer
API    : Application Programming Interface
HTTP : Hypertext Transfer Protocol
URI   : Universal Resource Identifier
