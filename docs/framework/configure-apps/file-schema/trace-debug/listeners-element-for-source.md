---
title: Element <listeners> pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 0eee325e01b41a15a19e4f40f479596f9d70f73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153409"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="1f801-102">\<naslouchací> Element pro \<zdrojový></span><span class="sxs-lookup"><span data-stu-id="1f801-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="1f801-103">Přidá nebo odebere posluchače v kolekci <xref:System.Diagnostics.TraceSource.Listeners%2A> pro <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="1f801-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="1f801-104">Naslouchací proces směruje výstup trasování na příslušný cíl, například protokol, okno nebo textový soubor.</span><span class="sxs-lookup"><span data-stu-id="1f801-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[<span data-ttu-id="1f801-105">**\<>konfigurace**</span><span class="sxs-lookup"><span data-stu-id="1f801-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="1f801-106">&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f801-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="1f801-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdroje>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f801-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="1f801-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdrojové>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f801-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="1f801-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<posluchači>**</span><span class="sxs-lookup"><span data-stu-id="1f801-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f801-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f801-110">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f801-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1f801-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1f801-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1f801-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f801-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="1f801-113">Attributes</span></span>  
 <span data-ttu-id="1f801-114">Žádné.</span><span class="sxs-lookup"><span data-stu-id="1f801-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1f801-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1f801-115">Child Elements</span></span>  
  
|<span data-ttu-id="1f801-116">Element</span><span class="sxs-lookup"><span data-stu-id="1f801-116">Element</span></span>|<span data-ttu-id="1f801-117">Popis</span><span class="sxs-lookup"><span data-stu-id="1f801-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f801-118">\<přidat></span><span class="sxs-lookup"><span data-stu-id="1f801-118">\<add></span></span>](add-element-for-listeners-for-source.md)|<span data-ttu-id="1f801-119">Přidá naslouchací proces do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="1f801-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="1f801-120">\<odebrat></span><span class="sxs-lookup"><span data-stu-id="1f801-120">\<remove></span></span>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="1f801-121">Odebere naslouchací proces z `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="1f801-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="1f801-122">\<jasné></span><span class="sxs-lookup"><span data-stu-id="1f801-122">\<clear></span></span>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="1f801-123">Vymaže kolekci `Listeners` pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="1f801-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f801-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1f801-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1f801-125">Element</span><span class="sxs-lookup"><span data-stu-id="1f801-125">Element</span></span>|<span data-ttu-id="1f801-126">Popis</span><span class="sxs-lookup"><span data-stu-id="1f801-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1f801-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1f801-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1f801-128">Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="1f801-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="1f801-129">Obsahuje zdroje trasování, které iniciují tracing zprávy.</span><span class="sxs-lookup"><span data-stu-id="1f801-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="1f801-130">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="1f801-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f801-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f801-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="1f801-132">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="1f801-132">Configuration File</span></span>  
 <span data-ttu-id="1f801-133">Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f801-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f801-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f801-134">Example</span></span>  
 <span data-ttu-id="1f801-135">Následující příklad ukazuje, jak `<listeners>` použít prvek k přidání `mySource` posluchače trasování konzoly do zdroje a odebrat výchozí naslouchací proces trasování.</span><span class="sxs-lookup"><span data-stu-id="1f801-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f801-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f801-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="1f801-137">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="1f801-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1f801-138">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="1f801-138">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
