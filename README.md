# Swarn Draw – Flutter + Firebase prototype (demo only)
Setup: `flutterfire configure` → `firebase deploy --only firestore:rules,functions` → `flutter run`.
Enable Phone Auth, App Check, and MFA. Give an admin a custom claim: `{role:'admin'}`.
Draw flow: admin `commitDraw` (hash published) → threshold met → `runDraw` (seed revealed; anyone can recompute winners from the public `draws/{n}` doc).
Locked until legal approval: real payments (`createPayment` throws), live draw, cash wallet.
Before 10M scale: shard the registration counter, use an independent randomness beacon, add Firestore indexes (users.regNo), add tests, enable PITR backups.

## Tests
`cd functions && npm i && node --test` (draw logic) · `flutter test` (prize table).
## Admin
Set claim `{role:'admin'}` + enrol MFA. Dashboard: Profile → Admin dashboard (commit/seal draw, jurisdiction approvals, audit log).
