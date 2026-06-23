# Plan — Implement Dummy Admin Login Portal

**Branch:** feature/admin-login-dummy_3
**Issue:** #3
**Date:** 2026-06-23

## Goal
Implement a mock admin login page and a landing dashboard that redirects users upon mock validation, referencing User Story #3.

## Approach
Create simple page routes at `pages/admin/login.vue` and `pages/admin/dashboard.vue` using scoped CSS for clean visuals. Logic checks for custom credentials or simulates successful Google Auth logins.

## Changes
- `pages/admin/login.vue` — Simple credentials and Google Auth login layout
- `pages/admin/dashboard.vue` — Mock admin dashboard layout
- `plans/2-feature-admin-login-dummy_3.md` — This plan file
