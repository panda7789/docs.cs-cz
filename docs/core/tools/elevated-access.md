---
title: Přístup se zvýšeným oprávněním pro příkazy dotnet
description: Podívejte se na osvědčené postupy pro dotnet příkazy, které vyžadují přístup se zvýšeným oprávněním.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 3d874a76eadbf5330c4e5efe4e86bfeca0a9b504
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410644"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="20217-103">Přístup se zvýšeným oprávněním pro příkazy dotnet</span><span class="sxs-lookup"><span data-stu-id="20217-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="20217-104">Osvědčené postupy při vývoji softwaru Příručka vývojáře k vytváření softwaru, který vyžaduje minimální množství oprávnění.</span><span class="sxs-lookup"><span data-stu-id="20217-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="20217-105">Některý software, jako jsou nástroje pro monitorování výkonu však vyžaduje oprávnění správce z důvodu pravidla operačního systému.</span><span class="sxs-lookup"><span data-stu-id="20217-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="20217-106">Následující pokyny popisuje podporované scénáře pro zápis takový software s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="20217-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span> 

<span data-ttu-id="20217-107">Může být spuštěn se zvýšenými oprávněními následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="20217-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="20217-108">`dotnet tool` příkazy, jako například [instalace nástrojů dotnet](dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="20217-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`

<span data-ttu-id="20217-109">Nedoporučujeme spouštění dalších příkazů se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="20217-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="20217-110">Zejména nedoporučujeme zvýšení oprávnění pomocí příkazů, které používají MSBuild, jako například [dotnet restore](dotnet-restore.md), [dotnet sestavení](dotnet-build.md), a [dotnet spustit](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="20217-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="20217-111">Primární problém je oprávnění správy problémů, když uživatel přejde vpřed a zpět mezi kořenové a účet s omezeným přístupem po vydání příkazy dotnet.</span><span class="sxs-lookup"><span data-stu-id="20217-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="20217-112">Můžete zjistit jako uživatel s omezeným přístupem, že nemáte přístup k souboru vytvořená uživatelem root.</span><span class="sxs-lookup"><span data-stu-id="20217-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="20217-113">Existují způsoby, jak tuto situaci vyřešit, ale jsou nutné získat na prvním místě.</span><span class="sxs-lookup"><span data-stu-id="20217-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="20217-114">Můžete spouštět příkazy jako uživatel root, tak dlouho, dokud není přejít vpřed a zpět mezi kořenové a účet s omezeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="20217-114">You can run commands as root as long as you don’t transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="20217-115">Například kontejnery Dockeru jako uživatel root ve výchozím nastavení spouští, takže mají tato vlastnost.</span><span class="sxs-lookup"><span data-stu-id="20217-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="20217-116">Nástroj pro globální instalace</span><span class="sxs-lookup"><span data-stu-id="20217-116">Global tool installation</span></span>

<span data-ttu-id="20217-117">Následující pokyny ukazují doporučeným způsobem, jak nainstalovat, spustit a odinstalaci nástroje .NET Core, které vyžadují zvýšená oprávnění ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="20217-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET Core tools that require elevated permissions to execute.</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="20217-118">Windows</span><span class="sxs-lookup"><span data-stu-id="20217-118">Windows</span></span>](#tab/windows)

### <a name="install-the-global-tool"></a><span data-ttu-id="20217-119">Nainstalujte nástroj global</span><span class="sxs-lookup"><span data-stu-id="20217-119">Install the global tool</span></span>

<span data-ttu-id="20217-120">Pokud složka `%ProgramFiles%\dotnet-tools` již existuje, následujícím postupem zkontrolujte, zda má skupina "Users" oprávnění k zápisu nebo úpravám tohoto adresáře:</span><span class="sxs-lookup"><span data-stu-id="20217-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

* <span data-ttu-id="20217-121">Klikněte pravým tlačítkem myši `%ProgramFiles%\dotnet-tools` a pak zvolte položku **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="20217-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="20217-122">**Společné vlastnosti** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="20217-122">The **Common Properties** dialog box opens.</span></span> 
* <span data-ttu-id="20217-123">Vyberte **zabezpečení** kartu. V části **skupiny nebo jméno uživatele**, zkontrolujte, zda má skupina "Users" oprávnění k zápisu nebo úpravám adresáři.</span><span class="sxs-lookup"><span data-stu-id="20217-123">Select the **Security** tab. Under **Group or user names**, check whether the “Users” group has permission to write or modify the directory.</span></span> 
* <span data-ttu-id="20217-124">Pokud skupiny "Users" může zápisu nebo úpravám adresáři, použijte název jiného adresáře při instalaci nástrojů spíše než *nástrojů dotnet*.</span><span class="sxs-lookup"><span data-stu-id="20217-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="20217-125">Chcete-li nainstalovat nástroje, spusťte následující příkaz v řádku se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="20217-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="20217-126">Vytvoří *nástrojů dotnet* složky během instalace.</span><span class="sxs-lookup"><span data-stu-id="20217-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```cmd
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="20217-127">Spusťte nástroj global</span><span class="sxs-lookup"><span data-stu-id="20217-127">Run the global tool</span></span>

