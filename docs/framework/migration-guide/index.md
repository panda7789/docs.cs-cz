---
title: 'Průvodce migrací na .NET Framework 4,8, 4,7, 4,6 a 4,5 '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: 2fa992e1c0897d360f322581888c51dca8d8a734
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974975"
---
# <a name="migration-guide-to-the-net-framework-48-47-46-and-45"></a><span data-ttu-id="e12b9-102">Průvodce migrací na .NET Framework 4,8, 4,7, 4,6 a 4,5</span><span class="sxs-lookup"><span data-stu-id="e12b9-102">Migration Guide to the .NET Framework 4.8, 4.7, 4.6, and 4.5</span></span>

<span data-ttu-id="e12b9-103">Pokud jste aplikaci vytvořili pomocí starší verze .NET Framework, můžete ji obecně upgradovat na .NET Framework 4,5 a jejich vydání (4.5.1 a 4.5.2), .NET Framework 4,6 a v jejích verzích (4.6.1 a 4.6.2), .NET Framework 4,7 a jejich verze v bodech ( 4.7.1 a 4.7.2) nebo je snadno .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="e12b9-103">If you created your app using an earlier version of the .NET Framework, you can generally upgrade it to .NET Framework 4.5 and its point releases (4.5.1 and 4.5.2), .NET Framework 4.6 and its point releases (4.6.1 and 4.6.2), .NET Framework 4.7 and its point releases (4.7.1 and 4.7.2), or .NET Framework 4.8 easily.</span></span> <span data-ttu-id="e12b9-104">Otevřete projekt v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e12b9-104">Open your project in Visual Studio.</span></span> <span data-ttu-id="e12b9-105">Pokud byl projekt vytvořen v dřívější verzi sady Visual Studio, otevře se dialogové okno **Kompatibilita projektu** automaticky.</span><span class="sxs-lookup"><span data-stu-id="e12b9-105">If your project was created in an earlier version of Visual Studio, the **Project Compatibility** dialog box automatically opens.</span></span> <span data-ttu-id="e12b9-106">Další informace o upgradu projektu v aplikaci Visual Studio naleznete v tématu [port, migrace a upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) a [cílení na platformu a kompatibilita platformy Visual Studio 2019](/visualstudio/releases/2019/compatibility).</span><span class="sxs-lookup"><span data-stu-id="e12b9-106">For more information about upgrading a project in Visual Studio, see [Port, Migrate, and Upgrade Visual Studio Projects](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) and [Visual Studio 2019 Platform Targeting and Compatibility](/visualstudio/releases/2019/compatibility).</span></span>

 <span data-ttu-id="e12b9-107">Některé změny v .NET Framework však vyžadují změny kódu.</span><span class="sxs-lookup"><span data-stu-id="e12b9-107">However, some changes in the .NET Framework require changes to your code.</span></span> <span data-ttu-id="e12b9-108">Můžete také využít výhody funkcí, které jsou novinkou v .NET Framework 4,5 a jeho vydání, v .NET Framework 4,6 a v jeho vydáních, v .NET Framework 4,7 a v jeho vydaných verzích nebo v .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="e12b9-108">You may also want to take advantage of functionality that is new in .NET Framework 4.5 and its point releases, in .NET Framework 4.6 and its point releases, in .NET Framework 4.7 and its point releases, or in .NET Framework 4.8.</span></span> <span data-ttu-id="e12b9-109">Provedení těchto typů změn aplikace pro novou verzi .NET Framework se obvykle označuje jako *migrace*.</span><span class="sxs-lookup"><span data-stu-id="e12b9-109">Making these types of changes to your app for a new version of the .NET Framework is typically referred to as *migration*.</span></span> <span data-ttu-id="e12b9-110">Pokud vaše aplikace nemusí být migrována, můžete ji spustit v .NET Framework 4,5 nebo novější verzi bez jejich opětovné kompilace.</span><span class="sxs-lookup"><span data-stu-id="e12b9-110">If your app doesn't have to be migrated, you can run it in the .NET Framework 4.5 or a later version without recompiling it.</span></span>

