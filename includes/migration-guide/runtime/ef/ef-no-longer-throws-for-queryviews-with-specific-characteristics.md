---
ms.openlocfilehash: c6c897c13c84ce4b2be21da18e5702365518f286
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620026"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a><span data-ttu-id="3345f-101">EF již nevyvolává pro QueryViews s konkrétními charakteristikami</span><span class="sxs-lookup"><span data-stu-id="3345f-101">EF no longer throws for QueryViews with specific characteristics</span></span>

#### <a name="details"></a><span data-ttu-id="3345f-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3345f-102">Details</span></span>

<span data-ttu-id="3345f-103">Entity Framework už nevyvolává <xref:System.StackOverflowException?displayProperty=fullName> výjimku, když aplikace spustí dotaz, který zahrnuje QueryView s vlastností navigace 0.. 1, která se pokusí zahrnout související entity jako součást dotazu.</span><span class="sxs-lookup"><span data-stu-id="3345f-103">Entity Framework no longer throws a <xref:System.StackOverflowException?displayProperty=fullName> exception when an app executes a query that involves a QueryView with a 0..1 navigation property that attempts to include the related entities as part of the query.</span></span> <span data-ttu-id="3345f-104">Například voláním metody <code>.Include(e =&gt; e.RelatedNavProp)</code> .</span><span class="sxs-lookup"><span data-stu-id="3345f-104">For example, by calling <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3345f-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="3345f-105">Suggestion</span></span>

<span data-ttu-id="3345f-106">Tato změna má vliv pouze na kód, který používá QueryViews s 1 – 0.. 1 relacemi při spouštění dotazů, které volají. Připojit.</span><span class="sxs-lookup"><span data-stu-id="3345f-106">This change only affects code that uses QueryViews with 1-0..1 relationships when running queries that call .Include.</span></span> <span data-ttu-id="3345f-107">Zlepšuje spolehlivost a měla by být transparentní pro téměř všechny aplikace.</span><span class="sxs-lookup"><span data-stu-id="3345f-107">It improves reliability and should be transparent to almost all apps.</span></span> <span data-ttu-id="3345f-108">Pokud ale dojde k neočekávanému chování, můžete ho zakázat přidáním následujícího záznamu do <code>&lt;appSettings&gt;</code> části konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="3345f-108">However, if it causes unexpected behavior, you can disable it by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the app's configuration file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="3345f-109">Name</span><span class="sxs-lookup"><span data-stu-id="3345f-109">Name</span></span>    | <span data-ttu-id="3345f-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3345f-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3345f-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="3345f-111">Scope</span></span>   |<span data-ttu-id="3345f-112">Edge</span><span class="sxs-lookup"><span data-stu-id="3345f-112">Edge</span></span>|
|<span data-ttu-id="3345f-113">Verze</span><span class="sxs-lookup"><span data-stu-id="3345f-113">Version</span></span>|<span data-ttu-id="3345f-114">4.5.2</span><span class="sxs-lookup"><span data-stu-id="3345f-114">4.5.2</span></span>|
|<span data-ttu-id="3345f-115">Typ</span><span class="sxs-lookup"><span data-stu-id="3345f-115">Type</span></span>|<span data-ttu-id="3345f-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="3345f-116">Runtime</span></span>|
