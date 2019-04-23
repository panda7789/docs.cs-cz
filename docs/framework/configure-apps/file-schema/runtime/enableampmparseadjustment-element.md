---
title: Element <EnableAmPmParseAdjustment>
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57d1a14199debbb90827c1ea95347d485a636329
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222507"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="c32ce-102">\<EnableAmPmParseAdjustment > – Element</span><span class="sxs-lookup"><span data-stu-id="c32ce-102">\<EnableAmPmParseAdjustment> Element</span></span>
<span data-ttu-id="c32ce-103">Určuje, zda analýzy metody data a času použít upravenou sadu pravidel k parsování řetězců kalendářních dat, které obsahují den, měsíc, hodinu a označení dopoledne/odpoledne.</span><span class="sxs-lookup"><span data-stu-id="c32ce-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
 <span data-ttu-id="c32ce-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="c32ce-104">\<configuration></span></span>  
 <span data-ttu-id="c32ce-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="c32ce-105">\<runtime></span></span>  
<span data-ttu-id="c32ce-106">\<EnableAmPmParseAdjustment ></span><span class="sxs-lookup"><span data-stu-id="c32ce-106">\<EnableAmPmParseAdjustment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c32ce-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c32ce-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c32ce-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c32ce-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c32ce-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c32ce-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c32ce-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c32ce-110">Attributes</span></span>  
  
|<span data-ttu-id="c32ce-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="c32ce-111">Attribute</span></span>|<span data-ttu-id="c32ce-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c32ce-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c32ce-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c32ce-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c32ce-114">Určuje, jestli analýzy metody data a času použít upravenou sadu pravidel k parsování řetězců kalendářních dat, které obsahují pouze den, měsíc, hodinu a označení dopoledne/odpoledne.</span><span class="sxs-lookup"><span data-stu-id="c32ce-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="c32ce-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="c32ce-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="c32ce-116">Value</span><span class="sxs-lookup"><span data-stu-id="c32ce-116">Value</span></span>|<span data-ttu-id="c32ce-117">Popis</span><span class="sxs-lookup"><span data-stu-id="c32ce-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c32ce-118">0</span><span class="sxs-lookup"><span data-stu-id="c32ce-118">0</span></span>|<span data-ttu-id="c32ce-119">Datum a čas analýze metody nepoužívejte upravené pravidla pro parsování řetězců kalendářních dat, které obsahují pouze den, měsíc, hodinu a označení dopoledne/odpoledne.</span><span class="sxs-lookup"><span data-stu-id="c32ce-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="c32ce-120">1</span><span class="sxs-lookup"><span data-stu-id="c32ce-120">1</span></span>|<span data-ttu-id="c32ce-121">Analýzy metody data a času pomocí upravené pravidel pro parsování řetězců kalendářních dat, které obsahují pouze den, měsíc, hodinu a označení dopoledne/odpoledne.</span><span class="sxs-lookup"><span data-stu-id="c32ce-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c32ce-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c32ce-122">Child Elements</span></span>  
 <span data-ttu-id="c32ce-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="c32ce-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c32ce-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c32ce-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c32ce-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="c32ce-125">Element</span></span>|<span data-ttu-id="c32ce-126">Popis</span><span class="sxs-lookup"><span data-stu-id="c32ce-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c32ce-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c32ce-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c32ce-128">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c32ce-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c32ce-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c32ce-129">Remarks</span></span>  
 <span data-ttu-id="c32ce-130">`<EnableAmPmParseAdjustment>` Prvek určuje, jak analyzovat řetězec data, který obsahuje číselné vyjádření dne a měsíce, za nímž následuje za hodinu a dopoledne/odpoledne (například "4/10 6 AM") v následujících metod:</span><span class="sxs-lookup"><span data-stu-id="c32ce-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="c32ce-131">Žádné jiné vzory jsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="c32ce-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="c32ce-132">`<EnableAmPmParseAdjustment>` Element nemá žádný vliv <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, a <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c32ce-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c32ce-133">V .NET Core a .NET Native jsou ve výchozím nastavení povolené upravené pravidla analýzy dop. / odp.</span><span class="sxs-lookup"><span data-stu-id="c32ce-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="c32ce-134">Pokud není povolené analýzy pravidlo úpravy, první číslice řetězec je interpretován jako hodinu 12hodinový formát a zbytek řetězci s výjimkou dopoledne/odpoledne ignorováno.</span><span class="sxs-lookup"><span data-stu-id="c32ce-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="c32ce-135">Datum a čas, vrátí metoda analýzy se skládá z aktuálního data a hodina dne z řetězce data extrahovat.</span><span class="sxs-lookup"><span data-stu-id="c32ce-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="c32ce-136">Pokud je povolené analýzy pravidlo úpravy, při analýze metody interpretovat den a měsíc jako patřící do aktuálního roku a interpretovat jako hodina 12hodinový formát času.</span><span class="sxs-lookup"><span data-stu-id="c32ce-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="c32ce-137">Následující tabulka ukazuje rozdíly <xref:System.DateTime> hodnotu v případě <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> metoda se používá pro analýzu řetězce "" 4/10 6 AM"s `<EnableAmPmParseAdjustment>` elementu `enabled` vlastnost nastavena na"0"nebo"1".</span><span class="sxs-lookup"><span data-stu-id="c32ce-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="c32ce-138">Předpokládá, že dnešní datum je 5. ledna 2017 a zobrazí datum, jako kdyby je naformátována pomocí řetězec formátu "G" zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="c32ce-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="c32ce-139">Název jazykové verze</span><span class="sxs-lookup"><span data-stu-id="c32ce-139">Culture name</span></span>|<span data-ttu-id="c32ce-140">enabled="0"</span><span class="sxs-lookup"><span data-stu-id="c32ce-140">enabled="0"</span></span>|<span data-ttu-id="c32ce-141">enabled="1"</span><span class="sxs-lookup"><span data-stu-id="c32ce-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="c32ce-142">en-US</span><span class="sxs-lookup"><span data-stu-id="c32ce-142">en-US</span></span>|<span data-ttu-id="c32ce-143">1. 5. 2017 4:00:00: 00</span><span class="sxs-lookup"><span data-stu-id="c32ce-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="c32ce-144">4/10/2017 6:00:00: 00</span><span class="sxs-lookup"><span data-stu-id="c32ce-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="c32ce-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="c32ce-145">en-GB</span></span>|<span data-ttu-id="c32ce-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="c32ce-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="c32ce-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="c32ce-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c32ce-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c32ce-148">See also</span></span>

- [<span data-ttu-id="c32ce-149">\<modul runtime > – Element</span><span class="sxs-lookup"><span data-stu-id="c32ce-149">\<runtime> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)
- [<span data-ttu-id="c32ce-150">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="c32ce-150">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
