# Caddy redirects for Hugo

Generate a redirects file compatible with the [`http.redir`](https://caddyserver.com/v1/docs/redir) plugin from Caddy.

## Usage

Add the module import to your Hugo config file:

```yaml
module:
  imports:
    # other imports
    - path: github.com/hacdias/hugo-caddy-redirs
```

Then enable the output file for home:

```yaml
# Optional: disable the generation of HTML aliases.
disableAliases: true

# Mandatory
outputs:
  home:
    - html # Default
    - rss # Default
    - redir
```

This will create a `redirects.txt` file on the root of your website. Now you can
add a rule to your Caddy configuration to use this file as the 301 redirects:

```
redir 301 {
  import /the/public/path/redirects.txt
}
```

## Thanks

Thanks to @jlelse for the improvement on adding the version with and without the trailing slash. 

## License

MIT
