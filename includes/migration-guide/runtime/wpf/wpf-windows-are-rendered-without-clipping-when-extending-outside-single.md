---
ms.openlocfilehash: 2e974d277d6659aaada321b2a7e7a604df78a7bd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858646"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="c939d-101">Vykreslení WPF windows bez oříznutí při rozšiřování mimo jednoho monitoru</span><span class="sxs-lookup"><span data-stu-id="c939d-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c939d-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c939d-102">Details</span></span>|<span data-ttu-id="c939d-103">V rozhraní .NET Framework 4.6 spuštěné v systému Windows 8 a vyšším, je vykreslen celé okno bez oříznutí při rozšiřuje mimo jednotné zobrazení v případě více monitorů.</span><span class="sxs-lookup"><span data-stu-id="c939d-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="c939d-104">Tím se liší od předchozích verzí rozhraní .NET Framework, které by oříznout WPF windows, které rozšířit nad rámec jednoho zobrazení.</span><span class="sxs-lookup"><span data-stu-id="c939d-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>|
|<span data-ttu-id="c939d-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="c939d-105">Suggestion</span></span>|<span data-ttu-id="c939d-106">Toto chování (jestli se má oříznout nebo ne) lze explicitně nastavit pomocí <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> prvek <code>&lt;appSettings&gt;</code> v konfiguračním souboru aplikace nebo tím, že nastavíte <code>EnableMultiMonitorDisplayClipping</code> vlastnost při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c939d-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>|
|<span data-ttu-id="c939d-107">Scope</span><span class="sxs-lookup"><span data-stu-id="c939d-107">Scope</span></span>|<span data-ttu-id="c939d-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="c939d-108">Minor</span></span>|
|<span data-ttu-id="c939d-109">Version</span><span class="sxs-lookup"><span data-stu-id="c939d-109">Version</span></span>|<span data-ttu-id="c939d-110">4.6</span><span class="sxs-lookup"><span data-stu-id="c939d-110">4.6</span></span>|
|<span data-ttu-id="c939d-111">type</span><span class="sxs-lookup"><span data-stu-id="c939d-111">Type</span></span>|<span data-ttu-id="c939d-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c939d-112">Runtime</span></span>|

