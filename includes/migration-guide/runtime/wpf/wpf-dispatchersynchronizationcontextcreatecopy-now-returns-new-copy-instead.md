---
ms.openlocfilehash: fc6066fd0b23d299158114cb397934041b99ba47
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620097"
---
### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a><span data-ttu-id="63ed8-101">WPF DispatcherSynchronizationContext. CreateCopy nyní vrátí novou kopii místo aktuální instance.</span><span class="sxs-lookup"><span data-stu-id="63ed8-101">WPF DispatcherSynchronizationContext.CreateCopy now returns a new copy instead of the current instance</span></span>

#### <a name="details"></a><span data-ttu-id="63ed8-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="63ed8-102">Details</span></span>

<span data-ttu-id="63ed8-103">V .NET Framework 4 <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> vrátil odkaz na aktuální instanci, hlavně jako optimalizaci výkonu.</span><span class="sxs-lookup"><span data-stu-id="63ed8-103">In the .NET Framework 4, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> returned a reference to the current instance, primarily as a performance optimization.</span></span> <span data-ttu-id="63ed8-104">V .NET Framework 4,5 vrátí novou instanci, která umožňuje, aby bylo možné poprvé uzavřít tyto stejné odkazy znamenají, že spuštěné vlákno je ve správném kontextu synchronizace.</span><span class="sxs-lookup"><span data-stu-id="63ed8-104">In the .NET Framework 4.5, it returns a new instance which makes it possible for the first time to conclude that equal references indicate the executing thread is in the correct synchronization context.</span></span>  <span data-ttu-id="63ed8-105">Je pravděpodobné, že kód, který kontroluje identitu těchto odkazů, bude ovlivněn, ale kvůli změně by měl být kód, který volá, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> testován jako součást migrace na .NET Framework 4,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="63ed8-105">It is unlikely that code that checks the identity of these references will be affected, but because of the change, code that calls <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> should be tested as part of migration to the .NET Framework 4.5 or newer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="63ed8-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="63ed8-106">Suggestion</span></span>

<span data-ttu-id="63ed8-107">Počítejte s tím, že <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> nyní vrátí nový <xref:System.Threading.SynchronizationContext?displayProperty=fullName> objekt.</span><span class="sxs-lookup"><span data-stu-id="63ed8-107">Be aware that <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> will now return a new <xref:System.Threading.SynchronizationContext?displayProperty=fullName> object.</span></span> <span data-ttu-id="63ed8-108">Dříve kód, který použil rovnocennost odkazů vygenerovaný tímto způsobem, nebyl ve skutečnosti zkontrolován, zda byl ve správném kontextu, ale v případě, že je sestaven proti .NET Framework 4,5 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="63ed8-108">Previously, code that used equivalence of references generated this way was not actually checking whether it was in the proper context, but does when built against .NET Framework 4.5 or later.</span></span>  <span data-ttu-id="63ed8-109">I když by nedošlo k potížím, by mělo být vhodné, aby při uplatnění ovlivněných cest kódu bylo možné zjistit, zda se jedná o problém.</span><span class="sxs-lookup"><span data-stu-id="63ed8-109">While unlikely to cause issues, exercising the affected code paths should be enough to determine if this poses any problem.</span></span>

| <span data-ttu-id="63ed8-110">Name</span><span class="sxs-lookup"><span data-stu-id="63ed8-110">Name</span></span>    | <span data-ttu-id="63ed8-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="63ed8-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="63ed8-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="63ed8-112">Scope</span></span>   |<span data-ttu-id="63ed8-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="63ed8-113">Minor</span></span>|
|<span data-ttu-id="63ed8-114">Verze</span><span class="sxs-lookup"><span data-stu-id="63ed8-114">Version</span></span>|<span data-ttu-id="63ed8-115">4.5</span><span class="sxs-lookup"><span data-stu-id="63ed8-115">4.5</span></span>|
|<span data-ttu-id="63ed8-116">Typ</span><span class="sxs-lookup"><span data-stu-id="63ed8-116">Type</span></span>|<span data-ttu-id="63ed8-117">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="63ed8-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="63ed8-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="63ed8-118">Affected APIs</span></span>

-<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|
