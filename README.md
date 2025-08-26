# Inhibit

A systemd-based sleep/suspend inhibitor with timer functionality and real-time status monitoring.

## What it does

Prevents your system from going to sleep or suspending for a specified duration, with the ability to query remaining time via a Unix socket.

## Setup

Enable and start the query socket:

```bash
systemctl --user daemon-reload
systemctl --user enable --now ironhibit.socket
```

## Usage

### Start ironhibit timer

```bash
# Inhibit sleep for 90 minutes
systemctl --user start ironhibit@90m

# Custom duration (e.g., 30 minutes)
systemctl --user start ironhibit@30m
```

### Monitor remaining time

```bash
# Stream remaining time (MM:SS format) until done
nc -U "$XDG_RUNTIME_DIR/ironhibit.sock"

# One-shot check (first line only)
nc -U "$XDG_RUNTIME_DIR/ironhibit.sock" | head -n1
```

### Stop early

```bash
systemctl --user stop ironhibit-timer.service
```

### Check status

```bash
# Service status
systemctl --user status ironhibit-timer

# System-wide inhibitors
systemd-inhibit --list
```

### Cleanup

```bash
# Disable socket when no longer needed
systemctl --user disable --now ironhibit.socket
```
