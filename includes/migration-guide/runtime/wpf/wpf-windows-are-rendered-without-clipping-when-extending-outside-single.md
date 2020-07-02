---
ms.openlocfilehash: d276e2bbf24c8b2389a0a8078c62c327c3729d50
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621157"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="c5d6b-101">Okna WPF se vykreslují bez oříznutí, když se rozšíří mimo jeden monitor.</span><span class="sxs-lookup"><span data-stu-id="c5d6b-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

#### <a name="details"></a><span data-ttu-id="c5d6b-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c5d6b-102">Details</span></span>

<span data-ttu-id="c5d6b-103">V .NET Framework 4,6 spuštěném v systému Windows 8 a vyšším se celé okno vykreslí bez oříznutí, když se v případě více monitorů rozšíří mimo jeden displej.</span><span class="sxs-lookup"><span data-stu-id="c5d6b-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="c5d6b-104">To se liší od předchozích verzí .NET Framework, které by mohly oříznout okna WPF, která přesahují rámec jednoho zobrazení.</span><span class="sxs-lookup"><span data-stu-id="c5d6b-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c5d6b-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="c5d6b-105">Suggestion</span></span>

<span data-ttu-id="c5d6b-106">Toto chování (bez ohledu na to, jestli se má oříznout), je možné explicitně nastavit pomocí <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> elementu v <code>&lt;appSettings&gt;</code> konfiguračním souboru aplikace nebo nastavením <code>EnableMultiMonitorDisplayClipping</code> vlastnosti při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5d6b-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>

| <span data-ttu-id="c5d6b-107">Name</span><span class="sxs-lookup"><span data-stu-id="c5d6b-107">Name</span></span>    | <span data-ttu-id="c5d6b-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c5d6b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c5d6b-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c5d6b-109">Scope</span></span>   |<span data-ttu-id="c5d6b-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="c5d6b-110">Minor</span></span>|
|<span data-ttu-id="c5d6b-111">Verze</span><span class="sxs-lookup"><span data-stu-id="c5d6b-111">Version</span></span>|<span data-ttu-id="c5d6b-112">4.6</span><span class="sxs-lookup"><span data-stu-id="c5d6b-112">4.6</span></span>|
|<span data-ttu-id="c5d6b-113">Typ</span><span class="sxs-lookup"><span data-stu-id="c5d6b-113">Type</span></span>|<span data-ttu-id="c5d6b-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c5d6b-114">Runtime</span></span>|
