---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "67540097"
---
### <a name="install-the-global-tool"></a>Instalace globálního nástroje

Prostředky balíčku by měly být `--tool-path` nainstalovány v chráněném umístění pomocí možnosti. Toto oddělení zabraňuje sdílení prostředí s omezeným přístupem uživatele se zvýšenými oprávněními prostředí.

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

`/usr/local/share/dotnet-tools`bude vytvořena se `drwxr-xr-x`svolením . Pokud adresář již existuje, `ls -l` ověřte pomocí příkazu, že uživatel s omezeným přístupem nemá oprávnění k úpravám adresáře. Pokud ano, `sudo chmod o-w -R /usr/share/dotnet-tools` odeberte přístup pomocí příkazu.

### <a name="run-the-global-tool"></a>Spuštění globálního nástroje

**Možnost 1** Použijte celou cestu s sudo:

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

**Možnost č. 2** Přidejte odkaz na symbol nástroje jednou za nástroj:

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

A běh s:

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Odinstalace globálního nástroje

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

Pokud jste vytvořili odkaz na symbol, musíte jej také odstranit:

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```
