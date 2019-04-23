---
ms.openlocfilehash: 3b7309347c643d89a28331c6ef3cac36085a969a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118468"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="602f0-101">Vykreslení WPF windows bez oříznutí při rozšiřování mimo jednoho monitoru</span><span class="sxs-lookup"><span data-stu-id="602f0-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

|   |   |
|---|---|
|<span data-ttu-id="602f0-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="602f0-102">Details</span></span>|<span data-ttu-id="602f0-103">V rozhraní .NET Framework 4.6 spuštěné v systému Windows 8 a vyšším, je vykreslen celé okno bez oříznutí při rozšiřuje mimo jednotné zobrazení v případě více monitorů.</span><span class="sxs-lookup"><span data-stu-id="602f0-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="602f0-104">Tím se liší od předchozích verzí rozhraní .NET Framework, které by oříznout WPF windows, které rozšířit nad rámec jednoho zobrazení.</span><span class="sxs-lookup"><span data-stu-id="602f0-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>|
|<span data-ttu-id="602f0-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="602f0-105">Suggestion</span></span>|<span data-ttu-id="602f0-106">Toto chování (jestli se má oříznout nebo ne) lze explicitně nastavit pomocí <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> prvek <code>&lt;appSettings&gt;</code> v konfiguračním souboru aplikace nebo tím, že nastavíte <code>EnableMultiMonitorDisplayClipping</code> vlastnost při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="602f0-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>|
|<span data-ttu-id="602f0-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="602f0-107">Scope</span></span>|<span data-ttu-id="602f0-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="602f0-108">Minor</span></span>|
|<span data-ttu-id="602f0-109">Version</span><span class="sxs-lookup"><span data-stu-id="602f0-109">Version</span></span>|<span data-ttu-id="602f0-110">4.6</span><span class="sxs-lookup"><span data-stu-id="602f0-110">4.6</span></span>|
|<span data-ttu-id="602f0-111">Type</span><span class="sxs-lookup"><span data-stu-id="602f0-111">Type</span></span>|<span data-ttu-id="602f0-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="602f0-112">Runtime</span></span>|
