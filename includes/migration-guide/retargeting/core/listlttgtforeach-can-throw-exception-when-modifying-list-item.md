---
ms.openlocfilehash: 4e81087431091dfa4d5432d5ea5e2b665be2b130
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234660"
---
### <a name="listtforeach-can-throw-exception-when-modifying-list-item"></a><span data-ttu-id="ed540-101">Seznam\<T >. ForEach může vyvolat výjimku při úpravě položky seznamu</span><span class="sxs-lookup"><span data-stu-id="ed540-101">List\<T>.ForEach can throw exception when modifying list item</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ed540-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ed540-102">Details</span></span>|<span data-ttu-id="ed540-103">Počínaje .NET Framework 4.5 <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> čítač vyvolá výjimku <xref:System.InvalidOperationException?displayProperty=name> výjimku, pokud byl prvek v kolekci volání změněn.</span><span class="sxs-lookup"><span data-stu-id="ed540-103">Beginning in .NET Framework 4.5, a <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerator will throw an <xref:System.InvalidOperationException?displayProperty=name> exception if an element in the calling collection is modified.</span></span> <span data-ttu-id="ed540-104">Dříve to vyvolání výjimky, by ale může vést ke konfliktům časování.</span><span class="sxs-lookup"><span data-stu-id="ed540-104">Previously, this would not throw an exception but could lead to race conditions.</span></span>|
|<span data-ttu-id="ed540-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="ed540-105">Suggestion</span></span>|<span data-ttu-id="ed540-106">V ideálním případě by kód stanovit nemohou měnit seznamy při vytváření výčtu jejich elementy, protože to je nikdy bezpečný provoz.</span><span class="sxs-lookup"><span data-stu-id="ed540-106">Ideally, code should be fixed to not modify lists while enumerating their elements because that is never a safe operation.</span></span> <span data-ttu-id="ed540-107">Chcete-li vrátit k předchozí chování, ale aplikace mohou být zaměřeny na rozhraní .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="ed540-107">To revert to the previous behavior, though, an app may target .NET Framework 4.0.</span></span>|
|<span data-ttu-id="ed540-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="ed540-108">Scope</span></span>|<span data-ttu-id="ed540-109">Edge</span><span class="sxs-lookup"><span data-stu-id="ed540-109">Edge</span></span>|
|<span data-ttu-id="ed540-110">Version</span><span class="sxs-lookup"><span data-stu-id="ed540-110">Version</span></span>|<span data-ttu-id="ed540-111">4.5</span><span class="sxs-lookup"><span data-stu-id="ed540-111">4.5</span></span>|
|<span data-ttu-id="ed540-112">Type</span><span class="sxs-lookup"><span data-stu-id="ed540-112">Type</span></span>|<span data-ttu-id="ed540-113">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="ed540-113">Retargeting</span></span>|
|<span data-ttu-id="ed540-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ed540-114">Affected APIs</span></span>|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|
