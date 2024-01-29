# app-test

## Thingboard

Run in the background
`docker compose up -d`

Login at: http://localhost:8080

### Two main acconts

#### Sysadmin

Can make tenants

Username: `sysadmin@thingsboard.org`
Password `sysadmin`

#### Tenant admin ()

Configure tenant, tenant devices, and tenant customers.

Username: `tenant@thingsboard.org`
Password `tenant`

### Emulator

`node emulator.js localhost:1883 <DEVICE_ACCESS_TOKEN>`
