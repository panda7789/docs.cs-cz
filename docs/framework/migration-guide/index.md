---
title: 'Příručka k migraci na rozhraní .NET Framework 4.7, 4.6 a 4.5 '
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9c537aa8fff5fdf823effeae42382ee499efaf4
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221499"
---
# <a name="migration-guide-to-the-net-framework-47-46-and-45"></a><span data-ttu-id="e9aa4-102">Příručka k migraci na rozhraní .NET Framework 4.7, 4.6 a 4.5</span><span class="sxs-lookup"><span data-stu-id="e9aa4-102">Migration Guide to the .NET Framework 4.7, 4.6, and 4.5</span></span>

<span data-ttu-id="e9aa4-103">Pokud jste aplikaci vytvořili pomocí starší verze rozhraní .NET Framework, obecně upgradem ji na verzi rozhraní .NET Framework 4.5 a jeho novější vydání (4.5.1 a 4.5.2), rozhraní .NET Framework 4.6 a jeho novější vydání (4.6.1 a 4.6.2), nebo rozhraní .NET Framework 4.7 a jeho bod snadno uvolní (4.7.1 a 4.7.2).</span><span class="sxs-lookup"><span data-stu-id="e9aa4-103">If you created your app using an earlier version of the .NET Framework, you can generally upgrade it to the .NET Framework 4.5 and its point releases (4.5.1 and 4.5.2), the .NET Framework 4.6 and its point releases (4.6.1 and 4.6.2), or the .NET Framework 4.7 and its point releases (4.7.1 and 4.7.2) easily.</span></span> <span data-ttu-id="e9aa4-104">Otevřete svůj projekt v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e9aa4-104">Open your project in Visual Studio.</span></span> <span data-ttu-id="e9aa4-105">Pokud váš projekt byl vytvořen v dřívější verzi sady Visual Studio **kompatibilita projektu** automaticky otevře se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e9aa4-105">If your project was created in an earlier version of Visual Studio, the **Project Compatibility** dialog box automatically opens.</span></span> <span data-ttu-id="e9aa4-106">Další informace o upgradu projektu v sadě Visual Studio najdete v tématu [Port, migrace a Upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) a [Visual Studio 2017 cílení na platformy a Kompatibilita](/visualstudio/productinfo/vs2017-compatibility-vs).</span><span class="sxs-lookup"><span data-stu-id="e9aa4-106">For more information about upgrading a project in Visual Studio, see [Port, Migrate, and Upgrade Visual Studio Projects](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) and [Visual Studio 2017 Platform Targeting and Compatibility](/visualstudio/productinfo/vs2017-compatibility-vs).</span></span>

 <span data-ttu-id="e9aa4-107">Nicméně některé změny v rozhraní .NET Framework vyžadují změny kódu.</span><span class="sxs-lookup"><span data-stu-id="e9aa4-107">However, some changes in the .NET Framework require changes to your code.</span></span> <span data-ttu-id="e9aa4-108">Můžete také využít výhod funkcí, které jsou nové v rozhraní .NET Framework 4.5 a jeho novější vydání, v rozhraní .NET Framework 4.6 a jeho novější vydání nebo v rozhraní .NET Framework 4.7 a jeho verze.</span><span class="sxs-lookup"><span data-stu-id="e9aa4-108">You may also want to take advantage of functionality that is new in the .NET Framework 4.5 and its point releases, in the .NET Framework 4.6 and its point releases, or in the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="e9aa4-109">Provedení těchto typů změn aplikace pro novou verzi rozhraní .NET Framework se obvykle označuje jako *migrace*.</span><span class="sxs-lookup"><span data-stu-id="e9aa4-109">Making these types of changes to your app for a new version of the .NET Framework is typically referred to as *migration*.</span></span> <span data-ttu-id="e9aa4-110">Pokud aplikace nemá být přenesena, můžete ji spustit v rozhraní .NET Framework 4.5 nebo novější verze bez opětovné kompilace.</span><span class="sxs-lookup"><span data-stu-id="e9aa4-110">If your app doesn't have to be migrated, you can run it in the .NET Framework 4.5 or a later version without recompiling it.</span></span>

