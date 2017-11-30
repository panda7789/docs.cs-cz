---
title: "&lt;moduly pro naslouchání&gt; Element pro &lt;zdroje&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 71b11cbc34bdbb5d414aa250ea2c2fce85cfac0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltlistenersgt-element-for-ltsourcegt"></a><span data-ttu-id="0816a-102">&lt;moduly pro naslouchání&gt; Element pro &lt;zdroje&gt;</span><span class="sxs-lookup"><span data-stu-id="0816a-102">&lt;listeners&gt; Element for &lt;source&gt;</span></span>
<span data-ttu-id="0816a-103">Přidá nebo odebere naslouchací procesy v <xref:System.Diagnostics.TraceSource.Listeners%2A> kolekci <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="0816a-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="0816a-104">Naslouchací proces nasměruje výstup trasování do příslušné cílové, jako je například protokol, okno nebo textového souboru.</span><span class="sxs-lookup"><span data-stu-id="0816a-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="0816a-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="0816a-105">\<configuration></span></span>  
<span data-ttu-id="0816a-106">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="0816a-106">\<system.diagnostics></span></span>  
<span data-ttu-id="0816a-107">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="0816a-107">\<sources></span></span>  
<span data-ttu-id="0816a-108">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="0816a-108">\<source></span></span>  
<span data-ttu-id="0816a-109">\<moduly pro naslouchání > elementu</span><span class="sxs-lookup"><span data-stu-id="0816a-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0816a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0816a-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0816a-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0816a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0816a-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0816a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0816a-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="0816a-113">Attributes</span></span>  
 <span data-ttu-id="0816a-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="0816a-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0816a-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0816a-115">Child Elements</span></span>  
  
|<span data-ttu-id="0816a-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="0816a-116">Element</span></span>|<span data-ttu-id="0816a-117">Popis</span><span class="sxs-lookup"><span data-stu-id="0816a-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0816a-118">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="0816a-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="0816a-119">Přidá naslouchací proces a `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="0816a-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="0816a-120">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="0816a-120">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="0816a-121">Odebere naslouchací proces z `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="0816a-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="0816a-122">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="0816a-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="0816a-123">Vymaže `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="0816a-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0816a-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0816a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0816a-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="0816a-125">Element</span></span>|<span data-ttu-id="0816a-126">Popis</span><span class="sxs-lookup"><span data-stu-id="0816a-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0816a-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0816a-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0816a-128">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="0816a-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="0816a-129">Obsahuje trasování zdrojů, které zahájí trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="0816a-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="0816a-130">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="0816a-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0816a-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0816a-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="0816a-132">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="0816a-132">Configuration File</span></span>  
 <span data-ttu-id="0816a-133">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="0816a-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0816a-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="0816a-134">Example</span></span>  
 <span data-ttu-id="0816a-135">Následující příklad ukazuje, jak používat `<listeners>` elementu, který chcete přidat naslouchací konzoly na `mySource` zdroje a odeberete naslouchací proces trasování výchozí.</span><span class="sxs-lookup"><span data-stu-id="0816a-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0816a-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="0816a-136">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="0816a-137">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="0816a-137">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="0816a-138">Trasování – moduly naslouchání</span><span class="sxs-lookup"><span data-stu-id="0816a-138">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
