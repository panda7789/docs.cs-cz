---
title: Řešení potíží s touto aplikací nelze spustit.
description: Přečtěte si, co dělat, když se zobrazí dialogové okno Tato aplikace nelze spustit.
ms.date: 09/05/2019
ms.openlocfilehash: 864c6ea23e9a048f060eee39d904bd4377be5084
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965903"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a><span data-ttu-id="f1612-103">Poradce při potížích s chybovou zprávou Tuto aplikaci nelze spustit</span><span class="sxs-lookup"><span data-stu-id="f1612-103">Troubleshooting a 'This application could not be started' error message</span></span>

<span data-ttu-id="f1612-104">Aplikace vyvinuté pro rozhraní .NET Framework obvykle vyžadují, aby byla v systému nainstalována určitá verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1612-104">Applications that are developed for the .NET Framework typically require that a specific version of the .NET Framework be installed on your system.</span></span> <span data-ttu-id="f1612-105">V některých případech se můžete pokusit spustit aplikaci bez nainstalované verze nebo očekávané verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1612-105">In some cases, you may attempt to run an application without either an installed version or the expected version of the .NET Framework present.</span></span> <span data-ttu-id="f1612-106">To často vytváří chybové dialogové okno, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="f1612-106">This often produces an error dialog box like the following:</span></span>

![Tuto aplikaci nelze spustit.](media/application-not-started/app-could-not-be-started.png)

<span data-ttu-id="f1612-108">To obvykle označuje jednu z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="f1612-108">This typically indicates one of the following conditions:</span></span>

- <span data-ttu-id="f1612-109">Instalace rozhraní .NET Framework v systému byla poškozena.</span><span class="sxs-lookup"><span data-stu-id="f1612-109">A .NET Framework installation on your system has become corrupted.</span></span>

- <span data-ttu-id="f1612-110">Nelze zjistit verzi rozhraní .NET Framework, kterou vaše aplikace potřebuje.</span><span class="sxs-lookup"><span data-stu-id="f1612-110">The version of the .NET Framework needed by your application cannot be detected.</span></span>

<span data-ttu-id="f1612-111">Chcete-li tento problém vyřešit, abyste mohli aplikaci spustit, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="f1612-111">To address this issue so that you can run your application, do the following:</span></span>

