---
ms.openlocfilehash: dece035f443ff827a250ca1c1233b7651df7d108
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424711"
---
### <a name="install-the-global-tool"></a><span data-ttu-id="610cf-101">Nainstalujte nástroj global</span><span class="sxs-lookup"><span data-stu-id="610cf-101">Install the global tool</span></span>

<span data-ttu-id="610cf-102">Prostředky balíčku by měl být nainstalován do chráněného umístění pomocí `--tool-path` možnost.</span><span class="sxs-lookup"><span data-stu-id="610cf-102">Package assets should be installed in a protected location using the `--tool-path` option.</span></span> <span data-ttu-id="610cf-103">Toto oddělení zabraňuje sdílení obsahu s omezeným přístupem uživatelské prostředí s prostředí se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="610cf-103">This separation avoids sharing a restricted user environment with an elevated environment.</span></span>

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="610cf-104">`/usr/local/share/dotnet-tools` bude vytvořena s oprávněním `drwxr-xr-x`.</span><span class="sxs-lookup"><span data-stu-id="610cf-104">`/usr/local/share/dotnet-tools` will be created with permission `drwxr-xr-x`.</span></span> <span data-ttu-id="610cf-105">Pokud adresář již existuje, použijte `ls -l` příkazu ověřte s omezeným přístupem uživatel nemá oprávnění k úpravám adresáři.</span><span class="sxs-lookup"><span data-stu-id="610cf-105">If the directory already exists, use the `ls -l` command to verify the restricted user doesn't have permission to edit the directory.</span></span> <span data-ttu-id="610cf-106">Pokud ano, použít `sudo chmod o-w -R /usr/share/dotnet-tools` příkazu k odebrání přístupu.</span><span class="sxs-lookup"><span data-stu-id="610cf-106">If so, use the `sudo chmod o-w -R /usr/share/dotnet-tools` command to remove the access.</span></span>

### <a name="run-the-global-tool"></a><span data-ttu-id="610cf-107">Spusťte nástroj global</span><span class="sxs-lookup"><span data-stu-id="610cf-107">Run the global tool</span></span>

<span data-ttu-id="610cf-108">**Možnost 1** použít úplnou cestu s příkazem sudo:</span><span class="sxs-lookup"><span data-stu-id="610cf-108">**Option 1** Use the full path with sudo:</span></span>

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

<span data-ttu-id="610cf-109">**Možnost 2** přidat odkaz na symbol nástroje, jednou za nástroj pro:</span><span class="sxs-lookup"><span data-stu-id="610cf-109">**Option 2** Add the symbol link of the tool, once per tool:</span></span>

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

<span data-ttu-id="610cf-110">A spuštění:</span><span class="sxs-lookup"><span data-stu-id="610cf-110">And run with:</span></span>

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="610cf-111">Odinstalujte nástroj global</span><span class="sxs-lookup"><span data-stu-id="610cf-111">Uninstall the global tool</span></span>

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="610cf-112">Pokud jste provedli odkaz symbol, musíte také odebrat:</span><span class="sxs-lookup"><span data-stu-id="610cf-112">If you made a symbol link, you also need to remove it:</span></span>

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```