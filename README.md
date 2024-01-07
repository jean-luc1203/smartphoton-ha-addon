# Smartphoton Add-on Home Assistant basé sur node red

Smartphoton est un addon de gestion d'onduleurs et de batteries

**Onduleur**
* [x] Voltronic (wks, Axpert ...)

**Batterie**
* [x] Pylontech

**Tension Batterie**
* [x] 48 volt
* [x] 24 volt (non testé)
* [ ] 12 volt

---
## Installation
---

L'installation de ce module complémentaire est assez simple et ne diffère pas en
comparaison avec l’installation de tout autre module complémentaire Home Assistant.

1. Ajouter le dépot "https://github.com/jean-luc1203/smartphoton-ha-addon/" dans la boutique des modules complémentaires
1. Cliquez sur le bouton "Installer" pour installer le module complémentaire..
1. Configurer votre installation dans le menu configuration.
1. Démarrez le module complémentaire "Smartphoton".
1. Vérifiez les journaux de "Smartphoton" pour voir si tout s'est bien passé.

---
## Configuration
---

**Note**: _N'oubliez pas de redémarrer le module complémentaire lorsque la configuration est modifiée.._

Example add-on configuration:

```yaml
onduleur: voltronic
usbonduleur: /dev/serial/by-id/usb-Prolific_Technology_Inc._ATEN_USB_to_Serial_Bridge_EQDPb115818-if00-port0
elfinonduleur: false
elfinonduleurip: Adresse ip
elfinonduleurport: 7777
nameEntities:
  nameOnduleur: Onduleur
  namePV: PV Puissance (Watt)
  nameBatt_charge: Batt Charge (Watt)
  nameBatt_batt_decharge: Batt deharge (Watt)
  nameBatt_batt_chargedecharge: Batt Charge et Decharge (watt)
  nameConso_maison: Conso Maison (Watt)
  nameGridTension: Grid Tension (Volt)
  nameBattTensiont: Batterie Voltage (Volt)
  namePvTensiont: PV Voltage (Volt)
  nameOnduleurTension: Onduleur Tension (Volt)
  nameDataFrequency: Data Frequency (Hz)
  nameOnduleurFrequency: Onduleur-Frequency (Hz)
  namePvIntensite: Pv Intensite (Amp)
  nameBattChargeIntensite: Batt Charge Intensite (Amp)
  nameBattDechargeIntensite: Batt Decharge Intensite (Amp)
  nameBattCapacite: Batterie Capacité
  nameMode: Mode Solaire
  nameTemp: Temperature (°)
  nameParam01: Paramètre 01
  nameParam02: Paramètre 02
  nameParam05: Paramètre 05
  nameParam11: Paramètre 11
  nameParam12: Paramètre 12
  nameParam13: Paramètre 13
  nameParam16: Paramètre 16
  nameParam27: Paramètre 27
  nameParam29: Paramètre 29
batterie: pylontech
battTension: "48"
usbbatterie: false
elfinbatterie: false
elfinbatterieip: Adresse ip
elfinbatterieport: 7777
mqtt:
  mqttadresse: 192.168.1.200
  mqttport: "1883"
  mqttuser: test
  mqttpass: test
ssl: false
certfile: fullchain.pem
keyfile: privkey.pem
```

**Note**: _Ceci n'est qu'un exemple, ne le copiez pas et ne le collez pas ! voir les détails de configuration en dessous_

---
## Onduleur
---  

### Option: `Choix de l'onduleur ou onduleur`
Choisir le type d'onduleur (d'autres seront ajoutés par la suite).
   
  
### Option: `Choix port onduleur ou usbonduleur`
Choisir du port usb de d'onduleur. ("false" pour ne pas l'utiliser)

### Option: `Activer le elfin ou elfinonduleur`
Si vous utilisé un elfin : vrai ou faux

### Option: `Elfin`
**Activer le elfin ou elfinonduleur** Si vous utilisé un elfin : vrai ou faux

**Adresse elfin onduleur ou elfinonduleurip** Si vrai adresse ip du elfin de votre onduleur 

**Port elfin onduleur ou elfinonduleurip** Si vrai port du elfin de votre onduleur 

### Option: `Nom des entités ou nameEntities`
Permet de personnalisé les noms des entités onduleur.

