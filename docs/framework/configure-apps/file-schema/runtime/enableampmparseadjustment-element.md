---
title: Element <EnableAmPmParseAdjustment>
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: 8920e51fcaaca5cb78b80a99ea321163c9b5240f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117372"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="86ae4-102">Element \<EnableAmPmParseAdjustment></span><span class="sxs-lookup"><span data-stu-id="86ae4-102">\<EnableAmPmParseAdjustment> Element</span></span>
<span data-ttu-id="86ae4-103">Určuje, zda metody analýzy data a času používají upravenou sadu pravidel k analýze datových řetězců obsahujících den, měsíc, hodinu a označení dopoledne/odpoledne.</span><span class="sxs-lookup"><span data-stu-id="86ae4-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**  
  
## <a name="syntax"></a><span data-ttu-id="86ae4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86ae4-104">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86ae4-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="86ae4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="86ae4-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="86ae4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86ae4-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="86ae4-107">Attributes</span></span>  
  
|<span data-ttu-id="86ae4-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="86ae4-108">Attribute</span></span>|<span data-ttu-id="86ae4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="86ae4-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="86ae4-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="86ae4-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="86ae4-111">Určuje, zda metody analýzy data a času používají upravenou sadu pravidel k analýze řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.</span><span class="sxs-lookup"><span data-stu-id="86ae4-111">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="86ae4-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="86ae4-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="86ae4-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="86ae4-113">Value</span></span>|<span data-ttu-id="86ae4-114">Description</span><span class="sxs-lookup"><span data-stu-id="86ae4-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="86ae4-115">0</span><span class="sxs-lookup"><span data-stu-id="86ae4-115">0</span></span>|<span data-ttu-id="86ae4-116">Metody analýzy data a času nepoužívají upravená pravidla pro analýzu řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.</span><span class="sxs-lookup"><span data-stu-id="86ae4-116">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="86ae4-117">1</span><span class="sxs-lookup"><span data-stu-id="86ae4-117">1</span></span>|<span data-ttu-id="86ae4-118">Metody analýzy data a času používají upravená pravidla pro analýzu řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.</span><span class="sxs-lookup"><span data-stu-id="86ae4-118">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86ae4-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="86ae4-119">Child Elements</span></span>  
 <span data-ttu-id="86ae4-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="86ae4-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86ae4-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="86ae4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="86ae4-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="86ae4-122">Element</span></span>|<span data-ttu-id="86ae4-123">Description</span><span class="sxs-lookup"><span data-stu-id="86ae4-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="86ae4-124">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86ae4-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="86ae4-125">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="86ae4-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86ae4-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86ae4-126">Remarks</span></span>  
 <span data-ttu-id="86ae4-127">`<EnableAmPmParseAdjustment>`Prvek řídí způsob, jakým následující metody analyzují řetězec data obsahující číselný den a měsíc následovaný hodinu a označení dopoledne/odpoledne (například "4/10 6 dop."):</span><span class="sxs-lookup"><span data-stu-id="86ae4-127">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="86ae4-128">Žádné další vzory nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="86ae4-128">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="86ae4-129">`<EnableAmPmParseAdjustment>`Element nemá žádný vliv na <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> metody,, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="86ae4-129">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="86ae4-130">V rozhraní .NET Core a .NET Native jsou ve výchozím nastavení povolená upravená pravidla analýzy dopoledne/odpoledne.</span><span class="sxs-lookup"><span data-stu-id="86ae4-130">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="86ae4-131">Pokud není pravidlo úpravy analýzy povoleno, první číslice řetězce je interpretována jako hodina 12 hodinového času a zbytek řetězce s výjimkou označení dopoledne/odpoledne je ignorován.</span><span class="sxs-lookup"><span data-stu-id="86ae4-131">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="86ae4-132">Datum a čas vracené metodou analýzy se skládají z aktuálního data a hodiny dne extrahované z řetězce data.</span><span class="sxs-lookup"><span data-stu-id="86ae4-132">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="86ae4-133">Pokud je pravidlo úpravy analýzy povoleno, metoda analýzy interpretuje den a měsíc jako patřící do aktuálního roku a interpretuje čas jako hodinu z 12 hodin.</span><span class="sxs-lookup"><span data-stu-id="86ae4-133">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="86ae4-134">Následující tabulka ukazuje rozdíl v <xref:System.DateTime> hodnotě při <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> použití metody k analýze řetězce "" 4/10 6 AM "s `<EnableAmPmParseAdjustment>` `enabled` vlastností elementu nastavenou na hodnotu" 0 "nebo" 1 ".</span><span class="sxs-lookup"><span data-stu-id="86ae4-134">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="86ae4-135">Předpokládá, že dnešní datum je 5. ledna 2017 a zobrazuje datum, jako by bylo formátováno pomocí formátovacího řetězce "G" zadané jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="86ae4-135">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="86ae4-136">Název jazykové verze</span><span class="sxs-lookup"><span data-stu-id="86ae4-136">Culture name</span></span>|<span data-ttu-id="86ae4-137">Enabled = "0"</span><span class="sxs-lookup"><span data-stu-id="86ae4-137">enabled="0"</span></span>|<span data-ttu-id="86ae4-138">Enabled = "1"</span><span class="sxs-lookup"><span data-stu-id="86ae4-138">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="86ae4-139">cs-CZ</span><span class="sxs-lookup"><span data-stu-id="86ae4-139">en-US</span></span>|<span data-ttu-id="86ae4-140">1/5/2017 4:00:00 DOP.</span><span class="sxs-lookup"><span data-stu-id="86ae4-140">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="86ae4-141">4/10/2017 6:00:00 DOP.</span><span class="sxs-lookup"><span data-stu-id="86ae4-141">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="86ae4-142">en-GB</span><span class="sxs-lookup"><span data-stu-id="86ae4-142">en-GB</span></span>|<span data-ttu-id="86ae4-143">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="86ae4-143">5/1/2017 6:00:00</span></span>|<span data-ttu-id="86ae4-144">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="86ae4-144">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86ae4-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="86ae4-145">See also</span></span>

- [<span data-ttu-id="86ae4-146">\<runtime>Objekt</span><span class="sxs-lookup"><span data-stu-id="86ae4-146">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="86ae4-147">\<configuration>Objekt</span><span class="sxs-lookup"><span data-stu-id="86ae4-147">\<configuration> Element</span></span>](../configuration-element.md)
