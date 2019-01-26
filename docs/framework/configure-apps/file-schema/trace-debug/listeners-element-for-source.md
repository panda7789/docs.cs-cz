---
title: '&lt;naslouchací procesy&gt; – Element pro &lt;zdroje&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 8378d34ffc2fea22fb5d16ed0b727da54ca74503
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083987"
---
# <a name="ltlistenersgt-element-for-ltsourcegt"></a><span data-ttu-id="314e3-102">&lt;naslouchací procesy&gt; – Element pro &lt;zdroje&gt;</span><span class="sxs-lookup"><span data-stu-id="314e3-102">&lt;listeners&gt; Element for &lt;source&gt;</span></span>
<span data-ttu-id="314e3-103">Přidá nebo odebere naslouchacích procesů v <xref:System.Diagnostics.TraceSource.Listeners%2A> kolekce <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="314e3-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="314e3-104">Naslouchací proces bude směrovat výstup trasování příslušný cíli, jako je protokol, okno nebo textový soubor.</span><span class="sxs-lookup"><span data-stu-id="314e3-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="314e3-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="314e3-105">\<configuration></span></span>  
<span data-ttu-id="314e3-106">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="314e3-106">\<system.diagnostics></span></span>  
<span data-ttu-id="314e3-107">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="314e3-107">\<sources></span></span>  
<span data-ttu-id="314e3-108">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="314e3-108">\<source></span></span>  
<span data-ttu-id="314e3-109">\<naslouchací procesy > – Element</span><span class="sxs-lookup"><span data-stu-id="314e3-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="314e3-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="314e3-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="314e3-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="314e3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="314e3-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="314e3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="314e3-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="314e3-113">Attributes</span></span>  
 <span data-ttu-id="314e3-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="314e3-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="314e3-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="314e3-115">Child Elements</span></span>  
  
|<span data-ttu-id="314e3-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="314e3-116">Element</span></span>|<span data-ttu-id="314e3-117">Popis</span><span class="sxs-lookup"><span data-stu-id="314e3-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="314e3-118">\<add></span><span class="sxs-lookup"><span data-stu-id="314e3-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="314e3-119">Přidá naslouchací proces pro `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="314e3-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="314e3-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="314e3-120">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="314e3-121">Odebere z naslouchacího procesu `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="314e3-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="314e3-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="314e3-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="314e3-123">Vymaže `Listeners` kolekci pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="314e3-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="314e3-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="314e3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="314e3-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="314e3-125">Element</span></span>|<span data-ttu-id="314e3-126">Popis</span><span class="sxs-lookup"><span data-stu-id="314e3-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="314e3-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="314e3-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="314e3-128">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="314e3-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="314e3-129">Obsahuje zdrojů trasování, které se zahájí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="314e3-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="314e3-130">Určuje zdroj trasování, který iniciuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="314e3-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="314e3-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="314e3-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="314e3-132">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="314e3-132">Configuration File</span></span>  
 <span data-ttu-id="314e3-133">Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="314e3-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="314e3-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="314e3-134">Example</span></span>  
 <span data-ttu-id="314e3-135">Následující příklad ukazuje způsob použití `<listeners>` prvku pro přidání naslouchacího procesu trasování konzoly pro `mySource` zdroje dat a Vymazat výchozí naslouchací služby stopy.</span><span class="sxs-lookup"><span data-stu-id="314e3-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="314e3-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="314e3-136">See also</span></span>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="314e3-137">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="314e3-137">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="314e3-138">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="314e3-138">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