1. <span data-ttu-id="f1612-112">Stáhněte si [nástroj .NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span><span class="sxs-lookup"><span data-stu-id="f1612-112">Download the [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span></span> <span data-ttu-id="f1612-113">Nástroj se spustí automaticky po dokončení stahování.</span><span class="sxs-lookup"><span data-stu-id="f1612-113">The tool runs automatically when the download completes.</span></span>

1. <span data-ttu-id="f1612-114">Pokud nástroj pro opravu rozhraní .NET Framework doporučuje jakoukoli další akci, například akci uvedenou na následujícím obrázku, vyberte **další**.</span><span class="sxs-lookup"><span data-stu-id="f1612-114">If the .NET Framework Repair Tool recommends any additional action, such as those shown in the following figure, select **Next**.</span></span>

   ![Doporučené změny](media/application-not-started/repair-tool-recommended-changes.png)

1. <span data-ttu-id="f1612-116">Nástroje pro opravu rozhraní .NET Framework zobrazí dialogové okno zobrazené na následujícím obrázku, které označuje, že změny jsou dokončeny.</span><span class="sxs-lookup"><span data-stu-id="f1612-116">The .NET Framework Repair Tools displays a dialog box shown in the following figure to indicate that changes are complete.</span></span> <span data-ttu-id="f1612-117">Chcete-li zkusit znovu spustit aplikaci, ponechejte dialogové okno otevřené.</span><span class="sxs-lookup"><span data-stu-id="f1612-117">Leave the dialog box open while you to try rerun your application.</span></span> <span data-ttu-id="f1612-118">To by mělo být úspěšné, pokud nástroj .NET Framework Repair Tool identifikoval a opravil poškozenou instalaci rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1612-118">This should succeed if the .NET Framework Repair Tool has identified and corrected a corrupted .NET Framework installation.</span></span>

   ![Doporučené změny](media/application-not-started/repair-tool-changes-complete.png)

1. <span data-ttu-id="f1612-120">Pokud se aplikace úspěšně spustí, vyberte tlačítko **Dokončit.**</span><span class="sxs-lookup"><span data-stu-id="f1612-120">If your application runs successfully, select the **Finish** button.</span></span> <span data-ttu-id="f1612-121">V opačném případě vyberte tlačítko **Další.**</span><span class="sxs-lookup"><span data-stu-id="f1612-121">Otherwise, select the **Next** button.</span></span>

1. <span data-ttu-id="f1612-122">Pokud jste vybrali tlačítko **Další,** nástroj pro opravu rozhraní .NET Framework zobrazí dialogové okno, jako je následující.</span><span class="sxs-lookup"><span data-stu-id="f1612-122">If you selected the **Next** button, the .NET Framework Repair Tool displays a dialog box like the following.</span></span> <span data-ttu-id="f1612-123">Chcete-li společnosti Microsoft odeslat diagnostické informace, vyberte tlačítko **Dokončit.**</span><span class="sxs-lookup"><span data-stu-id="f1612-123">Select the **Finish** button to send diagnostic information to Microsoft.</span></span>

   ![Problém nelze vyřešit.](media/application-not-started/repair-tool-no-resolution.png)

1. <span data-ttu-id="f1612-125">Pokud aplikaci stále nemůžete spustit, nainstalujte nejnovější verzi rozhraní .NET Framework podporovanou vaší verzí systému Windows, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="f1612-125">If you still cannot run the application, install the latest version of the .NET Framework supported by your version of Windows, as shown in the following table.</span></span>

   |<span data-ttu-id="f1612-126">Verze systému Windows</span><span class="sxs-lookup"><span data-stu-id="f1612-126">Windows version</span></span>|<span data-ttu-id="f1612-127">Instalace rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f1612-127">.NET Framework installation</span></span>|
   |---|---|
   |<span data-ttu-id="f1612-128">Aktualizace Windows 10 Anniversary update a novější verze</span><span class="sxs-lookup"><span data-stu-id="f1612-128">Windows 10 Anniversary Update and later versions</span></span>|[<span data-ttu-id="f1612-129">Doba běhu rozhraní .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="f1612-129">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="f1612-130">Windows 10, Listopadová aktualizace Windows 10</span><span class="sxs-lookup"><span data-stu-id="f1612-130">Windows 10, Windows 10 November Update</span></span>|[<span data-ttu-id="f1612-131">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f1612-131">.NET Framework 4.6.2</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |<span data-ttu-id="f1612-132">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="f1612-132">Windows 8.1</span></span>|[<span data-ttu-id="f1612-133">Doba běhu rozhraní .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="f1612-133">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="f1612-134">Windows 8</span><span class="sxs-lookup"><span data-stu-id="f1612-134">Windows 8</span></span>|[<span data-ttu-id="f1612-135">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="f1612-135">.NET Framework 4.6.1</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |<span data-ttu-id="f1612-136">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="f1612-136">Windows 7 SP1</span></span>|[<span data-ttu-id="f1612-137">Doba běhu rozhraní .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="f1612-137">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="f1612-138">Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="f1612-138">Windows Vista SP2</span></span>|[<span data-ttu-id="f1612-139">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="f1612-139">.NET Framework 4.6</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > <span data-ttu-id="f1612-140">Rozhraní .NET Framework 4.8 je předinstalováno v aktualizaci Windows 10 z května 2019.</span><span class="sxs-lookup"><span data-stu-id="f1612-140">.NET Framework 4.8 is preinstalled on Windows 10 May 2019 Update.</span></span>

1. <span data-ttu-id="f1612-141">Pokus o spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1612-141">Attempt to launch the application.</span></span>

1. <span data-ttu-id="f1612-142">V některých případech se může zobrazit dialogové okno, jako je následující, které vás požádá o instalaci rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="f1612-142">In some cases, you may see a dialog box like the following, which asks you to install the .NET Framework 3.5.</span></span> <span data-ttu-id="f1612-143">Vyberte **Stáhnout a nainstalujte tuto funkci,** nainstalujte rozhraní .NET Framework 3.5 a potom aplikaci znovu spusťte.</span><span class="sxs-lookup"><span data-stu-id="f1612-143">Select **Download and install this feature** to install the .NET Framework 3.5, then launch the application again.</span></span>

   ![Problém nelze vyřešit.](media/application-not-started/install-3-5.png)

## <a name="see-also"></a><span data-ttu-id="f1612-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1612-145">See also</span></span>

- [<span data-ttu-id="f1612-146">Požadavky na systém rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f1612-146">.NET Framework System Requirements</span></span>](../get-started/system-requirements.md)
- [<span data-ttu-id="f1612-147">Instalační příručka rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f1612-147">.NET Framework installation guide</span></span>](index.md)
- [<span data-ttu-id="f1612-148">Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f1612-148">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
