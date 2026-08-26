# Changelog: relegation-Addon (LMOnext)

Dieses Addon war bis LMOnext 1.9.0-beta Teil des Core-Pakets. Mit der
Einführung des Addon-Manager-Frameworks (Beitrag Torsten Hofmann) wurde es
als eigenständiges, self-contained Paket extrahiert.

Die vollständige Entwicklungshistorie bis zur Extraktion steht im
CHANGELOG.md des LMOnext-Kernprojekts unter den Abschnitten
`addon/relegation/*`.

## Aktuelle Version: 1.0.1

- Als eigenständiges addon.json-Paket verpackt (Templates/Sprachdateien
  jetzt lokal im Addon statt zentral im Core), installierbar über
  Administrator → Addons.

## min_core_version-Korrektur

- min_core_version von "1.4.0" auf "1.9.0" korrigiert (Copy-Paste-Rest aus
  einer älteren internen Versionierung, faktisch wirkungslos, da niedriger
  als jede real existierende LMOnext-Version - AddonManager konnte damit nie
  eine zu alte Core-Version blockieren). "1.9.0" ist die tatsächliche
  LMOnext-Core-Version, ab der der Addon-Manager überhaupt existiert.

## Version 1.1.0 (Sicherheitsüberarbeitung)

- lmo-relegation.php 1.1.0: Aufruf-Erkennung auf die neue Konstante
  LMO_ADDON_STANDALONE_CALL umgestellt (gesetzt vom neuen zentralen
  Controller /addon-run.php). Der direkte URL-Aufruf ist per
  addon/.htaccess jetzt komplett gesperrt - Einbettungen müssen ab sofort
  über /addon-run.php?addon=relegation&file=lmo-relegation.php&...
  laufen, NICHT mehr über /addon/relegation/lmo-relegation.php.
- Neues Manifest-Feld "standalone_entrypoints": ["lmo-relegation.php"].
- Asset-Pfadauflösung (rlProjectRootUrlPrefix()) nutzt jetzt bevorzugt
  die vom Controller gelieferte LMO_ADDON_WEB_BASE.

**WICHTIG für bestehende Einbettungen:** URL wie oben anpassen, falls
bereits per iframe/URL extern eingebunden.
