---
title: '&lt;Filtr&gt; Element pro &lt;přidat&gt; pro &lt;naslouchací procesy&gt; pro &lt;trasování&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 095212f73adb906d9d80db747c331c436c1cf846
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745776"
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="fe0ed-102">&lt;Filtr&gt; Element pro &lt;přidat&gt; pro &lt;naslouchací procesy&gt; pro &lt;trasování&gt;</span><span class="sxs-lookup"><span data-stu-id="fe0ed-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="fe0ed-103">Přidá filtr do naslouchací proces ve `Listeners` kolekci pro trasování.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
 <span data-ttu-id="fe0ed-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="fe0ed-104">\<configuration></span></span>  
<span data-ttu-id="fe0ed-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="fe0ed-105">\<system.diagnostics></span></span>  
<span data-ttu-id="fe0ed-106">\<trasování ></span><span class="sxs-lookup"><span data-stu-id="fe0ed-106">\<trace></span></span>  
<span data-ttu-id="fe0ed-107">\<moduly pro naslouchání ></span><span class="sxs-lookup"><span data-stu-id="fe0ed-107">\<listeners></span></span>  
<span data-ttu-id="fe0ed-108">\<add></span><span class="sxs-lookup"><span data-stu-id="fe0ed-108">\<add></span></span>  
<span data-ttu-id="fe0ed-109">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="fe0ed-109">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe0ed-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe0ed-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe0ed-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fe0ed-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fe0ed-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe0ed-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="fe0ed-113">Attributes</span></span>  
  
|<span data-ttu-id="fe0ed-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="fe0ed-114">Attribute</span></span>|<span data-ttu-id="fe0ed-115">Popis</span><span class="sxs-lookup"><span data-stu-id="fe0ed-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="fe0ed-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="fe0ed-117">Určuje typ filtru, který by měl dědí <xref:System.Diagnostics.TraceFilter> třídy.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="fe0ed-118">Můžete použít obor názvů kvalifikovaný název typu, který odpovídá na typ <xref:System.Type.FullName%2A> vlastnost, nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení, který odpovídá <xref:System.Type.AssemblyQualifiedName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="fe0ed-119">Informace o úplné názvy typů najdete v tématu [určení plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="fe0ed-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="fe0ed-120">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fe0ed-121">Řetězec předaný konstruktoru pro třídu zadaný filtr.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe0ed-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fe0ed-122">Child Elements</span></span>  
 <span data-ttu-id="fe0ed-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="fe0ed-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe0ed-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fe0ed-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fe0ed-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe0ed-125">Element</span></span>|<span data-ttu-id="fe0ed-126">Popis</span><span class="sxs-lookup"><span data-stu-id="fe0ed-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fe0ed-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fe0ed-128">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="fe0ed-129">Obsahuje naslouchací procesy, které shromažďování, ukládání a směrovat trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="fe0ed-130">Obsahuje naslouchací procesy, které shromažďování, ukládání a směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="fe0ed-131">Moduly pro naslouchání přesměrujte výstup trasování do příslušné cílové.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="fe0ed-132">Přidá naslouchací proces a `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe0ed-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe0ed-133">Remarks</span></span>  
 <span data-ttu-id="fe0ed-134">`<filter>` Element musí být obsažená v `<add>` element pro naslouchací proces trasování, který určuje typ naslouchacího procesu, nikoli jen název naslouchací proces definované v [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="fe0ed-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="fe0ed-135">Pokud naslouchací proces je definována v [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtr pro tento naslouchacího procesu musí být definován v daný element.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-135">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="fe0ed-136">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe0ed-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="fe0ed-137">Example</span></span>  
 <span data-ttu-id="fe0ed-138">Následující příklad ukazuje, jak používat `<filter>` elementu, který chcete přidat filtr na naslouchací proces `console` v `Listeners` kolekce pro trasování, úroveň události filtru jako zadání `Error`.</span><span class="sxs-lookup"><span data-stu-id="fe0ed-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe0ed-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe0ed-139">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="fe0ed-140">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="fe0ed-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
