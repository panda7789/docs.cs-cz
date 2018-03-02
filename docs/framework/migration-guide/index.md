---
title: "Příručka k migraci na rozhraní .NET Framework 4.7, 4.6 a 4.5 "
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 59c4ae2961b3e029ddd5f67afc9644042af95efb
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="migration-guide-to-the-net-framework-47-46-and-45"></a><span data-ttu-id="0ccd3-102">Příručka k migraci na rozhraní .NET Framework 4.7, 4.6 a 4.5</span><span class="sxs-lookup"><span data-stu-id="0ccd3-102">Migration Guide to the .NET Framework 4.7, 4.6, and 4.5</span></span> 
<span data-ttu-id="0ccd3-103">Pokud jste vytvořili vaší aplikaci pomocí dřívější verze rozhraní .NET Framework, můžete obvykle ho upgradovat na rozhraní .NET Framework 4.5 nebo jeho verze bodu (4.5.1 a 4.5.2), rozhraní .NET Framework 4.6 a jeho verze bodu (4.6.1 a 4.6.2), nebo 4.7 rozhraní .NET Framework a jeho bod verze, rozhraní .NET Framework 4.7.1, snadno.</span><span class="sxs-lookup"><span data-stu-id="0ccd3-103">If you created your app using an earlier version of the .NET Framework, you can generally upgrade it to the .NET Framework 4.5 and its point releases (4.5.1 and 4.5.2), the .NET Framework 4.6 and its point releases (4.6.1 and 4.6.2), or the .NET Framework 4.7 and its point release, the .NET Framework 4.7.1, easily.</span></span> <span data-ttu-id="0ccd3-104">Otevřete projekt v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0ccd3-104">Open your project in Visual Studio.</span></span> <span data-ttu-id="0ccd3-105">Pokud váš projekt byla vytvořena ve starší verzi sady Visual Studio **projektu kompatibility** automaticky otevře dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="0ccd3-105">If your project was created in an earlier version of Visual Studio, the **Project Compatibility** dialog box automatically opens.</span></span> <span data-ttu-id="0ccd3-106">Další informace o upgradu na projekt v sadě Visual Studio najdete v tématu [Port, migrace a Upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) a [Visual Studio 2017 cílení a kompatibilita platformy](/visualstudio/productinfo/vs2017-compatibility-vs).</span><span class="sxs-lookup"><span data-stu-id="0ccd3-106">For more information about upgrading a project in Visual Studio, see [Port, Migrate, and Upgrade Visual Studio Projects](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) and [Visual Studio 2017 Platform Targeting and Compatibility](/visualstudio/productinfo/vs2017-compatibility-vs).</span></span>  
  
 <span data-ttu-id="0ccd3-107">Ale některé změny v rozhraní .NET Framework vyžadovat změny vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="0ccd3-107">However, some changes in the .NET Framework require changes to your code.</span></span> <span data-ttu-id="0ccd3-108">Můžete také využít výhod funkcí, které je v rozhraní .NET Framework 4.5 a jeho verze bodu v rozhraní .NET Framework 4.6 a jeho verze bodu nebo v 4.7 rozhraní .NET Framework a její bod verze rozhraní .NET Framework 4.7.1 nový.</span><span class="sxs-lookup"><span data-stu-id="0ccd3-108">You may also want to take advantage of functionality that is new in the .NET Framework 4.5 and its point releases, in the .NET Framework 4.6 and its point releases, or in the .NET Framework 4.7 and its point release, the .NET Framework 4.7.1.</span></span> <span data-ttu-id="0ccd3-109">Provedením těchto typů změn do vaší aplikace pro novou verzi rozhraní .NET Framework se obvykle označuje jako *migrace*.</span><span class="sxs-lookup"><span data-stu-id="0ccd3-109">Making these types of changes to your app for a new version of the .NET Framework is typically referred to as *migration*.</span></span> <span data-ttu-id="0ccd3-110">Pokud aplikace nemá být provedena migrace, můžete ho spustit v rozhraní .NET Framework 4.5 nebo novější verze bez nutnosti rekompilace ho.</span><span class="sxs-lookup"><span data-stu-id="0ccd3-110">If your app doesn't have to be migrated, you can run it in the .NET Framework 4.5 or a later version without recompiling it.</span></span>  
  
## <a name="migration-resources"></a><span data-ttu-id="0ccd3-111">Migrace prostředků</span><span class="sxs-lookup"><span data-stu-id="0ccd3-111">Migration resources</span></span>  
 <span data-ttu-id="0ccd3-112">Před migrací aplikace z dřívějších verzí rozhraní .NET Framework verze 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 nebo 4.7.1, projděte si následující dokumenty:</span><span class="sxs-lookup"><span data-stu-id="0ccd3-112">Review the following documents before you migrate your app from earlier versions of the .NET Framework to version 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, or 4.7.1:</span></span>  
  
