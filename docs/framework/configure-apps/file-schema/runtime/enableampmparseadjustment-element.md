---
title: Element <EnableAmPmParseAdjustment>
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46cf37ee800c05eb7fe12e8491ad3b2130c3a04d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920812"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="9c806-102">\<EnableAmPmParseAdjustment – element ></span><span class="sxs-lookup"><span data-stu-id="9c806-102">\<EnableAmPmParseAdjustment> Element</span></span>
<span data-ttu-id="9c806-103">Určuje, zda metody analýzy data a času používají upravenou sadu pravidel k analýze datových řetězců obsahujících den, měsíc, hodinu a označení dopoledne/odpoledne.</span><span class="sxs-lookup"><span data-stu-id="9c806-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
 <span data-ttu-id="9c806-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9c806-104">\<configuration></span></span>  
 <span data-ttu-id="9c806-105">\<> modulu runtime</span><span class="sxs-lookup"><span data-stu-id="9c806-105">\<runtime></span></span>  
<span data-ttu-id="9c806-106">\<EnableAmPmParseAdjustment ></span><span class="sxs-lookup"><span data-stu-id="9c806-106">\<EnableAmPmParseAdjustment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c806-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c806-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c806-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9c806-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9c806-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9c806-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c806-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="9c806-110">Attributes</span></span>  
  
|<span data-ttu-id="9c806-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="9c806-111">Attribute</span></span>|<span data-ttu-id="9c806-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9c806-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9c806-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="9c806-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="9c806-114">Určuje, zda metody analýzy data a času používají upravenou sadu pravidel k analýze řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.</span><span class="sxs-lookup"><span data-stu-id="9c806-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="9c806-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="9c806-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="9c806-116">Value</span><span class="sxs-lookup"><span data-stu-id="9c806-116">Value</span></span>|<span data-ttu-id="9c806-117">Popis</span><span class="sxs-lookup"><span data-stu-id="9c806-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9c806-118">0</span><span class="sxs-lookup"><span data-stu-id="9c806-118">0</span></span>|<span data-ttu-id="9c806-119">Metody analýzy data a času nepoužívají upravená pravidla pro analýzu řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.</span><span class="sxs-lookup"><span data-stu-id="9c806-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="9c806-120">1</span><span class="sxs-lookup"><span data-stu-id="9c806-120">1</span></span>|<span data-ttu-id="9c806-121">Metody analýzy data a času používají upravená pravidla pro analýzu řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.</span><span class="sxs-lookup"><span data-stu-id="9c806-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c806-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9c806-122">Child Elements</span></span>  
 <span data-ttu-id="9c806-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="9c806-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c806-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9c806-124">Parent Elements</span></span>  
  
|<span data-ttu-id="9c806-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="9c806-125">Element</span></span>|<span data-ttu-id="9c806-126">Popis</span><span class="sxs-lookup"><span data-stu-id="9c806-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9c806-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c806-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9c806-128">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="9c806-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c806-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9c806-129">Remarks</span></span>  
 <span data-ttu-id="9c806-130">`<EnableAmPmParseAdjustment>` Prvek řídí způsob, jakým následující metody analyzují řetězec data obsahující číselný den a měsíc následovaný hodinu a označení dopoledne/odpoledne (například "4/10 6 dop."):</span><span class="sxs-lookup"><span data-stu-id="9c806-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="9c806-131">Žádné další vzory nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="9c806-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="9c806-132"><xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> Element nemá žádný vliv <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>na metody,, a. `<EnableAmPmParseAdjustment>`</span><span class="sxs-lookup"><span data-stu-id="9c806-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9c806-133">V rozhraní .NET Core a .NET Native jsou ve výchozím nastavení povolená upravená pravidla analýzy dopoledne/odpoledne.</span><span class="sxs-lookup"><span data-stu-id="9c806-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="9c806-134">Pokud není pravidlo úpravy analýzy povoleno, první číslice řetězce je interpretována jako hodina 12 hodinového času a zbytek řetězce s výjimkou označení dopoledne/odpoledne je ignorován.</span><span class="sxs-lookup"><span data-stu-id="9c806-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="9c806-135">Datum a čas vracené metodou analýzy se skládají z aktuálního data a hodiny dne extrahované z řetězce data.</span><span class="sxs-lookup"><span data-stu-id="9c806-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="9c806-136">Pokud je pravidlo úpravy analýzy povoleno, metoda analýzy interpretuje den a měsíc jako patřící do aktuálního roku a interpretuje čas jako hodinu z 12 hodin.</span><span class="sxs-lookup"><span data-stu-id="9c806-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="9c806-137">Následující tabulka ukazuje rozdíl <xref:System.DateTime> v hodnotě <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> při použití metody k analýze řetězce "" `<EnableAmPmParseAdjustment>` 4/10 6 am `enabled` "s vlastností elementu nastavenou na hodnotu" 0 "nebo" 1 ".</span><span class="sxs-lookup"><span data-stu-id="9c806-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="9c806-138">Předpokládá, že dnešní datum je 5. ledna 2017 a zobrazuje datum, jako by bylo formátováno pomocí formátovacího řetězce "G" zadané jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="9c806-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="9c806-139">Název jazykové verze</span><span class="sxs-lookup"><span data-stu-id="9c806-139">Culture name</span></span>|<span data-ttu-id="9c806-140">enabled="0"</span><span class="sxs-lookup"><span data-stu-id="9c806-140">enabled="0"</span></span>|<span data-ttu-id="9c806-141">enabled="1"</span><span class="sxs-lookup"><span data-stu-id="9c806-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="9c806-142">en-US</span><span class="sxs-lookup"><span data-stu-id="9c806-142">en-US</span></span>|<span data-ttu-id="9c806-143">1/5/2017 4:00:00 DOP.</span><span class="sxs-lookup"><span data-stu-id="9c806-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="9c806-144">4/10/2017 6:00:00 DOP.</span><span class="sxs-lookup"><span data-stu-id="9c806-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="9c806-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="9c806-145">en-GB</span></span>|<span data-ttu-id="9c806-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="9c806-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="9c806-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="9c806-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c806-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c806-148">See also</span></span>

- [<span data-ttu-id="9c806-149">\<Běhový > element</span><span class="sxs-lookup"><span data-stu-id="9c806-149">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="9c806-150">\<Element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9c806-150">\<configuration> Element</span></span>](../configuration-element.md)