<span data-ttu-id="20217-128">**Možnost 1** použít úplnou cestu s řádku se zvýšenými oprávněními:</span><span class="sxs-lookup"><span data-stu-id="20217-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="20217-129">**Možnost 2** přidat nově vytvořená složka k `%Path%`.</span><span class="sxs-lookup"><span data-stu-id="20217-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="20217-130">Stačí jednou tuto operaci provést.</span><span class="sxs-lookup"><span data-stu-id="20217-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="20217-131">A spuštění:</span><span class="sxs-lookup"><span data-stu-id="20217-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="20217-132">Odinstalujte nástroj global</span><span class="sxs-lookup"><span data-stu-id="20217-132">Uninstall the global tool</span></span>

<span data-ttu-id="20217-133">V řádku se zvýšenými oprávněními zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="20217-133">In an elevated prompt, type the following command:</span></span>

```cmd
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linuxtablinux"></a>[<span data-ttu-id="20217-134">Linux</span><span class="sxs-lookup"><span data-stu-id="20217-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macostabmacos"></a>[<span data-ttu-id="20217-135">macOS</span><span class="sxs-lookup"><span data-stu-id="20217-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="20217-136">Místní nástroje</span><span class="sxs-lookup"><span data-stu-id="20217-136">Local tools</span></span>

<span data-ttu-id="20217-137">Místní nástroje jsou omezená na podstrom na uživatele.</span><span class="sxs-lookup"><span data-stu-id="20217-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="20217-138">Při spuštění se zvýšenými oprávněními, sdílet nástrojů pro místní prostředí s omezeným přístupem uživatele do prostředí se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="20217-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="20217-139">V Linuxu a macOS výsledkem souborů nastavena s přístupem jen pro uživatele root.</span><span class="sxs-lookup"><span data-stu-id="20217-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="20217-140">Uživatel přepne zpět na účet s omezeným přístupem, uživatel může již přistupovat k nebo zápis do souborů.</span><span class="sxs-lookup"><span data-stu-id="20217-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="20217-141">Proto instalace nástrojů, které vyžadují zvýšení jako místní nástroje se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="20217-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="20217-142">Místo toho použijte `--tool-path` možnost a předchozí pokyny pro globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="20217-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="20217-143">Zvýšení oprávnění během vývoje.</span><span class="sxs-lookup"><span data-stu-id="20217-143">Elevation during development</span></span>

<span data-ttu-id="20217-144">Během vývoje potřebujete přístup se zvýšeným oprávněním k testování aplikace.</span><span class="sxs-lookup"><span data-stu-id="20217-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="20217-145">Tento scénář je běžné, že aplikace IoT, např.</span><span class="sxs-lookup"><span data-stu-id="20217-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="20217-146">Doporučujeme vám vytvořit aplikaci bez zvýšení oprávnění a pak ho spusťte se zvýšením oprávnění.</span><span class="sxs-lookup"><span data-stu-id="20217-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="20217-147">Existuje několik vzorových postupů, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="20217-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="20217-148">Pomocí generované spustitelné soubory (poskytuje nejlepší výkon při spuštění):</span><span class="sxs-lookup"><span data-stu-id="20217-148">Using generated executable (it provides the best startup performance):</span></span>

   ```bash
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- <span data-ttu-id="20217-149">Použití [dotnet spustit](dotnet-run.md) příkazů `—no-build` příznak pro zabránění generování nových binárních souborů:</span><span class="sxs-lookup"><span data-stu-id="20217-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```bash
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="20217-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20217-150">See also</span></span>

* [<span data-ttu-id="20217-151">Přehled globální nástroje .NET core</span><span class="sxs-lookup"><span data-stu-id="20217-151">.NET Core Global Tools overview</span></span>](global-tools.md)
