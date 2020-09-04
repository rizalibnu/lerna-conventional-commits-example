{{ if .Versions -}}
{{ range .Versions }}
## {{ if .Tag.Previous }}[{{ .Tag.Name }}]({{ $.Info.RepositoryURL }}/compare/{{ .Tag.Previous.Name }}...{{ .Tag.Name }}){{ else }}{{ .Tag.Name }}{{ end }} ({{ datetime "2006-01-02" .Tag.Date }})

{{ if .RevertCommits -}}
### Reverts
{{ range .RevertCommits -}}
* {{ .Revert.Header }}
{{ end -}}
{{ end -}}
{{ if .NoteGroups -}}
{{ range .NoteGroups -}}
### ⚠ {{ .Title }}
{{ range .Notes }}
* {{ .Body }}
{{ end }}
{{ end -}}
{{ end -}}
{{ if .CommitGroups -}}
{{ range .CommitGroups -}}
### {{ .Title }}
{{ range .Commits -}}
* {{ if .Scope }}**{{ .Scope }}:** {{ end }}{{ .Subject }}
{{ end }}
{{ end -}}
{{ else -}}
**Note:** Version bump only for package {{ $.Info.Title }}
{{ end -}}
{{ end -}}
{{ end -}}