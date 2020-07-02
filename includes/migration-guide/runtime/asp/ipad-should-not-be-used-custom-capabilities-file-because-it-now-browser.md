---
ms.openlocfilehash: af10716fe5f4c07091e8605cdf620e4a499fb1e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619942"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a><span data-ttu-id="f9d89-101">IPad by se neměl používat v souboru vlastních schopností, protože je teď funkcí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="f9d89-101">IPad should not be used in custom capabilities file because it is now a browser capability</span></span>

#### <a name="details"></a><span data-ttu-id="f9d89-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f9d89-102">Details</span></span>

<span data-ttu-id="f9d89-103">Počínaje .NET Framework 4,5 je iPad identifikátorem ve výchozím souboru schopností prohlížeče ASP.NET, takže by se neměl používat ve vlastním souboru schopností.</span><span class="sxs-lookup"><span data-stu-id="f9d89-103">Beginning in .NET Framework 4.5, iPad is an identifier in the default ASP.NET browser capabilities file, so it should not be used in a custom capabilities file</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f9d89-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="f9d89-104">Suggestion</span></span>

<span data-ttu-id="f9d89-105">Pokud jsou nutné možnosti specifické pro iPad, je nutné upravit chování iPadu nastavením možností na předem definované bráně refID &quot; iPad, &quot; nikoli vygenerováním nového &quot; ID iPadu &quot; , které odpovídá uživatelskému agentu.</span><span class="sxs-lookup"><span data-stu-id="f9d89-105">If iPad-specific capabilities are required, it is necessary to modify iPad behavior by setting capabilities on the pre-defined gateway refID &quot;IPad&quot; instead of by generating a new &quot;IPad&quot; ID by user agent matching.</span></span>

| <span data-ttu-id="f9d89-106">Name</span><span class="sxs-lookup"><span data-stu-id="f9d89-106">Name</span></span>    | <span data-ttu-id="f9d89-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f9d89-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f9d89-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="f9d89-108">Scope</span></span>   |<span data-ttu-id="f9d89-109">Edge</span><span class="sxs-lookup"><span data-stu-id="f9d89-109">Edge</span></span>|
|<span data-ttu-id="f9d89-110">Verze</span><span class="sxs-lookup"><span data-stu-id="f9d89-110">Version</span></span>|<span data-ttu-id="f9d89-111">4.5</span><span class="sxs-lookup"><span data-stu-id="f9d89-111">4.5</span></span>|
|<span data-ttu-id="f9d89-112">Typ</span><span class="sxs-lookup"><span data-stu-id="f9d89-112">Type</span></span>|<span data-ttu-id="f9d89-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="f9d89-113">Runtime</span></span>|