## <a name="migration-resources"></a><span data-ttu-id="e12b9-111">Prostředky migrace</span><span class="sxs-lookup"><span data-stu-id="e12b9-111">Migration resources</span></span>

<span data-ttu-id="e12b9-112">Před migrací aplikace z dřívějších verzí .NET Framework na verzi 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 nebo 4,8 se podívejte na následující dokumenty:</span><span class="sxs-lookup"><span data-stu-id="e12b9-112">Review the following documents before you migrate your app from earlier versions of the .NET Framework to version 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2, or 4.8:</span></span>

- <span data-ttu-id="e12b9-113">Podívejte se na [verze a závislosti](versions-and-dependencies.md) , abyste pochopili verzi CLR založenou na jednotlivých verzích .NET Framework a zkontrolovali pokyny pro úspěšné cílení na vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="e12b9-113">See [Versions and Dependencies](versions-and-dependencies.md) to understand the CLR version underlying each version of the .NET Framework and to review guidelines for targeting your apps successfully.</span></span>

- <span data-ttu-id="e12b9-114">Přečtěte si informace o [kompatibilitě aplikací](application-compatibility.md) a zjistěte, jak se týkají prostředí runtime a změny cíle, které by mohly ovlivnit vaši aplikaci a jak je zpracovat.</span><span class="sxs-lookup"><span data-stu-id="e12b9-114">Review [Application compatibility](application-compatibility.md) to find out about runtime and retargeting changes that might affect your app and how to handle them.</span></span>

- <span data-ttu-id="e12b9-115">Přečtěte si, [co je zastaralé v knihovně tříd](../whats-new/whats-obsolete.md) a určete všechny typy nebo členy v kódu, které byly vytvořeny jako zastaralé, a Doporučené alternativy.</span><span class="sxs-lookup"><span data-stu-id="e12b9-115">Review [What's Obsolete in the Class Library](../whats-new/whats-obsolete.md) to determine any types or members in your code that have been made obsolete, and the recommended alternatives.</span></span>

- <span data-ttu-id="e12b9-116">Popis nových funkcí, které můžete chtít přidat do vaší aplikace, najdete v tématu [novinky](../whats-new/index.md) .</span><span class="sxs-lookup"><span data-stu-id="e12b9-116">See [What's New](../whats-new/index.md) for descriptions of new features that you may want to add to your app.</span></span>

## <a name="see-also"></a><span data-ttu-id="e12b9-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e12b9-117">See also</span></span>

- [<span data-ttu-id="e12b9-118">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="e12b9-118">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="e12b9-119">Migrace z rozhraní .NET Framework 1.1</span><span class="sxs-lookup"><span data-stu-id="e12b9-119">Migrating from the .NET Framework 1.1</span></span>](migrating-from-the-net-framework-1-1.md)
- [<span data-ttu-id="e12b9-120">Kompatibilita verzí</span><span class="sxs-lookup"><span data-stu-id="e12b9-120">Version Compatibility</span></span>](version-compatibility.md)
- [<span data-ttu-id="e12b9-121">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="e12b9-121">Versions and Dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="e12b9-122">Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí</span><span class="sxs-lookup"><span data-stu-id="e12b9-122">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [<span data-ttu-id="e12b9-123">Co je nového</span><span class="sxs-lookup"><span data-stu-id="e12b9-123">What's New</span></span>](../whats-new/index.md)
- [<span data-ttu-id="e12b9-124">Zastaralé položky v knihovně tříd</span><span class="sxs-lookup"><span data-stu-id="e12b9-124">What's Obsolete in the Class Library</span></span>](../whats-new/whats-obsolete.md)
- [<span data-ttu-id="e12b9-125">.NET Framework oficiálních zásad podpory</span><span class="sxs-lookup"><span data-stu-id="e12b9-125">.NET Framework official support policy</span></span>](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [<span data-ttu-id="e12b9-126">Problémy s migrací rozhraní .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="e12b9-126">.NET Framework 4 migration issues</span></span>](net-framework-4-migration-issues.md)
