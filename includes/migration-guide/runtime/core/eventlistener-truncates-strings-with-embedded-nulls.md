---
ms.openlocfilehash: 6f5c1ecead4e2f74e621354058aab70bfa1cccb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619966"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a><span data-ttu-id="02160-101">Naslouchacího procesu událostí zkrátí řetězce o vložené hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="02160-101">EventListener truncates strings with embedded nulls</span></span>

#### <a name="details"></a><span data-ttu-id="02160-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="02160-102">Details</span></span>

<span data-ttu-id="02160-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName>zkrátí řetězce na vložené hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="02160-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> truncates strings with embedded nulls.</span></span> <span data-ttu-id="02160-104">Třída nepodporuje znaky null <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="02160-104">Null characters are not supported by the <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> class.</span></span> <span data-ttu-id="02160-105">Tato změna ovlivní pouze aplikace, které používají <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> ke čtení <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> dat v procesu a které používají jako oddělovače znaky null.</span><span class="sxs-lookup"><span data-stu-id="02160-105">The change only affects apps that use <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> to read <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process and that use null characters as delimiters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="02160-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="02160-106">Suggestion</span></span>

<span data-ttu-id="02160-107"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>data by se měla aktualizovat, pokud je to možné, aby se vložené znaky null nepoužívaly.</span><span class="sxs-lookup"><span data-stu-id="02160-107"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data should be updated, if possible, to not use embedded null characters.</span></span>

| <span data-ttu-id="02160-108">Name</span><span class="sxs-lookup"><span data-stu-id="02160-108">Name</span></span>    | <span data-ttu-id="02160-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="02160-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="02160-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="02160-110">Scope</span></span>   |<span data-ttu-id="02160-111">Edge</span><span class="sxs-lookup"><span data-stu-id="02160-111">Edge</span></span>|
|<span data-ttu-id="02160-112">Verze</span><span class="sxs-lookup"><span data-stu-id="02160-112">Version</span></span>|<span data-ttu-id="02160-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="02160-113">4.5.1</span></span>|
|<span data-ttu-id="02160-114">Typ</span><span class="sxs-lookup"><span data-stu-id="02160-114">Type</span></span>|<span data-ttu-id="02160-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="02160-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="02160-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="02160-116">Affected APIs</span></span>

-<xref:System.Diagnostics.Tracing.EventListener.%23ctor></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|
