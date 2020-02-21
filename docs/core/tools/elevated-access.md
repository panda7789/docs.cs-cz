---
title: Zvýšený přístup pro příkazy dotnet
description: Seznamte se s osvědčenými postupy pro příkazy dotnet, které vyžadují vyšší přístup.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: fe33cbe966d175f71ba350737b283c1e83f64fa6
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543427"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="30700-103">Zvýšený přístup pro příkazy dotnet</span><span class="sxs-lookup"><span data-stu-id="30700-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="30700-104">Osvědčené postupy pro vývoj softwaru pomáhají vývojářům psát software, který vyžaduje nejnižší množství oprávnění.</span><span class="sxs-lookup"><span data-stu-id="30700-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="30700-105">Nicméně nějaký software, například nástroje pro monitorování výkonu, vyžaduje oprávnění správce z důvodu pravidel operačního systému.</span><span class="sxs-lookup"><span data-stu-id="30700-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="30700-106">Následující pokyny popisují podporované scénáře pro zápis takového softwaru pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30700-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span> 

<span data-ttu-id="30700-107">Následující příkazy lze spustit se zvýšenými oprávněními:</span><span class="sxs-lookup"><span data-stu-id="30700-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="30700-108">`dotnet tool` příkazy, jako je například [Instalace nástroje dotnet](dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="30700-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`

<span data-ttu-id="30700-109">Nedoporučujeme spouštět další příkazy se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="30700-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="30700-110">Konkrétně nedoporučujeme zvyšovat zvýšení oprávnění pomocí příkazů, které používají MSBuild, například [dotnet Restore](dotnet-restore.md), [sestavení dotnet](dotnet-build.md)a [spuštění dotnet](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="30700-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="30700-111">Primárním problémem jsou problémy se správou oprávnění, když uživatel prochází zpátky a zpátky mezi kořenovým a omezeným účtem po vystavení příkazů dotnet.</span><span class="sxs-lookup"><span data-stu-id="30700-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="30700-112">Můžete se setkat s omezeným uživatelem, který nemáte přístup k souboru vytvořenému kořenovým uživatelem.</span><span class="sxs-lookup"><span data-stu-id="30700-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="30700-113">Existují způsoby, jak tuto situaci vyřešit, ale nejsou potřebné k tomu, aby se na první místo dostaly.</span><span class="sxs-lookup"><span data-stu-id="30700-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="30700-114">Příkazy můžete spustit jako kořen, pokud nebudete mezi kořenem a omezeným účtem přecházet zpátky a zpátky.</span><span class="sxs-lookup"><span data-stu-id="30700-114">You can run commands as root as long as you don’t transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="30700-115">Například kontejnery Docker se ve výchozím nastavení spouštějí jako kořenové, takže mají tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="30700-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="30700-116">Instalace globálních nástrojů</span><span class="sxs-lookup"><span data-stu-id="30700-116">Global tool installation</span></span>

<span data-ttu-id="30700-117">Následující pokyny ukazují doporučený způsob, jak nainstalovat, spustit a odinstalovat nástroje .NET Core, které vyžadují vyšší oprávnění ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="30700-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET Core tools that require elevated permissions to execute.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="30700-118">Windows</span><span class="sxs-lookup"><span data-stu-id="30700-118">Windows</span></span>](#tab/windows)

### <a name="install-the-tool"></a><span data-ttu-id="30700-119">Instalace nástroje</span><span class="sxs-lookup"><span data-stu-id="30700-119">Install the tool</span></span>

<span data-ttu-id="30700-120">Pokud `%ProgramFiles%\dotnet-tools` složka již existuje, proveďte následující kroky a ověřte, zda má skupina uživatelé oprávnění k zápisu nebo úpravě tohoto adresáře:</span><span class="sxs-lookup"><span data-stu-id="30700-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

- <span data-ttu-id="30700-121">Klikněte pravým tlačítkem na složku `%ProgramFiles%\dotnet-tools` a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="30700-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="30700-122">Otevře se dialogové okno **společné vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="30700-122">The **Common Properties** dialog box opens.</span></span> 
- <span data-ttu-id="30700-123">Vyberte kartu **zabezpečení** . V části **uživatelské jméno nebo název skupiny**ověřte, zda má skupina uživatelé oprávnění k zápisu nebo úpravám adresáře.</span><span class="sxs-lookup"><span data-stu-id="30700-123">Select the **Security** tab. Under **Group or user names**, check whether the “Users” group has permission to write or modify the directory.</span></span> 
- <span data-ttu-id="30700-124">Pokud skupina uživatelé může zapisovat nebo upravovat adresář, použijte při instalaci nástrojů místo příkazu *dotnet-Tools*jiný název adresáře.</span><span class="sxs-lookup"><span data-stu-id="30700-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="30700-125">Nástroje nainstalujete spuštěním následujícího příkazu v příkazovém řádku se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="30700-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="30700-126">Během instalace vytvoří složku *dotnet-Tools* .</span><span class="sxs-lookup"><span data-stu-id="30700-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="30700-127">Spustit globální nástroj</span><span class="sxs-lookup"><span data-stu-id="30700-127">Run the global tool</span></span>

<span data-ttu-id="30700-128">**Možnost 1** Použít úplnou cestu s výzvou se zvýšenými oprávněními:</span><span class="sxs-lookup"><span data-stu-id="30700-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="30700-129">**Možnost 2** Přidejte nově vytvořenou složku do `%Path%`.</span><span class="sxs-lookup"><span data-stu-id="30700-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="30700-130">Tuto operaci je nutné provést pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="30700-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="30700-131">A spustit pomocí:</span><span class="sxs-lookup"><span data-stu-id="30700-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="30700-132">Odinstalace globálního nástroje</span><span class="sxs-lookup"><span data-stu-id="30700-132">Uninstall the global tool</span></span>

<span data-ttu-id="30700-133">Do příkazového řádku se zvýšenými oprávněními zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="30700-133">In an elevated prompt, type the following command:</span></span>

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linux"></a>[<span data-ttu-id="30700-134">Linux</span><span class="sxs-lookup"><span data-stu-id="30700-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[<span data-ttu-id="30700-135">macOS</span><span class="sxs-lookup"><span data-stu-id="30700-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="30700-136">Místní nástroje</span><span class="sxs-lookup"><span data-stu-id="30700-136">Local tools</span></span>

<span data-ttu-id="30700-137">Místní nástroje jsou vymezeny podle stromu podadresářů pro jednotlivé uživatele.</span><span class="sxs-lookup"><span data-stu-id="30700-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="30700-138">Při spuštění se zvýšenými oprávněními místní nástroje sdílí omezené uživatelské prostředí do prostředí se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="30700-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="30700-139">V systému Linux a macOS to vede k nastavování souborů s přístupem uživatele root.</span><span class="sxs-lookup"><span data-stu-id="30700-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="30700-140">Pokud uživatel přepne zpět na účet s omezeným přístupem, uživatel již nebude moci přistupovat k souborům nebo do něj zapisovat.</span><span class="sxs-lookup"><span data-stu-id="30700-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="30700-141">Proto se nedoporučuje instalovat nástroje, které vyžadují zvýšení oprávnění, protože místní nástroje.</span><span class="sxs-lookup"><span data-stu-id="30700-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="30700-142">Místo toho použijte možnost `--tool-path` a předchozí pokyny pro globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="30700-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="30700-143">Zvýšení úrovně během vývoje</span><span class="sxs-lookup"><span data-stu-id="30700-143">Elevation during development</span></span>

<span data-ttu-id="30700-144">Během vývoje můžete potřebovat vyšší úroveň přístupu k otestování aplikace.</span><span class="sxs-lookup"><span data-stu-id="30700-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="30700-145">Tento scénář je běžný například pro aplikace IoT.</span><span class="sxs-lookup"><span data-stu-id="30700-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="30700-146">Doporučujeme sestavit aplikaci bez zvýšení oprávnění a pak ji spustit se zvýšením oprávnění.</span><span class="sxs-lookup"><span data-stu-id="30700-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="30700-147">Existuje několik vzorů, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="30700-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="30700-148">Pomocí vygenerovaného spustitelného souboru (poskytuje nejlepší výkon při spuštění):</span><span class="sxs-lookup"><span data-stu-id="30700-148">Using generated executable (it provides the best startup performance):</span></span>

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- <span data-ttu-id="30700-149">Pomocí příkazu [dotnet Run](dotnet-run.md) s příznakem `—no-build` se vyhnete generování nových binárních souborů:</span><span class="sxs-lookup"><span data-stu-id="30700-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="30700-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30700-150">See also</span></span>

- [<span data-ttu-id="30700-151">Přehled globálních nástrojů .NET Core</span><span class="sxs-lookup"><span data-stu-id="30700-151">.NET Core Global Tools overview</span></span>](global-tools.md)
