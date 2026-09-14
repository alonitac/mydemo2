# Setup and Update

This is a reference for the `learning` skill. You come here from its "Start of every session" section, and you go back there when you finish.

## First-time setup

If the file `.exit0/e0` does not exist, greet the student and explain what is about to run. Use this template. The course name is the title of the repo's `README.md`.

> Welcome to the {course name} course!
>
> Before we start, we are going to download a small tool called `e0`. It is a Python script that helps manage your course: it fetches content, assigns you tasks through GitHub issues, and tracks your progress.
>
> It will live in the `.exit0/` folder in your repo. That folder is for internal course use. You can safely ignore it throughout the course.
>
> You do not need to use `e0` directly. I will use it on your behalf.
>
> {a short, friendly closing line in the student's language}

Then run:

```bash
RELEASE=v1.3
curl -fsSL "https://raw.githubusercontent.com/exit0-io/e0/${RELEASE}/cli/bin/e0" -o .exit0/e0 && chmod +x .exit0/e0
.exit0/e0 init
```

On Windows (PowerShell), run this instead, and from now on run every `e0` command as `python .exit0/e0 ...`:

```powershell
$RELEASE="v1.3"
curl.exe -fsSL "https://raw.githubusercontent.com/exit0-io/e0/$RELEASE/cli/bin/e0" -o .exit0/e0
python .exit0/e0 init
```

`init` prints JSON. If `ok` is `false`, tell the student the `message` and `guidance` in plain words and help them fix it (usually it is the internet connection or a missing `.exit0/config.json`). Do not continue until `init` succeeds.

After `init` succeeds you MUST:

1. Recommend that the student allow `.exit0/e0` to run without confirmation. It drives the whole course and sends nothing anywhere.
2. Suggest switching to the cheapest available model. The course supplies all content, tests, and rules. You are not reasoning from scratch.
3. Go back to the `learning` skill, "Start of every session", step 2.

## Updating

> Never update silently. Tell the student what you did and why.

When the student asks to update `e0`, or when `e0 status` reports that the current version should be updated:

1. Find the target version. If `e0 status` gave you one, use it. Otherwise use the latest release.
2. Run:

```bash
RELEASE=<target version>
curl -fsSL "https://raw.githubusercontent.com/exit0-io/e0/${RELEASE}/cli/bin/e0" -o .exit0/e0 && chmod +x .exit0/e0
.exit0/e0 init
```

`init` also refreshes the skills in `.exit0/skills/` to match the new version.

3. Run `.exit0/e0 status` to confirm it works, then go back to the `learning` skill, "Start of every session", step 2.

Do not update unless the student asked, or the `e0 status` output says the current version should be updated.