-   <span data-ttu-id="0ccd3-113">V tématu [verze a závislosti](../../../docs/framework/migration-guide/versions-and-dependencies.md) abyste pochopili základní každou verzi rozhraní .NET Framework verze CLR a přečtěte si pokyny pro cílení na aplikace úspěšně.</span><span class="sxs-lookup"><span data-stu-id="0ccd3-113">See [Versions and Dependencies](../../../docs/framework/migration-guide/versions-and-dependencies.md) to understand the CLR version underlying each version of the .NET Framework and to review guidelines for targeting your apps successfully.</span></span>  
  
-   <span data-ttu-id="0ccd3-114">Zkontrolujte [kompatibilita aplikací](../../../docs/framework/migration-guide/application-compatibility.md) informace o modulu runtime a odlišnosti ve změnách, které mohou ovlivnit vaše aplikace a jak bude zpracováván je cílení.</span><span class="sxs-lookup"><span data-stu-id="0ccd3-114">Review [Application Compatibility](../../../docs/framework/migration-guide/application-compatibility.md) to find out about runtime and retargeting changes that might affect your app and how to handle them.</span></span>  
  
-   <span data-ttu-id="0ccd3-115">Zkontrolujte [co je zastaralé v knihovně tříd](../../../docs/framework/whats-new/whats-obsolete.md) určit všechny typy nebo členy v váš kód, které jsou již zastaralé a doporučených alternativách.</span><span class="sxs-lookup"><span data-stu-id="0ccd3-115">Review [What's Obsolete in the Class Library](../../../docs/framework/whats-new/whats-obsolete.md) to determine any types or members in your code that have been made obsolete, and the recommended alternatives.</span></span>  
  
-   <span data-ttu-id="0ccd3-116">V tématu [co je nového](../../../docs/framework/whats-new/index.md) popis nové funkce, které chcete přidat do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="0ccd3-116">See [What's New](../../../docs/framework/whats-new/index.md) for descriptions of new features that you may want to add to your app.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ccd3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ccd3-117">See Also</span></span>  
 [<span data-ttu-id="0ccd3-118">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="0ccd3-118">Application Compatibility</span></span>](../../../docs/framework/migration-guide/application-compatibility.md)  
 [<span data-ttu-id="0ccd3-119">Migrace z rozhraní .NET Framework 1.1</span><span class="sxs-lookup"><span data-stu-id="0ccd3-119">Migrating from the .NET Framework 1.1</span></span>](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)  
 [<span data-ttu-id="0ccd3-120">Kompatibilita verzí</span><span class="sxs-lookup"><span data-stu-id="0ccd3-120">Version Compatibility</span></span>](../../../docs/framework/migration-guide/version-compatibility.md)  
 [<span data-ttu-id="0ccd3-121">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="0ccd3-121">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)  
 [<span data-ttu-id="0ccd3-122">Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo 4.5</span><span class="sxs-lookup"><span data-stu-id="0ccd3-122">How to: Configure an App to Support .NET Framework 4 or 4.5</span></span>](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)  
 [<span data-ttu-id="0ccd3-123">Co je nového</span><span class="sxs-lookup"><span data-stu-id="0ccd3-123">What's New</span></span>](../../../docs/framework/whats-new/index.md)  
 [<span data-ttu-id="0ccd3-124">Zastaralé položky v knihovně tříd</span><span class="sxs-lookup"><span data-stu-id="0ccd3-124">What's Obsolete in the Class Library</span></span>](../../../docs/framework/whats-new/whats-obsolete.md)  
 [<span data-ttu-id="0ccd3-125">Informace o sestavení a verze rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="0ccd3-125">.NET Framework Version and Assembly Information</span></span>](http://go.microsoft.com/fwlink/?LinkId=201701)  
 <span data-ttu-id="0ccd3-126">[Microsoft .NET Framework podporu životního cyklu zásad](http://go.microsoft.com/fwlink/?LinkId=196607) [problémy migrace v rozhraní .NET Framework 4](net-framework-4-migration-issues.md)</span><span class="sxs-lookup"><span data-stu-id="0ccd3-126">[Microsoft .NET Framework Support Lifecycle Policy](http://go.microsoft.com/fwlink/?LinkId=196607) [.NET Framework 4 migration issues](net-framework-4-migration-issues.md)</span></span>
