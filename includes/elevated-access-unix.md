---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "67540097"
---
### <a name="install-the-global-tool"></a><span data-ttu-id="52183-101">Instalace globálního nástroje</span><span class="sxs-lookup"><span data-stu-id="52183-101">Install the global tool</span></span>

<span data-ttu-id="52183-102">Prostředky balíčku by měly být `--tool-path` nainstalovány v chráněném umístění pomocí možnosti.</span><span class="sxs-lookup"><span data-stu-id="52183-102">Package assets should be installed in a protected location using the `--tool-path` option.</span></span> <span data-ttu-id="52183-103">Toto oddělení zabraňuje sdílení prostředí s omezeným přístupem uživatele se zvýšenými oprávněními prostředí.</span><span class="sxs-lookup"><span data-stu-id="52183-103">This separation avoids sharing a restricted user environment with an elevated environment.</span></span>

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="52183-104">`/usr/local/share/dotnet-tools`bude vytvořena se `drwxr-xr-x`svolením .</span><span class="sxs-lookup"><span data-stu-id="52183-104">`/usr/local/share/dotnet-tools` will be created with permission `drwxr-xr-x`.</span></span> <span data-ttu-id="52183-105">Pokud adresář již existuje, `ls -l` ověřte pomocí příkazu, že uživatel s omezeným přístupem nemá oprávnění k úpravám adresáře.</span><span class="sxs-lookup"><span data-stu-id="52183-105">If the directory already exists, use the `ls -l` command to verify the restricted user doesn't have permission to edit the directory.</span></span> <span data-ttu-id="52183-106">Pokud ano, `sudo chmod o-w -R /usr/share/dotnet-tools` odeberte přístup pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="52183-106">If so, use the `sudo chmod o-w -R /usr/share/dotnet-tools` command to remove the access.</span></span>

### <a name="run-the-global-tool"></a><span data-ttu-id="52183-107">Spuštění globálního nástroje</span><span class="sxs-lookup"><span data-stu-id="52183-107">Run the global tool</span></span>

<span data-ttu-id="52183-108">**Možnost 1** Použijte celou cestu s sudo:</span><span class="sxs-lookup"><span data-stu-id="52183-108">**Option 1** Use the full path with sudo:</span></span>

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

<span data-ttu-id="52183-109">**Možnost č. 2** Přidejte odkaz na symbol nástroje jednou za nástroj:</span><span class="sxs-lookup"><span data-stu-id="52183-109">**Option 2** Add the symbol link of the tool, once per tool:</span></span>

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

<span data-ttu-id="52183-110">A běh s:</span><span class="sxs-lookup"><span data-stu-id="52183-110">And run with:</span></span>

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="52183-111">Odinstalace globálního nástroje</span><span class="sxs-lookup"><span data-stu-id="52183-111">Uninstall the global tool</span></span>

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="52183-112">Pokud jste vytvořili odkaz na symbol, musíte jej také odstranit:</span><span class="sxs-lookup"><span data-stu-id="52183-112">If you made a symbol link, you also need to remove it:</span></span>

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```
