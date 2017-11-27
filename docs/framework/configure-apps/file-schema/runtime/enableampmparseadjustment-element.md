---
title: "&lt;EnableAmPmParseAdjustment&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 44bd6297142b6f29d93e9a3bebdb89d32d4bf46a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltenableampmparseadjustmentgt-element"></a><span data-ttu-id="1da50-102">&lt;EnableAmPmParseAdjustment&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="1da50-102">&lt;EnableAmPmParseAdjustment&gt; Element</span></span>
<span data-ttu-id="1da50-103">Určuje, zda datum a čas analýza metody použít upravenou sadu pravidel analyzovat data řetězce, které obsahují den, měsíc, hodinu a označení dop. / odp.</span><span class="sxs-lookup"><span data-stu-id="1da50-103">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
 <span data-ttu-id="1da50-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="1da50-104">\<configuration></span></span>  
 <span data-ttu-id="1da50-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="1da50-105">\<runtime></span></span>  
<span data-ttu-id="1da50-106">\<EnableAmPmParseAdjustment ></span><span class="sxs-lookup"><span data-stu-id="1da50-106">\<EnableAmPmParseAdjustment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1da50-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1da50-107">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1da50-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1da50-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1da50-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1da50-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1da50-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="1da50-110">Attributes</span></span>  
  
|<span data-ttu-id="1da50-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="1da50-111">Attribute</span></span>|<span data-ttu-id="1da50-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1da50-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1da50-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="1da50-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1da50-114">Určuje, zda datum a čas analýza metody používat upravenou sadu pravidel analyzovat data řetězce, které obsahují pouze den, měsíc, hodinu a označení dop. / odp.</span><span class="sxs-lookup"><span data-stu-id="1da50-114">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="1da50-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="1da50-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="1da50-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1da50-116">Value</span></span>|<span data-ttu-id="1da50-117">Popis</span><span class="sxs-lookup"><span data-stu-id="1da50-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1da50-118">0</span><span class="sxs-lookup"><span data-stu-id="1da50-118">0</span></span>|<span data-ttu-id="1da50-119">Datum a čas analýza metody nepoužívejte upravenou pravidla pro Analýza řetězců data, které obsahují pouze den, měsíc, hodinu a označení dop. / odp.</span><span class="sxs-lookup"><span data-stu-id="1da50-119">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="1da50-120">1</span><span class="sxs-lookup"><span data-stu-id="1da50-120">1</span></span>|<span data-ttu-id="1da50-121">Datum a čas analýza metody použít k analýze datum řetězce, které obsahují pouze den, měsíc, hodinu a označení dop. / odp upravenou pravidla.</span><span class="sxs-lookup"><span data-stu-id="1da50-121">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1da50-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1da50-122">Child Elements</span></span>  
 <span data-ttu-id="1da50-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="1da50-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1da50-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1da50-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1da50-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="1da50-125">Element</span></span>|<span data-ttu-id="1da50-126">Popis</span><span class="sxs-lookup"><span data-stu-id="1da50-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1da50-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1da50-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1da50-128">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="1da50-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1da50-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1da50-129">Remarks</span></span>  
 <span data-ttu-id="1da50-130">`<EnableAmPmParseAdjustment>` Element řídí, jak tyto metody analyzovat data řetězec, který obsahuje číslem dne a měsíce, za nímž následuje hodinu a označení dop. / odp (například "4/10 6 AM"):</span><span class="sxs-lookup"><span data-stu-id="1da50-130">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="1da50-131">Žádné jiné vzorce jsou vliv.</span><span class="sxs-lookup"><span data-stu-id="1da50-131">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="1da50-132">`<EnableAmPmParseAdjustment>` Element nemá žádný vliv <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, a <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="1da50-132">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1da50-133">V .NET Core a .NET Native jsou ve výchozím nastavení povolené upravenou dop. / odp analýzy pravidla.</span><span class="sxs-lookup"><span data-stu-id="1da50-133">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="1da50-134">Pokud není povolena analýza pravidlo úpravy, první číslice řetězce se interpretuje jako hodinu 12 hodin a zbytek řetězci s výjimkou dop. / odp označení je ignorováno.</span><span class="sxs-lookup"><span data-stu-id="1da50-134">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="1da50-135">Datum a čas, vrátí metoda analýzy se skládá z aktuální datum a hodinu dne extrahovat z řetězce datum.</span><span class="sxs-lookup"><span data-stu-id="1da50-135">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="1da50-136">Pokud je povolena analýza pravidlo úpravy, analýza metoda interpretovat dne a měsíce jako náležící do aktuálního roku a interpretovat dobu jako hodinu 12 hodin.</span><span class="sxs-lookup"><span data-stu-id="1da50-136">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="1da50-137">Následující tabulka ukazuje rozdíly <xref:System.DateTime> hodnotu v případě <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> je metoda použitá k analýze řetězec "" 4/10 6 AM"s `<EnableAmPmParseAdjustment>` elementu `enabled` vlastnost nastavena na hodnotu"0"nebo"1".</span><span class="sxs-lookup"><span data-stu-id="1da50-137">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="1da50-138">Předpokládá, že dnešní datum je 5. ledna 2017 a zobrazuje datum, jako kdyby je naformátovaný pomocí řetězce formátu "G" zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="1da50-138">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="1da50-139">Název jazykové verze</span><span class="sxs-lookup"><span data-stu-id="1da50-139">Culture name</span></span>|<span data-ttu-id="1da50-140">Povolit = "0"</span><span class="sxs-lookup"><span data-stu-id="1da50-140">enabled="0"</span></span>|<span data-ttu-id="1da50-141">Povolit = "1"</span><span class="sxs-lookup"><span data-stu-id="1da50-141">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="1da50-142">en US</span><span class="sxs-lookup"><span data-stu-id="1da50-142">en-US</span></span>|<span data-ttu-id="1da50-143">1/5/2017 4:00:00: 00</span><span class="sxs-lookup"><span data-stu-id="1da50-143">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="1da50-144">4/10/2017 6:00:00: 00</span><span class="sxs-lookup"><span data-stu-id="1da50-144">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="1da50-145">en-GB</span><span class="sxs-lookup"><span data-stu-id="1da50-145">en-GB</span></span>|<span data-ttu-id="1da50-146">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="1da50-146">5/1/2017 6:00:00</span></span>|<span data-ttu-id="1da50-147">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="1da50-147">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1da50-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="1da50-148">See Also</span></span>  
 [<span data-ttu-id="1da50-149">\<modul runtime > elementu</span><span class="sxs-lookup"><span data-stu-id="1da50-149">\<runtime> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
 [<span data-ttu-id="1da50-150">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="1da50-150">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
