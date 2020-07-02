---
ms.openlocfilehash: 6af8e97423c04abca25feb8d77ea9ab6e198a4f0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620029"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a><span data-ttu-id="ff6ac-101">ObjectContext. repřeklady a ObjectContext.ExecuteStoreQuery nyní podporují typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="ff6ac-101">ObjectContext.Translate and ObjectContext.ExecuteStoreQuery now support enum type</span></span>

#### <a name="details"></a><span data-ttu-id="ff6ac-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ff6ac-102">Details</span></span>

<span data-ttu-id="ff6ac-103">V .NET Framework 4,0 obecný parametr <code>T</code> <code>ObjectContext.Translate</code> a <code>ObjectContext.ExecuteStoreQuery</code> metod nemůže být výčet.</span><span class="sxs-lookup"><span data-stu-id="ff6ac-103">In .NET Framework 4.0, the generic parameter <code>T</code> of <code>ObjectContext.Translate</code> and <code>ObjectContext.ExecuteStoreQuery</code> methods could not be an enum.</span></span> <span data-ttu-id="ff6ac-104">Tento scénář se teď podporuje.</span><span class="sxs-lookup"><span data-stu-id="ff6ac-104">That scenario is now supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ff6ac-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="ff6ac-105">Suggestion</span></span>

<span data-ttu-id="ff6ac-106">Pokud byla metoda přeložit nebo ExecuteStoreQuery volána pro typ výčtu v .NET Framework 4,0, byla vrácena hodnota 0.</span><span class="sxs-lookup"><span data-stu-id="ff6ac-106">If Translate or ExecuteStoreQuery was called on an enum type in .NET Framework 4.0, '0' was returned.</span></span> <span data-ttu-id="ff6ac-107">V případě, že toto chování bylo žádoucí, volání by měla být nahrazena konstantou 0 (nebo ekvivalentem výčtu).</span><span class="sxs-lookup"><span data-stu-id="ff6ac-107">If that behavior was desirable, the calls should be replaced with a constant 0 (or the enum equivalent of it).</span></span>

| <span data-ttu-id="ff6ac-108">Name</span><span class="sxs-lookup"><span data-stu-id="ff6ac-108">Name</span></span>    | <span data-ttu-id="ff6ac-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ff6ac-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ff6ac-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="ff6ac-110">Scope</span></span>   |<span data-ttu-id="ff6ac-111">Edge</span><span class="sxs-lookup"><span data-stu-id="ff6ac-111">Edge</span></span>|
|<span data-ttu-id="ff6ac-112">Verze</span><span class="sxs-lookup"><span data-stu-id="ff6ac-112">Version</span></span>|<span data-ttu-id="ff6ac-113">4.5</span><span class="sxs-lookup"><span data-stu-id="ff6ac-113">4.5</span></span>|
|<span data-ttu-id="ff6ac-114">Typ</span><span class="sxs-lookup"><span data-stu-id="ff6ac-114">Type</span></span>|<span data-ttu-id="ff6ac-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="ff6ac-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ff6ac-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ff6ac-116">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
