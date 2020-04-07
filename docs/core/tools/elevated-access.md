---
title: Zvýšený přístup pro příkazy dotnet
description: Seznamte se s doporučenými postupy pro příkazy dotnet, které vyžadují zvýšený přístup.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: f99e0b257772e0a73d4945f1129997d1d3308ed2
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805788"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="5e937-103">Zvýšený přístup pro příkazy dotnet</span><span class="sxs-lookup"><span data-stu-id="5e937-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="5e937-104">Osvědčené postupy vývoje softwaru vedou vývojáře k psaní softwaru, který vyžaduje nejmenší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5e937-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="5e937-105">Některé software, jako jsou nástroje pro sledování výkonu, však vyžaduje oprávnění správce z důvodu pravidel operačního systému.</span><span class="sxs-lookup"><span data-stu-id="5e937-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="5e937-106">Následující pokyny popisují podporované scénáře pro psaní takového softwaru pomocí rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e937-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span>

<span data-ttu-id="5e937-107">Následující příkazy lze spustit se zvýšenými oprávněními:</span><span class="sxs-lookup"><span data-stu-id="5e937-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="5e937-108">`dotnet tool`příkazy, jako je [například instalace nástroje dotnet](dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="5e937-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`
- `dotnet-core-uninstall`

<span data-ttu-id="5e937-109">Nedoporučujeme spouštět další příkazy se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="5e937-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="5e937-110">Zejména nedoporučujeme zvýšení s příkazy, které používají MSBuild, například [dotnet obnovení](dotnet-restore.md), [dotnet sestavení](dotnet-build.md)a [dotnet spustit](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="5e937-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="5e937-111">Primární problém je problémy se správou oprávnění, když uživatel přechází tam a zpět mezi kořenovým a omezeným účtem po vydání příkazů dotnet.</span><span class="sxs-lookup"><span data-stu-id="5e937-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="5e937-112">Jako uživatele s omezeným přístupem můžete zjistit, že nemáte přístup k souboru vytvořenému kořenovým uživatelem.</span><span class="sxs-lookup"><span data-stu-id="5e937-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="5e937-113">Existují způsoby, jak tuto situaci vyřešit, ale oni jsou zbytečné se dostat do na prvním místě.</span><span class="sxs-lookup"><span data-stu-id="5e937-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="5e937-114">Příkazy můžete spouštět jako root, pokud nepřecházíte tam a zpět mezi kořenovým a omezeným účtem.</span><span class="sxs-lookup"><span data-stu-id="5e937-114">You can run commands as root as long as you don’t transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="5e937-115">Například kontejnery Dockeru běží jako root ve výchozím nastavení, takže mají tuto charakteristiku.</span><span class="sxs-lookup"><span data-stu-id="5e937-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="5e937-116">Globální instalace nástrojů</span><span class="sxs-lookup"><span data-stu-id="5e937-116">Global tool installation</span></span>

<span data-ttu-id="5e937-117">Následující pokyny ukazují doporučený způsob instalace, spuštění a odinstalace nástrojů .NET Core, které ke spuštění vyžadují zvýšená oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5e937-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET Core tools that require elevated permissions to execute.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="5e937-118">Windows</span><span class="sxs-lookup"><span data-stu-id="5e937-118">Windows</span></span>](#tab/windows)

### <a name="install-the-tool"></a><span data-ttu-id="5e937-119">Instalace nástroje</span><span class="sxs-lookup"><span data-stu-id="5e937-119">Install the tool</span></span>

<span data-ttu-id="5e937-120">Pokud složka `%ProgramFiles%\dotnet-tools` již existuje, zkontrolujte, zda má skupina Uživatelé oprávnění k zápisu nebo úpravám tohoto adresáře:</span><span class="sxs-lookup"><span data-stu-id="5e937-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

- <span data-ttu-id="5e937-121">Klepněte pravým `%ProgramFiles%\dotnet-tools` tlačítkem myši na složku a vyberte **příkaz Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5e937-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="5e937-122">Otevře se dialogové okno **Společné vlastnosti.**</span><span class="sxs-lookup"><span data-stu-id="5e937-122">The **Common Properties** dialog box opens.</span></span>
- <span data-ttu-id="5e937-123">Vyberte kartu **Zabezpečení.** V části **Seskupení nebo uživatelská jména**zkontrolujte, zda skupina Uživatelé nemá oprávnění k zápisu nebo úpravám adresáře.</span><span class="sxs-lookup"><span data-stu-id="5e937-123">Select the **Security** tab. Under **Group or user names**, check whether the “Users” group has permission to write or modify the directory.</span></span>
- <span data-ttu-id="5e937-124">Pokud skupina "Uživatelé" může psát nebo upravovat adresář, použijte při instalaci nástrojů jiný název adresáře, nikoli *dotnet-tools*.</span><span class="sxs-lookup"><span data-stu-id="5e937-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="5e937-125">Chcete-li nainstalovat nástroje, spusťte následující příkaz ve zvýšené mačkovém řádku.</span><span class="sxs-lookup"><span data-stu-id="5e937-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="5e937-126">Během instalace vytvoří složku *dotnet-tools.*</span><span class="sxs-lookup"><span data-stu-id="5e937-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="5e937-127">Spuštění globálního nástroje</span><span class="sxs-lookup"><span data-stu-id="5e937-127">Run the global tool</span></span>

<span data-ttu-id="5e937-128">**Možnost 1** Použijte úplnou cestu se zvýšenou výzvou:</span><span class="sxs-lookup"><span data-stu-id="5e937-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="5e937-129">**Možnost č. 2** Přidejte nově vytvořenou složku do aplikace `%Path%`.</span><span class="sxs-lookup"><span data-stu-id="5e937-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="5e937-130">Tuto operaci musíte provést pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="5e937-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="5e937-131">A běh s:</span><span class="sxs-lookup"><span data-stu-id="5e937-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="5e937-132">Odinstalace globálního nástroje</span><span class="sxs-lookup"><span data-stu-id="5e937-132">Uninstall the global tool</span></span>

<span data-ttu-id="5e937-133">Ve zvýšené mač zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="5e937-133">In an elevated prompt, type the following command:</span></span>

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linux"></a>[<span data-ttu-id="5e937-134">Linux</span><span class="sxs-lookup"><span data-stu-id="5e937-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[<span data-ttu-id="5e937-135">Macos</span><span class="sxs-lookup"><span data-stu-id="5e937-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="5e937-136">Místní nástroje</span><span class="sxs-lookup"><span data-stu-id="5e937-136">Local tools</span></span>

<span data-ttu-id="5e937-137">Místní nástroje jsou vymezeny podle stromu podadresářů a uživatele.</span><span class="sxs-lookup"><span data-stu-id="5e937-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="5e937-138">Při spuštění se zvýšenými oprávněními sdílejí místní nástroje omezené uživatelské prostředí s prostředím se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="5e937-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="5e937-139">V Linuxu a macOS to má za následek nastavení souborů s přístupem pouze pro root uživatele.</span><span class="sxs-lookup"><span data-stu-id="5e937-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="5e937-140">Pokud uživatel přepne zpět na omezený účet, uživatel již nemůže přistupovat k souborům ani do něj zapisovat.</span><span class="sxs-lookup"><span data-stu-id="5e937-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="5e937-141">Instalace nástrojů, které vyžadují zvýšení oprávnění jako místní nástroje, se tedy nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="5e937-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="5e937-142">Místo toho `--tool-path` použijte možnost a předchozí pokyny pro globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="5e937-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="5e937-143">Nadmořská výška během vývoje</span><span class="sxs-lookup"><span data-stu-id="5e937-143">Elevation during development</span></span>

<span data-ttu-id="5e937-144">Během vývoje budete pravděpodobně potřebovat zvýšený přístup k testování aplikace.</span><span class="sxs-lookup"><span data-stu-id="5e937-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="5e937-145">Tento scénář je běžné pro aplikace IoT, například.</span><span class="sxs-lookup"><span data-stu-id="5e937-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="5e937-146">Doporučujeme sestavit aplikaci bez zvýšení oprávnění a potom ji spustit s nadmořskou výškou.</span><span class="sxs-lookup"><span data-stu-id="5e937-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="5e937-147">Existuje několik vzorů, takto:</span><span class="sxs-lookup"><span data-stu-id="5e937-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="5e937-148">Použití generovaného spustitelného souboru (poskytuje nejlepší výkon při spuštění):</span><span class="sxs-lookup"><span data-stu-id="5e937-148">Using generated executable (it provides the best startup performance):</span></span>

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```

- <span data-ttu-id="5e937-149">Použití příkazu [dotnet](dotnet-run.md) `—no-build` run s příznakem, abyste se vyhnuli generování nových binárních souborů:</span><span class="sxs-lookup"><span data-stu-id="5e937-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="5e937-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e937-150">See also</span></span>

- [<span data-ttu-id="5e937-151">Přehled globálních nástrojů .NET Core</span><span class="sxs-lookup"><span data-stu-id="5e937-151">.NET Core Global Tools overview</span></span>](global-tools.md)
