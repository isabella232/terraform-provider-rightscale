---
layout: "rightscale"
page_title: "Rightscale: server"
sidebar_current: "docs-rightscale-datasource-server"
description: |-
  Create and maintain a RightScale server
---

# rightscale_server

Use this resource to create, update or destroy RightScale [servers](http://reference.rightscale.com/api1.5/resources/ResourceServers.html).

## Example Usage : Basic configuration of a server resource

```hcl
resource "rightscale_server" "web_server" {
  name = "web_server"
  deployment_href = "/api/deployments/1234"
  tags = [ "role:web_server=true" ]
  instance {
    cloud_href = "/api/clouds/1234"
    image_href = "/api/clouds/1234/images/1234"
    instance_type_href = "/api/clouds/1234/instance_types/1234"
    name = "web_instance"
    server_template_href = "/api/server_templates/1234"
    inputs {
      FOO = "text:bar"
      BAZ = "cred:Bangarang"
    }
  }
}
```

## Argument Reference

The following arguments are supported:

* `name` - (Required) The name of the server

* `deployment_href` - (Required) The href of the deployment the server will be placed in.

* `instance` - (Required) See [rightscale_instance](./cm_instance.html).

* `description` - (Optional) A description of the server.

* `optimized` - (Optional) A flag indicating whether instances of this server should be optimized for high-performance volumes.

* `tags` - (Optional) Any tags you want attached to the server and any instances created from this server object.

## Attributes Reference

The following attributes are exported:

* `links` - Hrefs of related API resources

* `created_at` - Datestamp of server creation.

* `updated_at` - Datestamp of when server was updated last.

* `state` - The state of the server (operational, terminating, pending, stranded, etc.)

* `href` - Href of the server.

* `resource_uid` - Cloud resource_uid as reported by cm platform.
