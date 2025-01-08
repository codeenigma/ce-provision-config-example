# Vars that apply to all servers in an AWS ASG
To mark a host as part of an ASG set `_profile: asg` in the vars in your playbook like so:

```yaml
  vars:
    _profile: asg
```

This will apply the tag `Profile: asg` to your infrastructure in AWS so the automatic host determination will place it in the `_asg` group when it filters on tags. Note this is automatically the case if you use the central ASG plays in this repo.

Vars are broken down in files matching the parent variable (usually the matching role name).
