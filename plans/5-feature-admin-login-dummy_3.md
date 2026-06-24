# Plan — Add MFA Notice to Admin Login Portal

**Branch:** feature/admin-login-dummy_3
**Issue:** #3
**Date:** 2026-06-24

## Goal
Enhance the existing admin login portal at `pages/admin/login.vue` by adding an informational banner notifying users that MFA (Multi-Factor Authentication) is required for staff accounts.

## Approach
Integrate an alert box component in the Vue template and style it using blue accent colors.

## Changes
- `pages/admin/login.vue` — Added MFA notice alert and styles
- `plans/5-feature-admin-login-dummy_3.md` — This plan file
