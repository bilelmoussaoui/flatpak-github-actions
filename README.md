# flatpak-github-actions
Build your flatpak application using Github Actions

<p align="center">
  <img src="https://user-images.githubusercontent.com/15098724/55282117-f8253380-52fa-11e9-95a3-ccae83b23034.png" alt="Flatpak logo" />
</p>

## How to use?  

Add a new workflow by creating a `.yml` file under `.github/workflows` with this content

```yaml
on: [push, pull_request]
name: Flatpak
jobs:
  flatpak-builder:
    name: "Flatpak Builder"
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - uses: docker://bilelmoussaoui/flatpak-builder-github-actions
      with:
        args:   --manifest-path "org.gnome.zbrown.Palette.yaml" 
                --app-id "org.gnome.zbrown.Palette" 
                --bundle "palette-nightly.flatpak"
```


### Arguments:
- `--manifest-path`

    The relative path the manifest file in this repository.

- `--app-id`

    The application ID

- `--bundle`

    The bundle name, by default it's `app.flatpak`

- `--runtime-repo`

    The repository used to fetch the runtime when the user download the Flatpak bundle.
    
    By default it's set to https://flathub.org/repo/flathub.flatpakrepo



The Docker Image used can be found [here](./Dockerfile).