## <a name="migration-resources"></a><span data-ttu-id="e9aa4-111">Zdroje migrace</span><span class="sxs-lookup"><span data-stu-id="e9aa4-111">Migration resources</span></span>

<span data-ttu-id="e9aa4-112">Před migrací vaší aplikace z předchozích verzí rozhraní .NET Framework verze 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 nebo 4.7.2, přečtěte si následující dokumenty:</span><span class="sxs-lookup"><span data-stu-id="e9aa4-112">Review the following documents before you migrate your app from earlier versions of the .NET Framework to version 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, or 4.7.2:</span></span>

- <span data-ttu-id="e9aa4-113">Zobrazit [verze a závislosti](versions-and-dependencies.md) pochopit verzi CLR v rámci každé verze rozhraní .NET Framework a kde naleznete pokyny pro úspěšné cílení na své aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9aa4-113">See [Versions and Dependencies](versions-and-dependencies.md) to understand the CLR version underlying each version of the .NET Framework and to review guidelines for targeting your apps successfully.</span></span>

- <span data-ttu-id="e9aa4-114">Kontrola [kompatibilita aplikací](application-compatibility.md) najdete informace o modulu runtime a změně cíle změn, které může mít vliv na vaše aplikace a způsob jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="e9aa4-114">Review [Application Compatibility](application-compatibility.md) to find out about runtime and retargeting changes that might affect your app and how to handle them.</span></span>

- <span data-ttu-id="e9aa4-115">Kontrola [What's Obsolete in knihovny tříd](../whats-new/whats-obsolete.md) určit všechny typy nebo členy v kódu, které jsou již zastaralé a doporučené alternativy.</span><span class="sxs-lookup"><span data-stu-id="e9aa4-115">Review [What's Obsolete in the Class Library](../whats-new/whats-obsolete.md) to determine any types or members in your code that have been made obsolete, and the recommended alternatives.</span></span>

- <span data-ttu-id="e9aa4-116">Zobrazit [novinky](../whats-new/index.md) popisy nových funkcí, které chcete přidat do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9aa4-116">See [What's New](../whats-new/index.md) for descriptions of new features that you may want to add to your app.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9aa4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9aa4-117">See also</span></span>

- [<span data-ttu-id="e9aa4-118">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="e9aa4-118">Application Compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="e9aa4-119">Migrace z rozhraní .NET Framework 1.1</span><span class="sxs-lookup"><span data-stu-id="e9aa4-119">Migrating from the .NET Framework 1.1</span></span>](migrating-from-the-net-framework-1-1.md)
- [<span data-ttu-id="e9aa4-120">Kompatibilita verzí</span><span class="sxs-lookup"><span data-stu-id="e9aa4-120">Version Compatibility</span></span>](version-compatibility.md)
- [<span data-ttu-id="e9aa4-121">Verze a závislosti</span><span class="sxs-lookup"><span data-stu-id="e9aa4-121">Versions and Dependencies</span></span>](versions-and-dependencies.md)
- [<span data-ttu-id="e9aa4-122">Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="e9aa4-122">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [<span data-ttu-id="e9aa4-123">Co je nového</span><span class="sxs-lookup"><span data-stu-id="e9aa4-123">What's New</span></span>](../whats-new/index.md)
- [<span data-ttu-id="e9aa4-124">Zastaralé položky v knihovně tříd</span><span class="sxs-lookup"><span data-stu-id="e9aa4-124">What's Obsolete in the Class Library</span></span>](../whats-new/whats-obsolete.md)
- [<span data-ttu-id="e9aa4-125">Verze rozhraní .NET framework a informace o sestavení</span><span class="sxs-lookup"><span data-stu-id="e9aa4-125">.NET Framework Version and Assembly Information</span></span>](https://go.microsoft.com/fwlink/?LinkId=201701)
- [<span data-ttu-id="e9aa4-126">Zásady životního cyklu podpory rozhraní Microsoft .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e9aa4-126">Microsoft .NET Framework Support Lifecycle Policy</span></span>](https://go.microsoft.com/fwlink/?LinkId=196607)
- [<span data-ttu-id="e9aa4-127">Problémy s migrací rozhraní .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="e9aa4-127">.NET Framework 4 migration issues</span></span>](net-framework-4-migration-issues.md)