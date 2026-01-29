<div align="center">
	<p>
		<img alt="Thoughtworks Logo" src="https://raw.githubusercontent.com/twplatformlabs/static/master/psk_banner.png" width=800 />
	</p>
  <h2>common-actions</h2>
  <img alt="GitHub Actions Workflow Status" src="https://img.shields.io/github/actions/workflow/status/ThoughtWorks-DPS/common-actions/.github%2Fworkflows%2Fdevelopment-build.yaml"> <img alt="GitHub Release" src="https://img.shields.io/github/v/release/ThoughtWorks-DPS/common-actions"> <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/license-MIT-blue.svg"></a>
</div>
<br />

Example of actions that are commonly used within any sort of pipeline and can be bundled in a collection to incorporate team or organization specific configurations.  

### /slack-bot

Post messages using the https://slack.com/api/chat.postMessage API resource.  
```yaml
- name: Post success message to slack channel
  uses: twplatformlabs/common-actions/slack-bot@v1
  with:
    channel: lab-events
    message: New version released
    custom-message: ""              # use this field to completely override json body
    include-link: "false"           # include link to workflow run in standard message
    include-tag: "false"            # include version tag in standard message
```

### /gh-release-create

Create GitHub Release using github-cli.
```yaml
- name: Generate release notes
  uses: twplatformlabs/common-actions/gh-release-create@v1
  with:
    release-discussion-category:    # Start a discussion in the specified category. Default false.
    release-draft:                  # Save the release as a draft instead of publishing it. Default is false.
    release-fail-on-no-commits:     # Fail if there are no commits since the last release. Default is false.
    release-generate-notes:         # Automatically generate title and notes for the release. Default is true.
    release-latest:                 # Mark this release as Latest. Default is true.
    release-notes:                  # Append additional information to generate-notes.
    release-notes-file:             # Use custom release notes file instead of automation. Default is false.
    release-notes-from-tag:         # Take release notes from this tag annotation. Default is none. 
    release-start-tag:              # Starting tag to read annotation up till current for release notes. Default is current.
    release-prerelease:             # Mark the release as a prerelease. Default is false.
    release-target:                 # Target branch or full commit SHA. Default [main branch].
    release-title:                  # Release title. Default is $github.ref_name (tag).
    release-verify-tag:             # Abort in case the git tag doesn't already exist in the remote repository. Default is false.
```

###  /gren

Create github release on current tag using github-release-notes.    
```yaml
- name: Generate release notes
  uses: twplatformlabs/common-actions/gren@v1
  with:
    gren-additional-args: ""        # include addiitonal gren command line arguments
```

### workflows/ossf-scorecard

Add the `.github/workflows/ossf-scorecard.yaml` workflow to your Action repository to keep the local code-scanning security results current.
