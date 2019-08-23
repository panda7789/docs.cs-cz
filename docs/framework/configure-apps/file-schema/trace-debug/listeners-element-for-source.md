---
title: <listeners> – element pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 853bc94978218fd4d426e6070b3a36e20435cd6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920496"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="afda5-102">\<naslouchací prvky > elementu \<pro zdroj ></span><span class="sxs-lookup"><span data-stu-id="afda5-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="afda5-103">Přidá nebo odebere naslouchací procesy v <xref:System.Diagnostics.TraceSource.Listeners%2A> kolekci <xref:System.Diagnostics.TraceSource>pro.</span><span class="sxs-lookup"><span data-stu-id="afda5-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="afda5-104">Naslouchací proces směruje výstup trasování do příslušného cíle, jako je protokol, okno nebo textový soubor.</span><span class="sxs-lookup"><span data-stu-id="afda5-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="afda5-105">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="afda5-105">\<configuration></span></span>  
<span data-ttu-id="afda5-106">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="afda5-106">\<system.diagnostics></span></span>  
<span data-ttu-id="afda5-107">\<> zdrojů</span><span class="sxs-lookup"><span data-stu-id="afda5-107">\<sources></span></span>  
<span data-ttu-id="afda5-108">\<> zdroje</span><span class="sxs-lookup"><span data-stu-id="afda5-108">\<source></span></span>  
<span data-ttu-id="afda5-109">\<naslouchací prvky > elementu</span><span class="sxs-lookup"><span data-stu-id="afda5-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afda5-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afda5-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afda5-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="afda5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="afda5-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="afda5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afda5-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="afda5-113">Attributes</span></span>  
 <span data-ttu-id="afda5-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="afda5-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="afda5-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="afda5-115">Child Elements</span></span>  
  
|<span data-ttu-id="afda5-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="afda5-116">Element</span></span>|<span data-ttu-id="afda5-117">Popis</span><span class="sxs-lookup"><span data-stu-id="afda5-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afda5-118">\<add></span><span class="sxs-lookup"><span data-stu-id="afda5-118">\<add></span></span>](add-element-for-listeners-for-source.md)|<span data-ttu-id="afda5-119">Přidá naslouchací proces do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="afda5-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="afda5-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="afda5-120">\<remove></span></span>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="afda5-121">Odebere naslouchací proces z `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="afda5-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="afda5-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="afda5-122">\<clear></span></span>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="afda5-123">`Listeners` Vymaže kolekci zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="afda5-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="afda5-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="afda5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="afda5-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="afda5-125">Element</span></span>|<span data-ttu-id="afda5-126">Popis</span><span class="sxs-lookup"><span data-stu-id="afda5-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="afda5-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="afda5-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="afda5-128">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="afda5-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="afda5-129">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="afda5-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="afda5-130">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="afda5-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afda5-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="afda5-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="afda5-132">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="afda5-132">Configuration File</span></span>  
 <span data-ttu-id="afda5-133">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="afda5-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afda5-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="afda5-134">Example</span></span>  
 <span data-ttu-id="afda5-135">Následující příklad ukazuje, jak použít `<listeners>` element k přidání naslouchacího procesu trasování konzoly `mySource` ke zdroji a k odebrání výchozího naslouchacího procesu trasování.</span><span class="sxs-lookup"><span data-stu-id="afda5-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="afda5-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afda5-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="afda5-137">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="afda5-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="afda5-138">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="afda5-138">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
