---
title: "Rozhraní .NET Framework a nesvázaná vydání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 83c3688afb3fe509d9a57eba8765cbd13bf581c8
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2018
---
# <a name="the-net-framework-and-out-of-band-releases"></a><span data-ttu-id="a5f96-102">Rozhraní .NET Framework a nesvázaná vydání</span><span class="sxs-lookup"><span data-stu-id="a5f96-102">The .NET Framework and Out-of-Band Releases</span></span>
<span data-ttu-id="a5f96-103">Rozhraní .NET Framework se vyvíjí pro různé platformy, jako jsou Windows Phone a aplikace pro Windows Store a tradiční stolní počítače a webové aplikace a maximalizuje opětovnou využitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="a5f96-103">The .NET Framework is evolving to accommodate different platforms such as Windows Phone and Windows Store apps as well as traditional desktop and web apps, and to maximize code reuse.</span></span> <span data-ttu-id="a5f96-104">Kromě regulárních verzí rozhraní .NET Framework vydáváme nové funkce OOB (out of band) z důvodu zlepšení vývoje napříč platformami nebo představení nových funkcí.</span><span class="sxs-lookup"><span data-stu-id="a5f96-104">In addition to our regular .NET Framework releases, we release new features out of band (OOB) to improve cross-platform development or to introduce new functionality.</span></span> <span data-ttu-id="a5f96-105">Toto téma popisuje budoucí směr rozhraní .NET Framework a jeho OOB verzí.</span><span class="sxs-lookup"><span data-stu-id="a5f96-105">This topic discusses the future direction of the .NET Framework and its OOB releases.</span></span>  
  
## <a name="advantages-of-oob-releases"></a><span data-ttu-id="a5f96-106">Výhody verzí OOB</span><span class="sxs-lookup"><span data-stu-id="a5f96-106">Advantages of OOB releases</span></span>  
 <span data-ttu-id="a5f96-107">Dodávání nových komponent nebo aktualizací komponent OOB umožňuje společnosti Microsoft poskytovat častější aktualizace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a5f96-107">Shipping new components or updates to components out of band enables Microsoft to provide more frequent updates to the .NET Framework.</span></span> <span data-ttu-id="a5f96-108">Kromě toho můžeme shromažďovat názory zákazníků a rychleji na ně reagovat.</span><span class="sxs-lookup"><span data-stu-id="a5f96-108">In addition, we can gather and respond to customer feedback more quickly.</span></span>  
  
 <span data-ttu-id="a5f96-109">Použijete-li ve své aplikaci funkci OOB, nemusí uživatelé instalovat nejnovější verzi rozhraní .NET Framework pro spuštění aplikace, protože sestavení OOB se nasazují s vaším balíčkem aplikací.</span><span class="sxs-lookup"><span data-stu-id="a5f96-109">When you use an OOB feature in your app, your users do not have to install the latest version of the .NET Framework to run your app, because the OOB assemblies deploy with your app package.</span></span>  
  
