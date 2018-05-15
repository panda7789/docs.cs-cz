---
title: '&lt;moduly pro naslouchání&gt; Element pro &lt;trasování&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2f0d795d6a8789772ff3fd46648fbc0d683c66e5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltlistenersgt-element-for-lttracegt"></a><span data-ttu-id="3a83c-102">&lt;moduly pro naslouchání&gt; Element pro &lt;trasování&gt;</span><span class="sxs-lookup"><span data-stu-id="3a83c-102">&lt;listeners&gt; Element for &lt;trace&gt;</span></span>
<span data-ttu-id="3a83c-103">Určuje naslouchací proces, který shromažďuje, úložiště a směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="3a83c-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="3a83c-104">Moduly pro naslouchání přesměrujte výstup trasování do příslušné cílové.</span><span class="sxs-lookup"><span data-stu-id="3a83c-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
 <span data-ttu-id="3a83c-105">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="3a83c-105">\<configuration> Element</span></span>  
<span data-ttu-id="3a83c-106">\<System.Diagnostics > elementu</span><span class="sxs-lookup"><span data-stu-id="3a83c-106">\<system.diagnostics> Element</span></span>  
<span data-ttu-id="3a83c-107">\<trasování > elementu</span><span class="sxs-lookup"><span data-stu-id="3a83c-107">\<trace> Element</span></span>  
<span data-ttu-id="3a83c-108">\<moduly pro naslouchání > elementu pro \<trasování ></span><span class="sxs-lookup"><span data-stu-id="3a83c-108">\<listeners> Element for \<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a83c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a83c-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a83c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3a83c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3a83c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3a83c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a83c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3a83c-112">Attributes</span></span>  
 <span data-ttu-id="3a83c-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="3a83c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3a83c-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3a83c-114">Child Elements</span></span>  
  
|<span data-ttu-id="3a83c-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="3a83c-115">Element</span></span>|<span data-ttu-id="3a83c-116">Popis</span><span class="sxs-lookup"><span data-stu-id="3a83c-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a83c-117">\<add></span><span class="sxs-lookup"><span data-stu-id="3a83c-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="3a83c-118">Přidá naslouchací proces a `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="3a83c-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="3a83c-119">\<clear></span><span class="sxs-lookup"><span data-stu-id="3a83c-119">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|<span data-ttu-id="3a83c-120">Vymaže `Listeners` kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="3a83c-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="3a83c-121">\<remove></span><span class="sxs-lookup"><span data-stu-id="3a83c-121">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|<span data-ttu-id="3a83c-122">Odebere naslouchací proces z `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="3a83c-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a83c-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3a83c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3a83c-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="3a83c-124">Element</span></span>|<span data-ttu-id="3a83c-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3a83c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3a83c-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3a83c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3a83c-127">Určuje kořenový element pro konfigurační oddíl technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3a83c-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="3a83c-128">Obsahuje naslouchací procesy, které shromažďování, ukládání a směrovat trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="3a83c-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a83c-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3a83c-129">Remarks</span></span>  
 <span data-ttu-id="3a83c-130"><xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> třídy sdílet stejný **naslouchací procesy** kolekce.</span><span class="sxs-lookup"><span data-stu-id="3a83c-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="3a83c-131">Pokud přidáte objekt naslouchací proces ke kolekci v jedné z těchto tříd, používá jiná třída stejný naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="3a83c-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="3a83c-132">Naslouchací proces třídy součástí rozhraní .NET Framework odvozena od <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="3a83c-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="3a83c-133">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="3a83c-133">Configuration File</span></span>  
 <span data-ttu-id="3a83c-134">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="3a83c-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a83c-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a83c-135">Example</span></span>  
 <span data-ttu-id="3a83c-136">Následující příklad ukazuje, jak používat  **\<naslouchací procesy >** elementu, který chcete přidat posluchače `MyListener` a `MyEventListener` k **naslouchací procesy** kolekce.</span><span class="sxs-lookup"><span data-stu-id="3a83c-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="3a83c-137">`MyListener` Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="3a83c-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="3a83c-138">`MyEventListener` vytvoří záznam v protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="3a83c-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a83c-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a83c-139">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="3a83c-140">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="3a83c-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
