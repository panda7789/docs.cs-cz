---
title: "&lt;Filtr&gt; Element pro &lt;přidat&gt; pro &lt;naslouchací procesy&gt; pro &lt;zdroje&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3b02f97caeef2a560682e5746c6c24986d5a3ad2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="fa41d-102">&lt;Filtr&gt; Element pro &lt;přidat&gt; pro &lt;naslouchací procesy&gt; pro &lt;zdroje&gt;</span><span class="sxs-lookup"><span data-stu-id="fa41d-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="fa41d-103">Přidá filtr do naslouchací proces ve `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="fa41d-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="fa41d-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="fa41d-104">\<configuration></span></span>  
<span data-ttu-id="fa41d-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="fa41d-105">\<system.diagnostics></span></span>  
<span data-ttu-id="fa41d-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="fa41d-106">\<sources></span></span>  
<span data-ttu-id="fa41d-107">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="fa41d-107">\<source></span></span>  
<span data-ttu-id="fa41d-108">\<moduly pro naslouchání ></span><span class="sxs-lookup"><span data-stu-id="fa41d-108">\<listeners></span></span>  
<span data-ttu-id="fa41d-109">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="fa41d-109">\<add></span></span>  
<span data-ttu-id="fa41d-110">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="fa41d-110">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa41d-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa41d-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa41d-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fa41d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fa41d-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fa41d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa41d-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="fa41d-114">Attributes</span></span>  
  
|<span data-ttu-id="fa41d-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="fa41d-115">Attribute</span></span>|<span data-ttu-id="fa41d-116">Popis</span><span class="sxs-lookup"><span data-stu-id="fa41d-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="fa41d-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="fa41d-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="fa41d-118">Určuje typ filtru, který by měl dědí <xref:System.Diagnostics.TraceFilter> třídy.</span><span class="sxs-lookup"><span data-stu-id="fa41d-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="fa41d-119">Můžete použít obor názvů kvalifikovaný název typu, který odpovídá na typ <xref:System.Type.FullName%2A> vlastnost, nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení, který odpovídá <xref:System.Type.AssemblyQualifiedName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fa41d-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="fa41d-120">Informace o úplné názvy typů najdete v tématu [určení plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="fa41d-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="fa41d-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="fa41d-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fa41d-122">Řetězec předaný konstruktoru pro třídu zadaný filtr.</span><span class="sxs-lookup"><span data-stu-id="fa41d-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa41d-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fa41d-123">Child Elements</span></span>  
 <span data-ttu-id="fa41d-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="fa41d-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fa41d-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fa41d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="fa41d-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="fa41d-126">Element</span></span>|<span data-ttu-id="fa41d-127">Popis</span><span class="sxs-lookup"><span data-stu-id="fa41d-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fa41d-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fa41d-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fa41d-129">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="fa41d-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="fa41d-130">Obsahuje trasování zdrojů, které zahájí trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="fa41d-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="fa41d-131">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="fa41d-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="fa41d-132">Obsahuje naslouchací procesy, které shromažďování, ukládání a směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="fa41d-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="fa41d-133">Moduly pro naslouchání přesměrujte výstup trasování do příslušné cílové.</span><span class="sxs-lookup"><span data-stu-id="fa41d-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="fa41d-134">Přidá naslouchací proces a `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="fa41d-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa41d-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa41d-135">Remarks</span></span>  
 <span data-ttu-id="fa41d-136">`<filter>` Element musí být obsažená v `<add>` element pro naslouchací proces zdroj trasování, který určuje typ naslouchacího procesu, nikoli jen název naslouchací proces definované v [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="fa41d-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="fa41d-137">Pokud naslouchací proces je definována v [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtr pro tento naslouchacího procesu musí být definován v daný element.</span><span class="sxs-lookup"><span data-stu-id="fa41d-137">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="fa41d-138">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="fa41d-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa41d-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa41d-139">Example</span></span>  
 <span data-ttu-id="fa41d-140">Následující příklad ukazuje, jak používat `<filter>` elementu, který chcete přidat filtr na naslouchací proces `console` v `Listeners` kolekci pro zdroj trasování `myTraceSource`, zadání úroveň události filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="fa41d-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa41d-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa41d-141">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="fa41d-142">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="fa41d-142">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
