# Global vars that apply to all hosts.
They are broken down in files matching the parent variable usually the matching role name. The exception is mostly that all AWS related variables begin with `_aws` if for an overarching infrastructure, or `aws` if for a specific role, to group them together. If you do not intend to use AWS you can delete/ignore these.
