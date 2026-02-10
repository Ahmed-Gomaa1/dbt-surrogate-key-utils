# Publishing Guide for Your dbt Package

## Creating a Git Repository

1. **Initialize Git Repository**:
   ```bash
   cd dbt-surrogate-key-trim
   git init
   git add .
   git commit -m "Initial commit: Surrogate Key Trim package with trim parameter functionality"
   ```

2. **Create Repository on GitHub**:
   - Go to GitHub.com
   - Click "New repository"
   - Name it `dbt-surrogate-key-trim` (or similar)
   - Don't initialize with README, .gitignore, or license (we already have these)

3. **Link Local Repo to GitHub**:
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/dbt-surrogate-key-trim.git
   git branch -M main
   git push -u origin main
   ```

## Creating Releases

1. **Tag Your Release**:
   ```bash
   git tag -a v1.0.0 -m "Release version 1.0.0"
   git push origin v1.0.0
   ```

2. **Create GitHub Release**:
   - Go to your repository on GitHub
   - Click "Releases" tab
   - Click "Draft a new release"
   - Choose your tag (v1.0.0)
   - Add release notes describing the trim parameter functionality
   - Publish release

## Making It Discoverable

1. **Submit to dbt Hub** (optional):
   - Visit https://hub.getdbt.com/
   - Follow submission guidelines
   - This makes your package easily discoverable by other dbt users

2. **Share on Community Channels**:
   - Post about it in the "Show and Tell" section of the dbt Community Forum
   - Share on relevant Slack channels or social media
   - Write a blog post about the functionality

## Usage Instructions for Others

Once published, other users can add your package to their `packages.yml`:

```yaml
packages:
  - git: "https://github.com/YOUR_USERNAME/dbt-surrogate-key-trim.git"
    revision: v1.0.0  # Use the latest release tag
```

Then run:
```bash
dbt deps
```

## Future Maintenance

1. **Versioning**: Follow semantic versioning (major.minor.patch)
2. **Backward Compatibility**: Maintain the `trim=false` default to preserve compatibility
3. **Bug Fixes**: Address any issues reported by users
4. **Updates**: Keep up with dbt core releases to ensure compatibility

## Example Implementation

Users can now call your enhanced macro:

```sql
{{ surrogate_key_trim.generate_surrogate_key(['field_a', 'field_b'], trim=true) }}
```

This provides the exact functionality that was requested but not accepted into the main dbt-utils package.