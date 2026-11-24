# Review rules for UEFI firmware (EDK II)

These rules apply to every Copilot code review in this repository.

## Untrusted input

- Treat images (BMP, PNG, JPEG), network packets, capsules and anything read
  from storage or other devices as untrusted input.
- Use SafeIntLib (for example `SafeUint32Mult` and `SafeUint32Add`) for every
  size or offset calculation that uses untrusted input. Flag plain `*` or `+`
  used to size a buffer.
- Check every length field against the real buffer size before copying.

## Safety checks

- Don't remove an existing overflow or bounds check unless the pull request
  explains why the value can't overflow.