## <a name="how-oob-packages-are-distributed"></a><span data-ttu-id="a5f96-110">Distribuce balíčků OOB</span><span class="sxs-lookup"><span data-stu-id="a5f96-110">How OOB packages are distributed</span></span>  
<span data-ttu-id="a5f96-111">Vydání OOB pro základní common language runtime (CLR) součásti se doručují prostřednictvím [NuGet](https://www.nuget.org/), což je Správce balíčků pro rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="a5f96-111">OOB releases for core common language runtime (CLR) components are delivered through the [NuGet](https://www.nuget.org/), which is a package manager for .NET.</span></span> <span data-ttu-id="a5f96-112">Technologie NuGet umožňuje procházet a přidávat knihovny do projektů rozhraní .NET Framework z Průzkumníku řešení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5f96-112">NuGet enables you to browse and add libraries to your .NET Framework projects easily from the Solution Explorer in Visual Studio.</span></span> <span data-ttu-id="a5f96-113">Správce balíčků NuGet je součástí všech edicí sady Visual Studio, počínaje verzí Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="a5f96-113">NuGet is included with all editions of Visual Studio starting with Visual Studio 2012.</span></span> <span data-ttu-id="a5f96-114">Chcete-li zjistit, zda je nainstalován NuGet, vyhledejte **Správce balíčků knihoven** v sadě Visual Studio **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="a5f96-114">To see if NuGet is installed, look for **Library Package Manager** on the Visual Studio **Tools** menu.</span></span> <span data-ttu-id="a5f96-115">Pokud není nainstalován:</span><span class="sxs-lookup"><span data-stu-id="a5f96-115">If it’s not installed:</span></span>  
  
1.  <span data-ttu-id="a5f96-116">Na panelu nabídek Visual Studio zvolte **nástroje**, **rozšíření a aktualizace** (v sadě Visual Studio 2010, zvolte **Správce rozšíření**).</span><span class="sxs-lookup"><span data-stu-id="a5f96-116">On the Visual Studio menu bar, choose **Tools**, **Extensions and Updates** (in Visual Studio 2010, choose **Extension Manager**).</span></span>  
  
     <span data-ttu-id="a5f96-117">**Rozšíření a aktualizace** otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="a5f96-117">The **Extensions and Updates** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="a5f96-118">Zvolte **Online**, **Správce balíčků NuGet**a potom zvolte **Stáhnout**.</span><span class="sxs-lookup"><span data-stu-id="a5f96-118">Choose **Online**, **NuGet Package Manager**, and then choose **Download**.</span></span>  
  
3.  <span data-ttu-id="a5f96-119">Po dokončení stahování restartujte aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5f96-119">After the download completes, restart Visual Studio.</span></span>  
  
 <span data-ttu-id="a5f96-120">Podrobné pokyny k instalaci naleznete v části [instalace NuGet](http://docs.nuget.org/docs/start-here/installing-nuget) na webu NuGet dokumentace.</span><span class="sxs-lookup"><span data-stu-id="a5f96-120">For detailed installation instructions, see [Installing NuGet](http://docs.nuget.org/docs/start-here/installing-nuget) on the NuGet Docs website.</span></span> <span data-ttu-id="a5f96-121">Další informace o systému NuGet najdete v tématu [NuGet dokumentaci](http://docs.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="a5f96-121">For more information about NuGet, see the [NuGet documentation](http://docs.nuget.org/).</span></span>  
  
## <a name="using-a-nuget-oob-package"></a><span data-ttu-id="a5f96-122">Použití balíčku NuGet OOB</span><span class="sxs-lookup"><span data-stu-id="a5f96-122">Using a NuGet OOB package</span></span>  
 <span data-ttu-id="a5f96-123">Po instalaci balíčku NuGet můžete procházet a přidávat odkazy na balíčky NuGet pomocí Průzkumníka řešení v sadě Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="a5f96-123">After you install NuGet, you can browse and add references to NuGet packages by using Solution Explorer in Visual Studio:</span></span>  
  
1.  <span data-ttu-id="a5f96-124">Otevřete místní nabídky pro váš projekt v sadě Visual Studio a zvolte **spravovat balíčky NuGet**.</span><span class="sxs-lookup"><span data-stu-id="a5f96-124">Open the shortcut menu for your project in Visual Studio, and then choose **Manage NuGet Packages**.</span></span> <span data-ttu-id="a5f96-125">(Tato možnost je dostupná také prostřednictvím **projektu** nabídky.)</span><span class="sxs-lookup"><span data-stu-id="a5f96-125">(This option is also available from the **Project** menu.)</span></span>  
  
2.  <span data-ttu-id="a5f96-126">V levém podokně vyberte **Online**.</span><span class="sxs-lookup"><span data-stu-id="a5f96-126">In the left pane, choose **Online**.</span></span>  
  
3.  <span data-ttu-id="a5f96-127">Pokud chcete použít předběžné verze balíčků, v rozevíracím seznamu v prostředním podokně, vyberte **zahrnout předběžné verze** místo **pouze stabilní**.</span><span class="sxs-lookup"><span data-stu-id="a5f96-127">If you want to use prerelease packages, in the drop-down list box in the middle pane, choose **Include Prerelease** instead of **Stable Only**.</span></span>  
  
4.  <span data-ttu-id="a5f96-128">V pravém podokně, použijte **vyhledávání** pole a vyhledejte balíček, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="a5f96-128">In the right pane, use the **Search** box to locate the package you would like to use.</span></span> <span data-ttu-id="a5f96-129">Některé balíčky společnosti Microsoft jsou označeny logem rozhraní Microsoft .NET Framework a všechny identifikují společnost Microsoft jako vydavatele.</span><span class="sxs-lookup"><span data-stu-id="a5f96-129">Some Microsoft packages are identified by the Microsoft .NET Framework logo, and all identify Microsoft as the publisher.</span></span>  
  
 <span data-ttu-id="a5f96-130">![Správce balíčků NuGet](../../../docs/framework/get-started/media/clrnugetdialog.png "clrNugetDialog")</span><span class="sxs-lookup"><span data-stu-id="a5f96-130">![NuGet Package Manager](../../../docs/framework/get-started/media/clrnugetdialog.png "clrNugetDialog")</span></span>  
  
 <span data-ttu-id="a5f96-131">Jak bylo zmíněno dříve, pokud nasadíte aplikaci, která používá balíček OOB, sestavení OOB bude dodáváno spolu s balíčkem aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5f96-131">As mentioned previously, when you deploy an app that uses an OOB package, the OOB assemblies will ship with your app package.</span></span>  
  
## <a name="types-of-oob-releases"></a><span data-ttu-id="a5f96-132">Typy verzí OOB</span><span class="sxs-lookup"><span data-stu-id="a5f96-132">Types of OOB releases</span></span>  
 <span data-ttu-id="a5f96-133">Balíček OOB obvykle má jednu nebo více předprodejních verzí a stabilní verzi.</span><span class="sxs-lookup"><span data-stu-id="a5f96-133">Typically, an OOB package has one or more prerelease versions and a stable version.</span></span> <span data-ttu-id="a5f96-134">Licence, které doprovází předběžné verze obvykle neumožňuje opětovné distribuci, ale můžete vyzkoušet na balíček a poskytnout zpětnou vazbu.</span><span class="sxs-lookup"><span data-stu-id="a5f96-134">The license that accompanies a prerelease doesn't typically allow redistribution, but enables you to try out a package and provide feedback.</span></span> <span data-ttu-id="a5f96-135">Zpětná vazba je součástí všech aktualizací balíčku.</span><span class="sxs-lookup"><span data-stu-id="a5f96-135">Feedback is incorporated in any updates made to the package.</span></span> <span data-ttu-id="a5f96-136">Konečná vydaná verze je distribuována jako stabilní balíček NuGet a obsahuje licenci, která umožňuje tento balíček NuGet distribuovat s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="a5f96-136">A final release is distributed as a stable package with NuGet and includes a license that lets you redistribute the NuGet package with your app.</span></span> <span data-ttu-id="a5f96-137">Microsoft podporuje stabilní balíčky.</span><span class="sxs-lookup"><span data-stu-id="a5f96-137">Stable packages are supported by Microsoft.</span></span> <span data-ttu-id="a5f96-138">Společnost Microsoft poskytuje podporu technologie IntelliSense, jakož i jiné typy dokumentace například příspěvcích na blogu a fórum odpovědi pro všechny balíčky.</span><span class="sxs-lookup"><span data-stu-id="a5f96-138">Microsoft provides IntelliSense support as well as other types of documentation such as blog posts and forum answers for all packages.</span></span> <span data-ttu-id="a5f96-139">Zdrojový kód kromě toho může být k dispozici s některé, ale ne všechny balíčky.</span><span class="sxs-lookup"><span data-stu-id="a5f96-139">In addition, source code may be available with some, but not all, packages.</span></span> <span data-ttu-id="a5f96-140">Pro oznámení o nových a aktualizovaných balíčků, můžete odebírat [na blogu .NET Framework](http://blogs.msdn.com/b/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="a5f96-140">For announcements regarding new and updated packages, you can subscribe to [the .NET Framework Blog](http://blogs.msdn.com/b/dotnet/).</span></span>  
  
 <span data-ttu-id="a5f96-141">Chcete-li najít předprodejní a stabilní balíčky, zvolte **zahrnout předprodejní** Správce balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="a5f96-141">To find both prerelease and stable packages, choose **Include Prerelease** in the NuGet Package Manager.</span></span>  
  
 <span data-ttu-id="a5f96-142">Pokud chcete být informováni o stabilní balíčku verze, přihlášení k odběru [rozhraní .NET Framework kanálu](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).</span><span class="sxs-lookup"><span data-stu-id="a5f96-142">If you want to be notified of stable package releases, subscribe to [the .NET Framework feed](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f96-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5f96-143">See Also</span></span>  
 [<span data-ttu-id="a5f96-144">Začínáme</span><span class="sxs-lookup"><span data-stu-id="a5f96-144">Getting Started</span></span>](../../../docs/framework/get-started/index.md)
