# Secure64 Ve-VNFM ReST API

The ReST API defined herein represents a general, non-fiat, standard
for the command, control, and provisioning of a virtual network
function providing DNS as a service.

## API Modeling Language

[RAML v1.0](https://github.com/raml-org/raml-spec/blob/master/versions/raml-10/raml-10.md)

"RAML is a language for the definition of HTTP-based APIs that embody
most or all of the principles of Representational State Transfer
(REST)."

## Modeling Tool

- [Atom Editor](https://atom.io/)
- Mulesoft api-workbench v0.8.36 (addon package)

To view the project in Atom:

1. Start the Atom editor
2. Open the RAML directory
3. Select and open the command_and_control-v1.raml file

* api-workbench provides a UI to navigate the model
  * From within Atom, select Packages->API Workbench->Open API Console

### Implementation Notes

The master_api.raml file is the Secure64 current DNS Rest API. It is
not part of the Ve-VNFM model and is provided for reference only.

## General Design Goals

For overall ReST API deisgn considerations, please see the ['ReST API
evaluation and design
criteria'](docs/rest-api-eval-design-criteria.md).
