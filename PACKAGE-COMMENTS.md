## Summary

On 10/09/2025 the following security alert was brought to our attention:

> 🚨 Security Alert: npm Packages Compromised 
> 
> The popular npm packages npm-debug.log and chalk were recently compromised and used to distribute malware. This incident highlights the ongoing risks in the open-source supply chain and the importance of vigilant dependency management.
> 
> If your projects depend on these packages, audit your dependencies and take appropriate actions to mitigate any potential impact.
> 
> More details: https://www.aikido.dev/blog/npm-debug-and-chalk-packages-compromised

[DSIT-142](https://officefornationalstatistics.atlassian.net/browse/DSIT-142) confirmed that although this repository was not compromised, several transient dependencies fell within the range of the affected dependency requests.  To mitigate against accidentally introducing the compromised packages, these dependencies have now been explicitly pinned.

## Rationale

Per https://www.aikido.dev/blog/npm-debug-and-chalk-packages-compromised

- error-ex pinned to 1.3.2 → avoid compromised 1.3.3
- ansi-regex pinned to 6.0.1 → avoid compromised 6.2.1
- strip-ansi pinned to 7.1.0 → avoid compromised 7.1.1
- debug pinned to 4.3.7 → avoid compromised 4.4.2
- ansi-styles pinned to 6.2.1 → avoid compromised 6.2.2

## Benefits and Risks

These pinned resolutions act as a <i>temporary</i> safety rail and should be reviewed once newer, safer packages are published.

### Benefits:
* Immediate protection
* Deterministic builds
* Quick to apply

### Risks:
* Blocked updates
* Technical debt
* Conflicts
