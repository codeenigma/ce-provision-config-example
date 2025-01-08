# Vars that apply to all web servers
To mark a host as a web server set `_profile: web` in the vars in your playbook like so:

```yaml
  vars:
    _profile: web
```

This will apply the tag `Profile: web` to your infrastructure in AWS so the automatic host determination will place it in the `_web` group when it filters on tags.

Vars are broken down in files matching the parent variable (usually the matching role name).
