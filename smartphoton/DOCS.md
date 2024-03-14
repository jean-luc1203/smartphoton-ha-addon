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

<br /><br />
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

Vous pouvez vous aider du [Smartphoton Configuration][addon-config] pour votre yaml

<br /><br />
---
## Onduleur
---  
   

### Option: `Choix port Liste Onduleur ou listonduleur`
Choisir du port usb de d'onduleur. ("false" pour ne pas l'utiliser)<br />
Chemin : ip ou serial. (<ip>:<port>) ou /dev/serial/by-id/<nom du serial><br />
Type : ip ou serial<br />
Onduleur : choix de la batterie. false ou voltronic<br />
multionduleur : Utilisation des qpgs.<br />
battTension : Tension des batterie branché sur l'onduleur<br />


<br /><br />
**exemple**
```yaml
- chemin: "false"
```
ou pour une communication avec onduleur en usb

```yaml
- chemin: /dev/serial/by-id/usb-Prolific_Technology_Inc._ATEN_USB_to_Serial_Bridge_EQDPb115818-if00-port0
  type: serial
  onduleur: voltronic
  battTension: 48
```

ou pour une communication avec onduleur en ip ou elfin

```yaml
- chemin: 192.168.1.252:8888
  type: ip
  onduleur: voltronic
  battTension: 48
```

<br /><br />
**Options disponibles**

| Nom | valeur par défaut | obligatoire | options |
|:--- |:---:|:---:|:--- |
| chemin | false | oui | Adresse ip, chemin serial|
| type | serial | oui | ip, serial |
| onduleur | voltronic | oui | voltronic |
| multionduleur | true | non | true, false |
| battTension | 48 | non | 48, 24, 12 |



<br /><br />
---
## Batterie
---

### Option: `Choix port Liste batterie ou listbatterie`
Choisir du port usb de la batterie. ("false" pour ne pas l'utiliser)<br />
Chemin : ip ou serial. (<ip>:<port>) ou /dev/serial/by-id/<nom du serial><br />
Type : ip ou serial<br />
Batterie : choix de la batterie. false ou pylontech<br />


<br /><br />
**exemple**
```yaml
- chemin: "false"
```
ou pour une communication avec batterie en usb

```yaml
- chemin: /dev/serial/by-id/usb-Prolific_Technology_Inc._ATEN_USB_to_Serial_Bridge_EQDPb115818-if00-port0
  type: serial
  batterie: pylontech
```

ou pour une communication avec batterie en ip ou elfin

```yaml
- chemin: 192.168.1.252:8888
  type: ip
  batterie: pylontech
```

<br /><br />
**Options disponibles**

| Nom | valeur par défaut | obligatoire | options |
|:--- |:---:|:---:|:--- |
| chemin | false | oui | Adresse ip, chemin serial|
| type | serial | oui | ip, serial |
| batterie | pylontech | oui | false,pylontech |


<br /><br />
---
## Nom des entités ou nameEntities
---

Permet de personnalisé les noms des entités onduleur.

<br /><br />
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
<br /><br />
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
[addon-config]: http://domosimple.eu/onduleur/
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
