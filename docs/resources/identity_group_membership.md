---
subcategory: "Identity and Access Management (IAM)"
---

# hcso_identity_group_membership

Manages an IAM group membership resource within Huawei Cloud Stack Online.

-> **NOTE:** You *must* have admin privileges to use this resource.

## Example Usage

```hcl
resource "hcso_identity_group" "group_1" {
  name        = "group1"
  description = "This is a test group"
}

resource "hcso_identity_user" "user_1" {
  name     = "user1"
  enabled  = true
  password = "password12345!"
}

resource "hcso_identity_user" "user_2" {
  name     = "user2"
  enabled  = true
  password = "password12345!"
}

resource "hcso_identity_group_membership" "membership_1" {
  group = hcso_identity_group.group_1.id
  users = [
    hcso_identity_user.user_1.id,
    hcso_identity_user.user_2.id
  ]
}
```

## Argument Reference

The following arguments are supported:

* `group` - (Required, String, ForceNew) Specifies the group ID of this membership.

* `users` - (Required, List) Specifies a list of IAM user IDs to associate to the group.

## Attribute Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The resource ID in UUID format.
