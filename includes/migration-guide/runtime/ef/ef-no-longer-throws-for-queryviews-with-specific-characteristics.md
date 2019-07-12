---
ms.openlocfilehash: bc33266bb2af639d7d0d1cb532ed73abd7f1ba9a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803252"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a><span data-ttu-id="1d8ca-101">EF již nevyvolá pro QueryViews s konkrétními vlastnostmi</span><span class="sxs-lookup"><span data-stu-id="1d8ca-101">EF no longer throws for QueryViews with specific characteristics</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1d8ca-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1d8ca-102">Details</span></span>|<span data-ttu-id="1d8ca-103">Entity Framework již nevyvolá <xref:System.StackOverflowException?displayProperty=name> výjimka při aplikace provede dotaz, který zahrnuje zobrazení QueryView s 0..1 navigační vlastnost, která se pokusí přidat související entity jako součást dotazu.</span><span class="sxs-lookup"><span data-stu-id="1d8ca-103">Entity Framework no longer throws a <xref:System.StackOverflowException?displayProperty=name> exception when an app executes a query that involves a QueryView with a 0..1 navigation property that attempts to include the related entities as part of the query.</span></span> <span data-ttu-id="1d8ca-104">Například voláním <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span><span class="sxs-lookup"><span data-stu-id="1d8ca-104">For example, by calling <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span></span>|
|<span data-ttu-id="1d8ca-105">Doporučení</span><span class="sxs-lookup"><span data-stu-id="1d8ca-105">Suggestion</span></span>|<span data-ttu-id="1d8ca-106">Tato změna ovlivní pouze kód, který používá QueryViews s 1-0..1 relací při spuštění dotazů toto volání. Zahrnout.</span><span class="sxs-lookup"><span data-stu-id="1d8ca-106">This change only affects code that uses QueryViews with 1-0..1 relationships when running queries that call .Include.</span></span> <span data-ttu-id="1d8ca-107">Zvyšuje spolehlivost a musejí být transparentní pro téměř všechny aplikace.</span><span class="sxs-lookup"><span data-stu-id="1d8ca-107">It improves reliability and should be transparent to almost all apps.</span></span> <span data-ttu-id="1d8ca-108">Ale pokud dojde k neočekávanému chování, můžete zakázat ho tak, že přidáte následující položky <code>&lt;appSettings&gt;</code> oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="1d8ca-108">However, if it causes unexpected behavior, you can disable it by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the app's configuration file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="1d8ca-109">Scope</span><span class="sxs-lookup"><span data-stu-id="1d8ca-109">Scope</span></span>|<span data-ttu-id="1d8ca-110">Edge</span><span class="sxs-lookup"><span data-stu-id="1d8ca-110">Edge</span></span>|
|<span data-ttu-id="1d8ca-111">Version</span><span class="sxs-lookup"><span data-stu-id="1d8ca-111">Version</span></span>|<span data-ttu-id="1d8ca-112">4.5.2</span><span class="sxs-lookup"><span data-stu-id="1d8ca-112">4.5.2</span></span>|
|<span data-ttu-id="1d8ca-113">type</span><span class="sxs-lookup"><span data-stu-id="1d8ca-113">Type</span></span>|<span data-ttu-id="1d8ca-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="1d8ca-114">Runtime</span></span>|

