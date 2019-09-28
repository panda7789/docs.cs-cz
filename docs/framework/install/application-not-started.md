---
title: Řešení potíží "tuto aplikaci nebylo možné spustit"
description: Přečtěte si, co dělat, když se zobrazí dialogové okno "Tato aplikace se nedá spustit".
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2019
ms.openlocfilehash: 2534979e8dea886c2d7298c57e12b66d7a962c69
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71401702"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a><span data-ttu-id="56ec3-103">Řešení potíží s chybovou zprávou "tuto aplikaci nebylo možné spustit"</span><span class="sxs-lookup"><span data-stu-id="56ec3-103">Troubleshooting a 'This application could not be started' error message</span></span>

<span data-ttu-id="56ec3-104">Aplikace, které jsou vyvíjené pro .NET Framework obvykle vyžadují, aby byla v systému nainstalovaná určitá verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="56ec3-104">Applications that are developed for the .NET Framework typically require that a specific version of the .NET Framework be installed on your system.</span></span> <span data-ttu-id="56ec3-105">V některých případech se můžete pokusit spustit aplikaci, aniž by byla nainstalována buď nainstalovaná verze, nebo očekávaná verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="56ec3-105">In some cases, you may attempt to run an application without either an installed version or the expected version of the .NET Framework present.</span></span> <span data-ttu-id="56ec3-106">Tím se často vytvoří chybové dialogové okno podobné následujícímu:</span><span class="sxs-lookup"><span data-stu-id="56ec3-106">This often produces an error dialog box like the following:</span></span>

![Tuto aplikaci nebylo možné spustit.](media/application-not-started/app-could-not-be-started.png)

<span data-ttu-id="56ec3-108">To obvykle znamená jednu z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="56ec3-108">This typically indicates one of the following conditions:</span></span>

- <span data-ttu-id="56ec3-109">Instalace .NET Framework v systému se stala poškozená.</span><span class="sxs-lookup"><span data-stu-id="56ec3-109">A .NET Framework installation on your system has become corrupted.</span></span>

- <span data-ttu-id="56ec3-110">Verze .NET Framework potřebná vaší aplikací nebyla zjištěna.</span><span class="sxs-lookup"><span data-stu-id="56ec3-110">The version of the .NET Framework needed by your application cannot be detected.</span></span>

<span data-ttu-id="56ec3-111">Chcete-li tento problém vyřešit, abyste mohli spustit aplikaci, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="56ec3-111">To address this issue so that you can run your application, do the following:</span></span>

