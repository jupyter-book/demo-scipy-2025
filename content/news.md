# News Feed

2025-06-02
: Wrote 12,000 lines of code and drank the entire red bull. All of it.

2025-06-01
: Googled how to bake foccacia, bought 12kg of flour.

2025-05-31
: Had existential dread about looming deadline, and therefore did no work.

2025-03-01
: Started project, feeling very excited.

:::{tip} Get this tale of woe in your shell
:class: dropdown

To get the authors!

```{code-block} shell
curl http://localhost:3000/news.json | jq '.frontmatter.authors[] | .name'
```

To get the messages :(

```{code-block} shell
curl http://localhost:3000/news.json | \
	jq '.mdast |
          # Recurse into children
	      recurse(.children[]?) |

          # Select definition lists
          select(.type == "definitionList").children[] |

          # Select definitionDescriptions
	      select(.type == "definitionDescription").children[] |

          # Pull out raw values
	      .value'
```

:::
