---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67540097"
---
### <a name="install-the-global-tool"></a>Nainstalujte nástroj global

Prostředky balíčku by měl být nainstalován do chráněného umístění pomocí `--tool-path` možnost. Toto oddělení zabraňuje sdílení obsahu s omezeným přístupem uživatelské prostředí s prostředí se zvýšenými oprávněními.

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

`/usr/local/share/dotnet-tools` bude vytvořena s oprávněním `drwxr-xr-x`. Pokud adresář již existuje, použijte `ls -l` příkazu ověřte s omezeným přístupem uživatel nemá oprávnění k úpravám adresáři. Pokud ano, použít `sudo chmod o-w -R /usr/share/dotnet-tools` příkazu k odebrání přístupu.

### <a name="run-the-global-tool"></a>Spusťte nástroj global

**Možnost 1** použít úplnou cestu s příkazem sudo:

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

**Možnost 2** přidat odkaz na symbol nástroje, jednou za nástroj pro:

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

A spuštění:

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Odinstalujte nástroj global

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

Pokud jste provedli odkaz symbol, musíte také odebrat:

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```
