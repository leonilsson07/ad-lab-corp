# AD Structure

This document describes the Active Directory structure used in the lab.

## Domain

- `corp.local`

## Organizational Units

- `north`

## Security Groups

- `employees`
- `managers`

## Users

- `emp01` (member of `employees`)
- `mgr01` (member of `managers`)

## File Shares and Permissions

- `\\SERVER1\Employees`
  - Share and NTFS permissions: Full Control for `employees`

- `\\SERVER1\Managers`
  - Share and NTFS permissions: Full Control for `managers`

## Summary

The structure mirrors a small corporate environment to practice OU design, group-based access, and basic AD administration tasks.
