---
title: '&lt;moduly pro naslouchání&gt; Element pro &lt;zdroje&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a711b8d6bfd5b6d73d3240cb84810841bdc5a2b6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746836"
---
# <a name="ltlistenersgt-element-for-ltsourcegt"></a><span data-ttu-id="fcf8b-102">&lt;moduly pro naslouchání&gt; Element pro &lt;zdroje&gt;</span><span class="sxs-lookup"><span data-stu-id="fcf8b-102">&lt;listeners&gt; Element for &lt;source&gt;</span></span>
<span data-ttu-id="fcf8b-103">Přidá nebo odebere naslouchací procesy v <xref:System.Diagnostics.TraceSource.Listeners%2A> kolekci <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="fcf8b-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="fcf8b-104">Naslouchací proces nasměruje výstup trasování do příslušné cílové, jako je například protokol, okno nebo textového souboru.</span><span class="sxs-lookup"><span data-stu-id="fcf8b-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="fcf8b-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="fcf8b-105">\<configuration></span></span>  
<span data-ttu-id="fcf8b-106">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="fcf8b-106">\<system.diagnostics></span></span>  
<span data-ttu-id="fcf8b-107">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="fcf8b-107">\<sources></span></span>  
<span data-ttu-id="fcf8b-108">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="fcf8b-108">\<source></span></span>  
<span data-ttu-id="fcf8b-109">\<moduly pro naslouchání > elementu</span><span class="sxs-lookup"><span data-stu-id="fcf8b-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcf8b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcf8b-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcf8b-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fcf8b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fcf8b-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fcf8b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcf8b-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="fcf8b-113">Attributes</span></span>  
 <span data-ttu-id="fcf8b-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="fcf8b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fcf8b-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fcf8b-115">Child Elements</span></span>  
  
|<span data-ttu-id="fcf8b-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="fcf8b-116">Element</span></span>|<span data-ttu-id="fcf8b-117">Popis</span><span class="sxs-lookup"><span data-stu-id="fcf8b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fcf8b-118">\<add></span><span class="sxs-lookup"><span data-stu-id="fcf8b-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="fcf8b-119">Přidá naslouchací proces a `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="fcf8b-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="fcf8b-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="fcf8b-120">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="fcf8b-121">Odebere naslouchací proces z `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="fcf8b-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="fcf8b-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="fcf8b-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="fcf8b-123">Vymaže `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="fcf8b-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fcf8b-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fcf8b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fcf8b-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="fcf8b-125">Element</span></span>|<span data-ttu-id="fcf8b-126">Popis</span><span class="sxs-lookup"><span data-stu-id="fcf8b-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fcf8b-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fcf8b-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fcf8b-128">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="fcf8b-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="fcf8b-129">Obsahuje trasování zdrojů, které zahájí trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="fcf8b-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="fcf8b-130">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="fcf8b-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcf8b-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fcf8b-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="fcf8b-132">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="fcf8b-132">Configuration File</span></span>  
 <span data-ttu-id="fcf8b-133">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcf8b-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcf8b-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="fcf8b-134">Example</span></span>  
 <span data-ttu-id="fcf8b-135">Následující příklad ukazuje, jak používat `<listeners>` elementu, který chcete přidat naslouchací konzoly na `mySource` zdroje a odeberete naslouchací proces trasování výchozí.</span><span class="sxs-lookup"><span data-stu-id="fcf8b-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fcf8b-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="fcf8b-136">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="fcf8b-137">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="fcf8b-137">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="fcf8b-138">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="fcf8b-138">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
