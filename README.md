AWS IAM Role Terraform module
=============================

Terraform module which creates IAM Role on AWS.

Support resources:

* [aws_iam_role](https://www.terraform.io/docs/providers/aws/r/iam_role.html)
* [aws_iam_instance_profile](https://www.terraform.io/docs/providers/aws/r/iam_instance_profile.html)
* [aws_iam_role_policy_attachment](https://www.terraform.io/docs/providers/aws/r/iam_role_policy_attachment.html)

Usage
-----

```hcl
module "ec2-iam-role" {
  source = "TerraformModules/aws/security/iam_role"
  name   = "ec2-iam-role"

  policy_arn = [
    "arn:aws:iam::aws:policy/AmazonEC2ReadOnlyAccess",
    "arn:aws:iam::aws:policy/CloudWatchReadOnlyAccess",
  ]
}
```

Argument Reference
------------------

* name (Required)

* name_prefix (Optional)
  Default `false`

* assume_role_policy (Optional)
  Default

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "",
      "Effect": "Allow",
      "Principal": {
        "Service": "ec2.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

* force_detach_policies (Optional)
  Default `false`

* path (Optional)
  Default `"/"`

* description (Optional)
  Default `"This IAM Role generated by Terraform."`

* policy_arn (Required)
  


Attributes Reference
--------------------

* arn

* unique_id

* name

License
-------
see ./LICENSE

Copyright (c) 2017 Takashi Kawano
