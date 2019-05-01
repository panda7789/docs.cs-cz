---
ms.openlocfilehash: 4e81087431091dfa4d5432d5ea5e2b665be2b130
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088476"
---
### <a name="listtforeach-can-throw-exception-when-modifying-list-item"></a><span data-ttu-id="3f9a4-101">Seznam\<T >. ForEach může vyvolat výjimku při úpravě položky seznamu</span><span class="sxs-lookup"><span data-stu-id="3f9a4-101">List\<T>.ForEach can throw exception when modifying list item</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3f9a4-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3f9a4-102">Details</span></span>|<span data-ttu-id="3f9a4-103">Počínaje .NET Framework 4.5 <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> čítač vyvolá výjimku <xref:System.InvalidOperationException?displayProperty=name> výjimku, pokud byl prvek v kolekci volání změněn.</span><span class="sxs-lookup"><span data-stu-id="3f9a4-103">Beginning in .NET Framework 4.5, a <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> enumerator will throw an <xref:System.InvalidOperationException?displayProperty=name> exception if an element in the calling collection is modified.</span></span> <span data-ttu-id="3f9a4-104">Dříve to vyvolání výjimky, by ale může vést ke konfliktům časování.</span><span class="sxs-lookup"><span data-stu-id="3f9a4-104">Previously, this would not throw an exception but could lead to race conditions.</span></span>|
|<span data-ttu-id="3f9a4-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="3f9a4-105">Suggestion</span></span>|<span data-ttu-id="3f9a4-106">V ideálním případě by kód stanovit nemohou měnit seznamy při vytváření výčtu jejich elementy, protože to je nikdy bezpečný provoz.</span><span class="sxs-lookup"><span data-stu-id="3f9a4-106">Ideally, code should be fixed to not modify lists while enumerating their elements because that is never a safe operation.</span></span> <span data-ttu-id="3f9a4-107">Chcete-li vrátit k předchozí chování, ale aplikace mohou být zaměřeny na rozhraní .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="3f9a4-107">To revert to the previous behavior, though, an app may target .NET Framework 4.0.</span></span>|
|<span data-ttu-id="3f9a4-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3f9a4-108">Scope</span></span>|<span data-ttu-id="3f9a4-109">Edge</span><span class="sxs-lookup"><span data-stu-id="3f9a4-109">Edge</span></span>|
|<span data-ttu-id="3f9a4-110">Version</span><span class="sxs-lookup"><span data-stu-id="3f9a4-110">Version</span></span>|<span data-ttu-id="3f9a4-111">4.5</span><span class="sxs-lookup"><span data-stu-id="3f9a4-111">4.5</span></span>|
|<span data-ttu-id="3f9a4-112">Type</span><span class="sxs-lookup"><span data-stu-id="3f9a4-112">Type</span></span>|<span data-ttu-id="3f9a4-113">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="3f9a4-113">Retargeting</span></span>|
|<span data-ttu-id="3f9a4-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3f9a4-114">Affected APIs</span></span>|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|
