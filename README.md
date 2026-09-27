# Selene Keycloak theme

A native Keycloak login theme matching the Selene web client: dark zinc surfaces, rose accents, compact typography, and a soft ambient glow. It inherits Keycloak's login templates, so standard and custom authentication flows keep working without duplicated FreeMarker templates.

## Install

Copy `themes/selene` into the Keycloak themes directory:

```text
<keycloak>/themes/selene
```

For a container, mount it read-only:

```yaml
volumes:
  - ./themes/selene:/opt/keycloak/themes/selene:ro
```

Then select **selene** under **Realm settings → Themes → Login theme** and save. During development, disable theme caching with these Keycloak options:

```text
--spi-theme-cache-themes=false
--spi-theme-cache-templates=false
--spi-theme-static-max-age=-1
```

Production should use Keycloak's default cache settings.

## Scope

The theme styles all pages rendered by Keycloak's inherited login flow, including sign-in, registration, password reset, email verification, OTP, WebAuthn, identity providers, informational pages, and errors. English labels are lightly tailored to Selene; Keycloak's inherited messages remain the fallback for every other key.
