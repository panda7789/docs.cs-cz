---
title: Element <EnableAmPmParseAdjustment>
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: 8920e51fcaaca5cb78b80a99ea321163c9b5240f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117372"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="655be-102">\<element > EnableAmPmParseAdjustment</span><span class="sxs-lookup"><span data-stu-id="655be-102">\<EnableAmPmParseAdjustment> Element</span></span>
<span data-ttu-id="655be-103">Určuje, zda metody analýzy data a času používají upravenou sadu pravidel k analýze datových řetězců obsahujících den, měsíc, hodinu a označení dopoledne/odpoledne.</span><span class="sxs-lookup"><span data-stu-id="655be-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
<span data-ttu-id="655be-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="655be-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="655be-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="655be-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="655be-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<EnableAmPmParseAdjustment >**</span><span class="sxs-lookup"><span data-stu-id="655be-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="655be-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="655be-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="655be-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="655be-108">Attributes and Elements</span></span>  
 <span data-ttu-id="655be-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="655be-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="655be-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="655be-110">Attributes</span></span>  
  
|<span data-ttu-id="655be-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="655be-111">Attribute</span></span>|<span data-ttu-id="655be-112">Popis</span><span class="sxs-lookup"><span data-stu-id="655be-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="655be-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="655be-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="655be-114">Určuje, zda metody analýzy data a času používají upravenou sadu pravidel k analýze řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.</span><span class="sxs-lookup"><span data-stu-id="655be-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="655be-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="655be-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="655be-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="655be-116">Value</span></span>|<span data-ttu-id="655be-117">Popis</span><span class="sxs-lookup"><span data-stu-id="655be-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="655be-118">0,8</span><span class="sxs-lookup"><span data-stu-id="655be-118">0</span></span>|<span data-ttu-id="655be-119">Metody analýzy data a času nepoužívají upravená pravidla pro analýzu řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.</span><span class="sxs-lookup"><span data-stu-id="655be-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="655be-120">první</span><span class="sxs-lookup"><span data-stu-id="655be-120">1</span></span>|<span data-ttu-id="655be-121">Metody analýzy data a času používají upravená pravidla pro analýzu řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.</span><span class="sxs-lookup"><span data-stu-id="655be-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="655be-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="655be-122">Child Elements</span></span>  
 <span data-ttu-id="655be-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="655be-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="655be-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="655be-124">Parent Elements</span></span>  
  
|<span data-ttu-id="655be-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="655be-125">Element</span></span>|<span data-ttu-id="655be-126">Popis</span><span class="sxs-lookup"><span data-stu-id="655be-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="655be-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="655be-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="655be-128">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="655be-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="655be-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="655be-129">Remarks</span></span>  
 <span data-ttu-id="655be-130">Element `<EnableAmPmParseAdjustment>` řídí, jak následující metody analyzují řetězec data obsahující číselný den a měsíc následovaný hodinou a označení AM/PM (například "4/10 6 dop."):</span><span class="sxs-lookup"><span data-stu-id="655be-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="655be-131">Žádné další vzory nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="655be-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="655be-132">`<EnableAmPmParseAdjustment>` element nemá žádný vliv na metody <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>a <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="655be-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="655be-133">V rozhraní .NET Core a .NET Native jsou ve výchozím nastavení povolená upravená pravidla analýzy dopoledne/odpoledne.</span><span class="sxs-lookup"><span data-stu-id="655be-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="655be-134">Pokud není pravidlo úpravy analýzy povoleno, první číslice řetězce je interpretována jako hodina 12 hodinového času a zbytek řetězce s výjimkou označení dopoledne/odpoledne je ignorován.</span><span class="sxs-lookup"><span data-stu-id="655be-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="655be-135">Datum a čas vracené metodou analýzy se skládají z aktuálního data a hodiny dne extrahované z řetězce data.</span><span class="sxs-lookup"><span data-stu-id="655be-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="655be-136">Pokud je pravidlo úpravy analýzy povoleno, metoda analýzy interpretuje den a měsíc jako patřící do aktuálního roku a interpretuje čas jako hodinu z 12 hodin.</span><span class="sxs-lookup"><span data-stu-id="655be-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="655be-137">Následující tabulka ilustruje rozdíl v hodnotě <xref:System.DateTime>, pokud je metoda <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> použita k analýze řetězce "" 4/10 6 AM "s vlastností `enabled` elementu `<EnableAmPmParseAdjustment>` nastaveným na hodnotu" 0 "nebo" 1 ".</span><span class="sxs-lookup"><span data-stu-id="655be-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="655be-138">Předpokládá, že dnešní datum je 5. ledna 2017 a zobrazuje datum, jako by bylo formátováno pomocí formátovacího řetězce "G" zadané jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="655be-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="655be-139">Název jazykové verze</span><span class="sxs-lookup"><span data-stu-id="655be-139">Culture name</span></span>|<span data-ttu-id="655be-140">Enabled = "0"</span><span class="sxs-lookup"><span data-stu-id="655be-140">enabled="0"</span></span>|<span data-ttu-id="655be-141">Enabled = "1"</span><span class="sxs-lookup"><span data-stu-id="655be-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="655be-142">EN-US</span><span class="sxs-lookup"><span data-stu-id="655be-142">en-US</span></span>|<span data-ttu-id="655be-143">1/5/2017 4:00:00 DOP.</span><span class="sxs-lookup"><span data-stu-id="655be-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="655be-144">4/10/2017 6:00:00 DOP.</span><span class="sxs-lookup"><span data-stu-id="655be-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="655be-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="655be-145">en-GB</span></span>|<span data-ttu-id="655be-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="655be-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="655be-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="655be-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="655be-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="655be-148">See also</span></span>

- [<span data-ttu-id="655be-149">\<element > runtime</span><span class="sxs-lookup"><span data-stu-id="655be-149">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="655be-150">> element konfigurace \<</span><span class="sxs-lookup"><span data-stu-id="655be-150">\<configuration> Element</span></span>](../configuration-element.md)