1. <span data-ttu-id="56ec3-112">Stáhněte si [Nástroj pro opravu .NET Framework (NetFxRepairTool. exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span><span class="sxs-lookup"><span data-stu-id="56ec3-112">Download the [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135).</span></span> <span data-ttu-id="56ec3-113">Nástroj se spustí automaticky po dokončení stahování.</span><span class="sxs-lookup"><span data-stu-id="56ec3-113">The tool runs automatically when the download completes.</span></span>

1. <span data-ttu-id="56ec3-114">Pokud nástroj pro opravu .NET Framework doporučuje jakékoli další akce, jako například na následujícím obrázku, vyberte možnost **Další**.</span><span class="sxs-lookup"><span data-stu-id="56ec3-114">If the .NET Framework Repair Tool recommends any additional action, such as those shown in the following figure, select **Next**.</span></span>

   ![Doporučené změny](media/application-not-started/repair-tool-recommended-changes.png)

1. <span data-ttu-id="56ec3-116">Nástroje .NET Framework pro opravu zobrazí dialogové okno zobrazené na následujícím obrázku, které indikuje, že se změny dokončily.</span><span class="sxs-lookup"><span data-stu-id="56ec3-116">The .NET Framework Repair Tools displays a dialog box shown in the following figure to indicate that changes are complete.</span></span> <span data-ttu-id="56ec3-117">Nechejte dialogové okno otevřené a zkuste znovu spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="56ec3-117">Leave the dialog box open while you to try rerun your application.</span></span> <span data-ttu-id="56ec3-118">To by mělo být úspěšné, pokud nástroj pro opravu .NET Framework identifikoval a opravil poškozenou instalaci .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="56ec3-118">This should succeed if the .NET Framework Repair Tool has identified and corrected a corrupted .NET Framework installation.</span></span>

   ![Doporučené změny](media/application-not-started/repair-tool-changes-complete.png)

1. <span data-ttu-id="56ec3-120">Pokud vaše aplikace funguje úspěšně, vyberte tlačítko **Dokončit** .</span><span class="sxs-lookup"><span data-stu-id="56ec3-120">If your application runs successfully, select the **Finish** button.</span></span> <span data-ttu-id="56ec3-121">V opačném případě klikněte na tlačítko **Další** .</span><span class="sxs-lookup"><span data-stu-id="56ec3-121">Otherwise, select the **Next** button.</span></span>

1. <span data-ttu-id="56ec3-122">Pokud jste vybrali tlačítko **Další** , nástroj .NET Framework pro opravu zobrazí dialogové okno podobné následujícímu.</span><span class="sxs-lookup"><span data-stu-id="56ec3-122">If you selected the **Next** button, the .NET Framework Repair Tool displays a a dialog box like the following.</span></span> <span data-ttu-id="56ec3-123">Kliknutím na tlačítko **Dokončit** odešlete diagnostické informace společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="56ec3-123">Select the **Finish** button to send diagnostic information to Microsoft.</span></span>

   ![Nepovedlo se vyřešit problém.](media/application-not-started/repair-tool-no-resolution.png)

1. <span data-ttu-id="56ec3-125">Pokud stále nemůžete aplikaci spustit, nainstalujte nejnovější verzi .NET Framework, kterou podporuje vaše verze Windows, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="56ec3-125">If you still cannot run the application, install the latest version of the .NET Framework supported by your version of Windows, as shown in the following table.</span></span>

   |<span data-ttu-id="56ec3-126">Verze Windows</span><span class="sxs-lookup"><span data-stu-id="56ec3-126">Windows version</span></span>|<span data-ttu-id="56ec3-127">Instalace .NET Framework</span><span class="sxs-lookup"><span data-stu-id="56ec3-127">.NET Framework installation</span></span>|
   |---|---|
   |<span data-ttu-id="56ec3-128">Windows 10 – aktualizace pro výročí a novější verze</span><span class="sxs-lookup"><span data-stu-id="56ec3-128">Windows 10 Anniversary Update and later versions</span></span>|[<span data-ttu-id="56ec3-129">Modul runtime .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="56ec3-129">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="56ec3-130">Windows 10, listopadová aktualizace Windows 10</span><span class="sxs-lookup"><span data-stu-id="56ec3-130">Windows 10, Windows 10 November Update</span></span>|[<span data-ttu-id="56ec3-131">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="56ec3-131">.NET Framework 4.6.2</span></span>](https://www.microsoft.com/download/details.aspx?id=53345)|
   |<span data-ttu-id="56ec3-132">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="56ec3-132">Windows 8.1</span></span>|[<span data-ttu-id="56ec3-133">Modul runtime .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="56ec3-133">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="56ec3-134">Windows 8</span><span class="sxs-lookup"><span data-stu-id="56ec3-134">Windows 8</span></span>|[<span data-ttu-id="56ec3-135">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="56ec3-135">.NET Framework 4.6.1</span></span>](https://www.microsoft.com/download/details.aspx?id=49981)|
   |<span data-ttu-id="56ec3-136">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="56ec3-136">Windows 7 SP1</span></span>|[<span data-ttu-id="56ec3-137">Modul runtime .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="56ec3-137">.NET Framework 4.8 Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |<span data-ttu-id="56ec3-138">Windows Vista SP2</span><span class="sxs-lookup"><span data-stu-id="56ec3-138">Windows Vista SP2</span></span>|[<span data-ttu-id="56ec3-139">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="56ec3-139">.NET Framework 4.6</span></span>](https://www.microsoft.com/download/details.aspx?id=48130)|

   > [!NOTE]
   >  <span data-ttu-id="56ec3-140">.NET Framework 4,8 je předinstalována ve Windows 10 – 2019 aktualizace.</span><span class="sxs-lookup"><span data-stu-id="56ec3-140">.NET Framework 4.8 is preinstalled on Windows 10 May 2019 Update.</span></span>

1. <span data-ttu-id="56ec3-141">Pokus o spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="56ec3-141">Attempt to launch the application.</span></span>

1. <span data-ttu-id="56ec3-142">V některých případech se může zobrazit dialogové okno podobné následujícímu, které vás vyzve k instalaci .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="56ec3-142">In some cases, you may see a dialog box like the following, which asks you to install the .NET Framework 3.5.</span></span> <span data-ttu-id="56ec3-143">Vyberte **Stáhnout a nainstalovat tuto funkci** , pokud chcete nainstalovat .NET Framework 3,5, a pak aplikaci znovu spusťte.</span><span class="sxs-lookup"><span data-stu-id="56ec3-143">Select **Download and install this feature** to install the .NET Framework 3.5, then launch the application again.</span></span>

   ![Nepovedlo se vyřešit problém.](media/application-not-started/install-3-5.png)

## <a name="see-also"></a><span data-ttu-id="56ec3-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56ec3-145">See also</span></span>

- [<span data-ttu-id="56ec3-146">.NET Framework požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="56ec3-146">.NET Framework System Requirements</span></span>](../get-started/system-requirements.md)
- [<span data-ttu-id="56ec3-147">Průvodce instalací .NET Framework</span><span class="sxs-lookup"><span data-stu-id="56ec3-147">.NET Framework installation guide</span></span>](index.md)
- [<span data-ttu-id="56ec3-148">Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="56ec3-148">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](troubleshoot-blocked-installations-and-uninstallations.md)