---
## Batterie
---
### Option: `Choix de la Batterie ou batterie`
Choisir le type de batterie (d'autres seront ajoutés par la suite).

### Option: `Tension batteries ou battTension`
Tension de vos batteries (Les options 12 et 24 ne sont pas entièrement fonctionnel)

### Option: `Choix port usb de la batterie ou usbbatterie`
Choisir du port usb de la batterie ("false" pour ne pas l'utiliser)

### Option: `Elfin`
**Activer le elfin ou elfinbatterie** Si vous utilisé un elfin : vrai ou faux

**Adresse elfin onduleur ou elfinbatterieip** Si vrai adresse ip du elfin de votre batterie

**Port elfin onduleur ou elfinbatterieport** Si vrai port du elfin de votre batterie

---
## MQTT (obligatoire)
---
Vous devez avoir un broker mqtt (vous pouvez l'intaller via la boutique des module complémentaire. [Addon Mosquitto broker][addon-mqtt])
Il sera ensuite indispenssable d'ajouter intégration mqtt (voir doc mqtt)


### Option: 
**mqttadresse** Adresse de votre broker

**mqttport** port broker

**mqttuser** utilisateur de connexion 

**mqttpass** mot de passe de connexion

---
## Autres options
---
### Option: `Log Level`
The `log_level` option controls the level of log output by the addon and can
be changed to be more or less verbose, which might be useful when you are
dealing with an unknown issue. Possible values are:

- `trace`: Show every detail, like all called internal functions.
- `debug`: Shows detailed debug information.
- `info`: Normal (usually) interesting events.
- `warning`: Exceptional occurrences that are not errors.
- `error`: Runtime errors that do not require immediate action.
- `fatal`: Something went terribly wrong. Add-on becomes unusable.

Please note that each level automatically includes log messages from a
more severe level, e.g., `debug` also shows `info` messages. By default,
the `log_level` is set to `info`, which is the recommended setting unless
you are troubleshooting.

### Option: `ssl` (non testé)

Enables/Disables SSL (HTTPS) on the web interface.
Set it `true` to enable it, `false` otherwise.

**Note**: _The SSL settings only apply to direct access and has no effect
on the Ingress service._

### Option: `certfile`

The certificate file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default_

### Option: `keyfile`

The private key file to use for SSL.

**Note**: _The file MUST be stored in `/ssl/`, which is the default_


## Changelog & Releases
---

`MAJOR.MINOR.PATCH`

- `MAJOR`: Incompatible or major changes.
- `MINOR`: Backwards-compatible new features and enhancements.
- `PATCH`: Backwards-compatible bugfixes and package updates.


## Support
---
- [Github][depot-mqtt]
- [Site][site]
- [Forum][forum]
- [Documentations Github][documentation]


## Authors & contributors
---
Smartphoton, Jean-luc / Alexis / Romain / Khamel / Samuel

The original setup of this repository is by [Franck Nijhof][frenck].

For a full list of all authors and contributors,
check [the contributor's page][contributors].

## License
---
MIT License

Copyright (c) 2018-2023 Franck Nijhof

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

[addon-badge]: https://my.home-assistant.io/badges/supervisor_addon.svg
[addon]: https://my.home-assistant.io/redirect/supervisor_addon/?addon=a0d7b954_nodered&repository_url=https%3A%2F%2Fgithub.com%2Fhassio-addons%2Frepository
[addon-mqtt]: https://my.home-assistant.io/redirect/supervisor_addon/?addon=core_mosquitto&repository_url=https%3A%2F%2Fgithub.com%2Fhassio-addons%2Frepository
[depot-mqtt]: https://github.com/jean-luc1203/smartphoton-ha-addon/
[site]: https://smartphoton.fr/
[forum]: http://domosimple.eu/forum/
[documentation]: https://github.com/jean-luc1203/Smartphoton-Documentation
[alpine-packages]: https://pkgs.alpinelinux.org/packages
[contributors]: https://github.com/hassio-addons/addon-node-red/graphs/contributors
[discord-ha]: https://discord.gg/c5DvZ4e
[discord]: https://discord.me/hassioaddons
[forum]: https://community.home-assistant.io/t/home-assistant-community-add-on-node-red/55023?u=frenck
[frenck]: https://github.com/frenck
[issue]: https://github.com/hassio-addons/addon-node-red/issues
[node-red-nodes]: https://flows.nodered.org/?type=node&num_pages=1
[nodered-docs]: https://nodered.org/docs
[nodered]: https://nodered.org
[npm-packages]: https://www.npmjs.com
[reddit]: https://reddit.com/r/homeassistant
[releases]: https://github.com/hassio-addons/addon-node-red/releases
[semver]: http://semver.org/spec/v2.0.0.htm
