---
title: Well-Known URIs for Service Description
docname: draft-polli-service-description-well-known-uri-latest
category: std

ipr: trust200902
area: General
workgroup: HTTP
keyword: Internet-Draft

stand_alone: yes
pi: [toc, tocindent, sortrefs, symrefs, strict, compact, comments, inline, docmapping]

author:
 -
    ins: R. Polli
    name: Roberto Polli
    org: Team Digitale, Italian Government
    email: robipolli@gmail.com

normative:
  RFC2119:

informative:
  OpenAPI:
    title: "OpenAPI Specifications"
    target: https://github.com/OAI/OpenAPI-Specification
    
--- abstract

Link Relation Types for Web Services have been introduced in RFC 8631
to provide documentation, descriptions, metadata, or status
information for these resources. This specification registers
the corrisponding labels into the well-known URI IANA Registry.

--- note_Note_to_Readers

*RFC EDITOR: please remove this section before publication*

Discussion of this draft takes place on the HTTP working group mailing list
(ietf-http-wg@w3.org), which is archived at
<https://lists.w3.org/Archives/Public/ietf-http-wg/>.

The source code and issues list for this draft can be found at
<https://github.com/ioggstream/draft-polli-service-description-well-known-uri>.


--- middle

# Introduction

Link Relation Types for Web Services have been introduced in {{?RFC8631}}
to provide documentation, descriptions, metadata, or status
information for these resources.

This specification adds the corrisponding entries in the well-known URI IANA
Registry.

## Notational Conventions
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 ([RFC2119] and {{?RFC8174}})
when, and only when, they appear in all capitals, as shown here.

The terms "documentation" and "description" are to be interpreted
as described in Section 3 of {{?RFC8631}}.

# Well-Known URI for Web Services

This specifications registers the following Well-Known URIs
associated to the Link Relations defined in {{?RFC8631}}.

Servers MAY use content negotiation (see Section 3.4 of {{?RFC7231}})
to provide different types
of documentation or description.

Clients SHOULD NOT make any assumptions about the provided type
of documentation or description.

# Examples


## Communicate API specification via well-known URI

Request:

~~~

  GET /.well-know/service-desc
  Accept: application/vnd.oai.openapi;version=3.0.1

~~~

Response:

~~~
  HTTP/1.1 200 Ok
  Content-Type: application/vnd.oai.openapi;version=3.0.1

  ...openapi specification...
~~~

## Communicate API documentation via well-known URI

Request:

~~~

  GET /.well-know/service-doc
  Accept: text/html, application/pdf

~~~

Response:

~~~
  HTTP/1.1 200 Ok
  Content-Type: text/html

  ...html documentation...
~~~

## Communicate API status via well-known URI

Request:

~~~

  GET /.well-know/status

~~~

Response:

~~~
  HTTP/1.1 503 Ok
  Content-Type: application/problem+json
  Retry-After: 3600
  
  {
    "status": 503,
    "title": "Service Unavailable",
    "detail": "Service is under maintenance. Check the Retry-After header."
  }
  
~~~



# Security Considerations

## Information exposure

TODO

# IANA Considerations

This specification defines a "well-known" URI
   using the registration procedure and template from Section 5.1 of
   {{?RFC8615}}.
   
## service-desc Well-Known URI Registration

IANA has added the following to the "Well-Known URIs" [RFC8615]
registry:

   URI suffix:  service-doc

   Change controller:  IETF.

   Specification document(s): Section 6.1 of {{?RFC8631}}, this document

   Related information: None.

## service-desc Well-Known URI Registration

IANA has added the following to the "Well-Known URIs" [RFC8615]
registry:

   URI suffix:  service-desc

   Change controller:  IETF.

   Specification document(s): Section 6.2 of {{?RFC8631}}, this document

   Related information:  None.

## service-meta Well-Known URI Registration

IANA has added the following to the "Well-Known URIs" [RFC8615]
registry:

   URI suffix:  service-meta

   Change controller:  IETF.

   Specification document(s): Section 6.3 {{?RFC8631}}, this document

   Related information:  None.

## status Well-Known URI Registration

IANA has added the following to the "Well-Known URIs" [RFC8615]
registry:

   URI suffix:  status

   Change controller:  IETF.

   Specification document(s): Section 6.4 {{?RFC8631}}, this document

   Related information:  None.


--- back



# Acknowledgements

This work is based on Erik Wilde's work
on service description contained in {{?RFC8631}}.

# Change Log
{:numbered="false"}

RFC EDITOR PLEASE DELETE THIS SECTION.


# FAQ
{:numbered="false"}

RFC EDITOR PLEASE DELETE THIS SECTION.

