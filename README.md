# <img src="docs/logo.png" width="32" align="top" alt=""> Remote System Explorer (RSE) for current Eclipse releases

[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/RoiSoleil/eclipse-rse/build.yml)](https://github.com/RoiSoleil/eclipse-rse/actions/workflows/build.yml)
[![GitHub](https://img.shields.io/github/license/RoiSoleil/eclipse-rse)](LICENSE)

The Remote System Explorer works with remote machines from Eclipse: browse and edit their files, run shells and
terminals, and see their processes, over SSH, FTP, Telnet or DStore, and on the local machine.

RSE was part of the Eclipse Target Management project, which is archived: its last release, 4.5.700, dates from
September 2024. This repository continues it for the current Eclipse releases, with the history of the original
code.

# Features

- **Remote files**: a tree of the files of each connection (SFTP, SCP, FTP, DStore or local), opened and saved in
  the Eclipse editors, with copy, drag and drop, rename, delete, compare and search.
- **Shells and terminals**: remote shells in the *Remote Shell* view, and terminals on SSH connections in the
  *Terminals* view, based on the Terminal of Eclipse Platform.
- **Processes**: the processes of a remote Linux machine, which can be killed.
- **User actions**: commands of your own on remote files and folders.
- **EFS**: remote files as an Eclipse file system (`rse://`), usable in projects.

Open the *Remote System Explorer* perspective, then create a connection in the *Remote Systems* view.

# Changes from the Eclipse release 4.5.700

- Runs on the current Eclipse releases, with Java 21.
- The terminals use the Terminal of Eclipse Platform (`org.eclipse.terminal.*`), which replaced the TM Terminal.
- SSH uses the maintained fork of JSch ([mwiede/jsch](https://github.com/mwiede/jsch)) instead of JSch 0.1.55,
  so that it connects to current SSH servers (modern key and host key algorithms).
- ICU4J, which Eclipse no longer ships, is replaced by the JDK.

The bundle identifiers are still `org.eclipse.rse.*` and `org.eclipse.dstore.*`, so that the plug-ins which
extend RSE keep working.

# Update Site

You can find the latest build of RSE here:

https://github.com/RoiSoleil/eclipse-rse/raw/update-site/latest/

# Build

Java 21 and Maven 3.9 are needed:

```
mvn clean verify
```

The update site is then in `update-site/org.eclipse.rse/target/repository`. The tests need remote hosts and do
not run by default; run them with `-DskipTests=false`.

# License

[Eclipse Public License 2.0](LICENSE), as the original code. The copyright of the original code belongs to its
authors (IBM, Wind River, MontaVista, Red Hat and others), as stated in each file.
