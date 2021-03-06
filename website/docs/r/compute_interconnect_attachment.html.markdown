---
# ----------------------------------------------------------------------------
#
#     ***     AUTO GENERATED CODE    ***    AUTO GENERATED CODE     ***
#
# ----------------------------------------------------------------------------
#
#     This file is automatically generated by Magic Modules and manual
#     changes will be clobbered when the file is regenerated.
#
#     Please read more about how to change this file in
#     .github/CONTRIBUTING.md.
#
# ----------------------------------------------------------------------------
layout: "google"
page_title: "Google: google_compute_interconnect_attachment"
sidebar_current: "docs-google-compute-interconnect-attachment"
description: |-
  Represents an InterconnectAttachment (VLAN attachment) resource.
---

# google\_compute\_interconnect\_attachment

Represents an InterconnectAttachment (VLAN attachment) resource. For more
information, see Creating VLAN Attachments.



## Example Usage

```hcl
resource "google_compute_router" "foobar" {
  name    = "my-router"
  network = "${google_compute_network.foobar.name}"
}

resource "google_compute_interconnect_attachment" "default" {
  name         = "test-interconnect"
  interconnect = "my-interconnect-id"
  router       = "${google_compute_router.foobar.self_link}"
}
```

## Argument Reference

The following arguments are supported:


* `interconnect` -
  (Required)
  URL of the underlying Interconnect object that this attachment's traffic will
  traverse through.

* `router` -
  (Required)
  URL of the cloud router to be used for dynamic routing. This router must be in
  the same region as this InterconnectAttachment. The InterconnectAttachment will
  automatically connect the Interconnect to the network & region within which the
  Cloud Router is configured.

* `name` -
  (Required)
  Name of the resource. Provided by the client when the resource is created. The
  name must be 1-63 characters long, and comply with RFC1035. Specifically, the
  name must be 1-63 characters long and match the regular expression
  `[a-z]([-a-z0-9]*[a-z0-9])?` which means the first character must be a
  lowercase letter, and all following characters must be a dash, lowercase
  letter, or digit, except the last character, which cannot be a dash.


- - -


* `description` -
  (Optional)
  An optional description of this resource.

* `region` -
  (Optional)
  Region where the regional interconnect attachment resides.
* `project` - (Optional) The ID of the project in which the resource belongs.
    If it is not provided, the provider project is used.


## Attributes Reference

In addition to the arguments listed above, the following computed attributes are exported:


* `cloud_router_ip_address` -
  IPv4 address + prefix length to be configured on Cloud Router
  Interface for this interconnect attachment.

* `customer_router_ip_address` -
  IPv4 address + prefix length to be configured on the customer
  router subinterface for this interconnect attachment.

* `private_interconnect_info` -
  Information specific to an InterconnectAttachment. This property
  is populated if the interconnect that this is attached to is of type DEDICATED.  Structure is documented below.

* `google_reference_id` -
  Google reference ID, to be used when raising support tickets with
  Google or otherwise to debug backend connectivity issues.

* `creation_timestamp` -
  Creation timestamp in RFC3339 text format.
* `self_link` - The URI of the created resource.


The `private_interconnect_info` block contains:

* `tag8021q` -
  802.1q encapsulation tag to be used for traffic between
  Google and the customer, going to and from this network and region.

## Timeouts

This resource provides the following
[Timeouts](/docs/configuration/resources.html#timeouts) configuration options:

- `create` - Default is 4 minutes.
- `delete` - Default is 4 minutes.

## Import

InterconnectAttachment can be imported using any of these accepted formats:

```
$ terraform import google_compute_interconnect_attachment.default projects/{{project}}/regions/{{region}}/interconnectAttachments/{{name}}
$ terraform import google_compute_interconnect_attachment.default {{project}}/{{region}}/{{name}}
$ terraform import google_compute_interconnect_attachment.default {{name}}
```

-> If you're importing a resource with beta features, make sure to include `provider=google-beta"
as an argument so that Terraform uses the correct provider to import your resource.
