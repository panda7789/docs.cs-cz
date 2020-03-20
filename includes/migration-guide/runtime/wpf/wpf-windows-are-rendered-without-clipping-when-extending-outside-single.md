---
ms.openlocfilehash: 3b7309347c643d89a28331c6ef3cac36085a969a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858646"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="09acd-101">WPF okna jsou vykreslovány bez oříznutí při vysazení mimo jeden monitor</span><span class="sxs-lookup"><span data-stu-id="09acd-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

|   |   |
|---|---|
|<span data-ttu-id="09acd-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="09acd-102">Details</span></span>|<span data-ttu-id="09acd-103">V rozhraní .NET Framework 4.6 spuštěné v systému Windows 8 a vyšší, celé okno je vykreslen bez oříznutí, když rozšiřuje mimo jeden displej ve scénáři více monitorů.</span><span class="sxs-lookup"><span data-stu-id="09acd-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="09acd-104">To se liší od předchozích verzí rozhraní .NET Framework, které by klip WPF okna, která rozšířena mimo jeden displej.</span><span class="sxs-lookup"><span data-stu-id="09acd-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>|
|<span data-ttu-id="09acd-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="09acd-105">Suggestion</span></span>|<span data-ttu-id="09acd-106">Toto chování (zda klip nebo ne) <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> lze <code>&lt;appSettings&gt;</code> explicitně nastavit pomocí prvku v konfiguračním souboru aplikace nebo nastavením <code>EnableMultiMonitorDisplayClipping</code> vlastnosti při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="09acd-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>|
|<span data-ttu-id="09acd-107">Rozsah</span><span class="sxs-lookup"><span data-stu-id="09acd-107">Scope</span></span>|<span data-ttu-id="09acd-108">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="09acd-108">Minor</span></span>|
|<span data-ttu-id="09acd-109">Version</span><span class="sxs-lookup"><span data-stu-id="09acd-109">Version</span></span>|<span data-ttu-id="09acd-110">4.6</span><span class="sxs-lookup"><span data-stu-id="09acd-110">4.6</span></span>|
|<span data-ttu-id="09acd-111">Typ</span><span class="sxs-lookup"><span data-stu-id="09acd-111">Type</span></span>|<span data-ttu-id="09acd-112">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="09acd-112">Runtime</span></span>|
