---
title: '&lt;trasování&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 55a7eb431432b67b3252853d14bf93be304ee883
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046512"
---
# <a name="lttracegt-element"></a><span data-ttu-id="19ac3-102">&lt;trasování&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="19ac3-102">&lt;trace&gt; Element</span></span>
<span data-ttu-id="19ac3-103">Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="19ac3-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
 <span data-ttu-id="19ac3-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="19ac3-104">\<configuration></span></span>  
<span data-ttu-id="19ac3-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="19ac3-105">\<system.diagnostics></span></span>  
<span data-ttu-id="19ac3-106">\<trasování ></span><span class="sxs-lookup"><span data-stu-id="19ac3-106">\<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19ac3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19ac3-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19ac3-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="19ac3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="19ac3-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="19ac3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19ac3-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="19ac3-110">Attributes</span></span>  
  
|<span data-ttu-id="19ac3-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="19ac3-111">Attribute</span></span>|<span data-ttu-id="19ac3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="19ac3-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="19ac3-113">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="19ac3-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="19ac3-114">Určuje, zda naslouchacími procesy trasování automaticky vyprázdní výstupní vyrovnávací paměť po každé operaci zápisu.</span><span class="sxs-lookup"><span data-stu-id="19ac3-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="19ac3-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="19ac3-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="19ac3-116">Určuje počet mezer pro odsazení.</span><span class="sxs-lookup"><span data-stu-id="19ac3-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="19ac3-117">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="19ac3-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="19ac3-118">Označuje, zda má být použita globální zámku.</span><span class="sxs-lookup"><span data-stu-id="19ac3-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="19ac3-119">autoflush atribut</span><span class="sxs-lookup"><span data-stu-id="19ac3-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="19ac3-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="19ac3-120">Value</span></span>|<span data-ttu-id="19ac3-121">Popis</span><span class="sxs-lookup"><span data-stu-id="19ac3-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="19ac3-122">Není vyprázdnění automaticky výstupní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="19ac3-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="19ac3-123">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="19ac3-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="19ac3-124">Automaticky vyprázdní vyrovnávací paměť pro výstup.</span><span class="sxs-lookup"><span data-stu-id="19ac3-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="19ac3-125">useGlobalLock atribut</span><span class="sxs-lookup"><span data-stu-id="19ac3-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="19ac3-126">Hodnota</span><span class="sxs-lookup"><span data-stu-id="19ac3-126">Value</span></span>|<span data-ttu-id="19ac3-127">Popis</span><span class="sxs-lookup"><span data-stu-id="19ac3-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="19ac3-128">Nepoužívá globální uzamčení, pokud je bezpečná; pro naslouchací proces v opačném případě používá globální zámku.</span><span class="sxs-lookup"><span data-stu-id="19ac3-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="19ac3-129">Používá globální zámek bez ohledu na to, jestli je bezpečná pro naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="19ac3-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="19ac3-130">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="19ac3-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19ac3-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="19ac3-131">Child Elements</span></span>  
  
|<span data-ttu-id="19ac3-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="19ac3-132">Element</span></span>|<span data-ttu-id="19ac3-133">Popis</span><span class="sxs-lookup"><span data-stu-id="19ac3-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19ac3-134">\<naslouchací procesy ></span><span class="sxs-lookup"><span data-stu-id="19ac3-134">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|<span data-ttu-id="19ac3-135">Určuje naslouchací proces, který shromažďuje, ukládá a provádí směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="19ac3-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19ac3-136">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="19ac3-136">Parent Elements</span></span>  
  
|<span data-ttu-id="19ac3-137">Prvek</span><span class="sxs-lookup"><span data-stu-id="19ac3-137">Element</span></span>|<span data-ttu-id="19ac3-138">Popis</span><span class="sxs-lookup"><span data-stu-id="19ac3-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="19ac3-139">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="19ac3-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="19ac3-140">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="19ac3-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="19ac3-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="19ac3-141">Example</span></span>  
 <span data-ttu-id="19ac3-142">Následující příklad ukazuje způsob použití `<trace>` prvek a přidat naslouchací proces `MyListener` k `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="19ac3-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="19ac3-143">`MyListener` Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="19ac3-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="19ac3-144">`useGlobalLock` Atribut je nastaven na `false`, což způsobí, že globální zámek nechcete použít, pokud je bezpečná pro posluchače trasování.</span><span class="sxs-lookup"><span data-stu-id="19ac3-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="19ac3-145">`autoflush` Atribut je nastaven na `true`, což způsobí, že naslouchací proces trasování pro zápis do souboru bez ohledu na to, zda <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="19ac3-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="19ac3-146">`indentsize` Atribut je nastaven na hodnotu 0 (nula), což způsobí, že naslouchací proces odsazení nulové prostory při <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="19ac3-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="19ac3-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="19ac3-147">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [<span data-ttu-id="19ac3-148">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="19ac3-148">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
