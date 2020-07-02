---
ms.openlocfilehash: e4d9efe7d2a06a1e501b070c23184dcd913dba71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621121"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a><span data-ttu-id="bba96-101">Perské kalendář teď používá algoritmus hidžra. inflace.</span><span class="sxs-lookup"><span data-stu-id="bba96-101">Persian calendar now uses the Hijri solar algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="bba96-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="bba96-102">Details</span></span>

<span data-ttu-id="bba96-103">Počínaje .NET Framework 4,6 <xref:System.Globalization.PersianCalendar?displayProperty=fullName> Třída používá algoritmus hidžra.</span><span class="sxs-lookup"><span data-stu-id="bba96-103">Starting with the .NET Framework 4.6, the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> class uses the Hijri solar algorithm.</span></span> <span data-ttu-id="bba96-104">Převod dat mezi daty <xref:System.Globalization.PersianCalendar?displayProperty=fullName> a dalšími kalendáři může způsobit trochu odlišný výsledek začínající .NET Framework 4,6 pro data starší než 1800 nebo novější než 2023 (gregoriánský). Také <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> je nyní <code>March 22, 0622</code> místo <code>March 21, 0622</code> .</span><span class="sxs-lookup"><span data-stu-id="bba96-104">Converting dates between the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> and other calendars may produce a slightly different result beginning with the .NET Framework 4.6 for dates earlier than 1800 or later than 2023 (Gregorian).Also, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> is now <code>March 22, 0622</code> instead of <code>March 21, 0622</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bba96-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="bba96-105">Suggestion</span></span>

<span data-ttu-id="bba96-106">Počítejte s tím, že některá počáteční nebo pozdě data mohou být mírně odlišná při použití PersianCalendar v .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="bba96-106">Be aware that some early or late dates may be slightly different when using the PersianCalendar in .NET Framework 4.6.</span></span> <span data-ttu-id="bba96-107">Při serializaci dat mezi procesy, které mohou běžet na různých verzích .NET Framework, je také neukládejte jako řetězce PersianCalendar data (protože se tyto hodnoty mohou lišit).</span><span class="sxs-lookup"><span data-stu-id="bba96-107">Also, when serializing dates between processes which may run on different .NET Framework versions, do not store them as PersianCalendar date strings (since those values may be different).</span></span>

| <span data-ttu-id="bba96-108">Name</span><span class="sxs-lookup"><span data-stu-id="bba96-108">Name</span></span>    | <span data-ttu-id="bba96-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bba96-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bba96-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="bba96-110">Scope</span></span>   |<span data-ttu-id="bba96-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="bba96-111">Minor</span></span>|
|<span data-ttu-id="bba96-112">Verze</span><span class="sxs-lookup"><span data-stu-id="bba96-112">Version</span></span>|<span data-ttu-id="bba96-113">4.6</span><span class="sxs-lookup"><span data-stu-id="bba96-113">4.6</span></span>|
|<span data-ttu-id="bba96-114">Typ</span><span class="sxs-lookup"><span data-stu-id="bba96-114">Type</span></span>|<span data-ttu-id="bba96-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="bba96-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bba96-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bba96-116">Affected APIs</span></span>

-<xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
