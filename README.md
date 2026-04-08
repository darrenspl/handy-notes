# Read Me

## Claude Code Install & Config

>[Claude Code Quick Start](https://code.claude.com/docs/en/quickstart)

### Windows

```PowerShell
irm https://claude.ai/install.ps1 | iex
```

### Linux

```Shell
curl -fsSL https://claude.ai/install.sh | bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc && source ~/.bashrc
```

### Configure Claude Code

```Shell
claude --dangerously-skip-permissions
```