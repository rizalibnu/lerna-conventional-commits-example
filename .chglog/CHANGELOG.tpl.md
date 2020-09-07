# Change Log

All notable changes to this project will be documented in this file.
See [Conventional Commits](https://conventionalcommits.org) for commit guidelines.
{{ if .Versions -}}
{{ range .Versions }}
## {{ if .Tag.Previous }}[{{ .Tag.Name }}]({{ $.Info.RepositoryURL }}/compare/{{ .Tag.Previous.Name }}...{{ .Tag.Name }}){{ else }}{{ .Tag.Name }}{{ end }} ({{ datetime "2006-01-02" .Tag.Date }})


{{ if .RevertCommits -}}
### Reverts

{{ range .RevertCommits -}}
* Revert "{{ .Revert.Header }}" {{if .Hash.Short }}([{{ .Hash.Short }}]({{ $.Info.RepositoryURL }}/commit/{{.Hash.Short}})){{ end }}
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
* {{ if .Scope }}**{{ .Scope }}:** {{ end }}{{ .Subject }} {{if .Hash.Short }}([{{ .Hash.Short }}]({{ $.Info.RepositoryURL }}/commit/{{.Hash.Short}})){{ end }}
{{ end }}
{{ end -}}
{{ else if .RevertCommits -}}
{{ else -}}
**Note:** Version bump only for package {{ $.Info.Title }}
{{ end -}}
{{ end -}}
{{ end }}