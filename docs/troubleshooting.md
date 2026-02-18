# Troubleshooting

Common issues and quick fixes for the corp.local lab.

## Domain Join Fails

- Verify CLIENT1 DNS is set to `192.168.20.50`.
- Confirm SERVER1 is running AD DS and DNS.
- Test name resolution with `nslookup corp.local`.

## Cannot Resolve DNS

- Restart DNS Server service on SERVER1.
- Ensure `corp.local` zone exists.
- Confirm VirtualBox Internal Network is `LABNET`.

## Access Denied to File Shares

- Confirm user is in the correct group.
- Check both Share and NTFS permissions.
- Log off and back in after group changes.

## Cannot Ping Between VMs

- Verify both VMs are on `LABNET`.
- Ensure Windows Firewall allows ICMP Echo.
- Check IP configuration on both machines.

## Time Sync Issues

- Ensure both VMs use the same host time source.
- Run `w32tm /resync` on CLIENT1.
