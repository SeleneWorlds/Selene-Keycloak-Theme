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

## Test locally

Start the included development server:

```bash
docker compose up
```

Then open the [theme preview](http://localhost:8080/realms/selene/protocol/openid-connect/auth?client_id=theme-preview&redirect_uri=http%3A%2F%2Flocalhost%3A8080%2F&response_type=code&scope=openid). Theme files are mounted directly and theme caching is disabled, so CSS and image changes only require a browser refresh.

The Keycloak Admin Console is available at <http://localhost:8080/admin/> with username `admin` and password `admin`. This setup uses Keycloak's development database and credentials and is only intended for local theme testing.

## Scope

The theme styles all pages rendered by Keycloak's inherited login flow, including sign-in, registration, password reset, email verification, OTP, WebAuthn, identity providers, informational pages, and errors. English labels are lightly tailored to Selene; Keycloak's inherited messages remain the fallback for every other key.
