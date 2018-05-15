---
title: '&lt;System.Diagnostics&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 090c296ba84043445364b350c8b74587c35b5940
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltsystemdiagnosticsgt-element"></a><span data-ttu-id="7a95b-102">&lt;System.Diagnostics&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="7a95b-102">&lt;system.diagnostics&gt; Element</span></span>
<span data-ttu-id="7a95b-103">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="7a95b-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="7a95b-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="7a95b-104">\<configuration></span></span>  
<span data-ttu-id="7a95b-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="7a95b-105">\<system.diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a95b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a95b-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a95b-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7a95b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7a95b-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7a95b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a95b-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="7a95b-109">Attributes</span></span>  
 <span data-ttu-id="7a95b-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="7a95b-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7a95b-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7a95b-111">Child Elements</span></span>  
  
|<span data-ttu-id="7a95b-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="7a95b-112">Element</span></span>|<span data-ttu-id="7a95b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7a95b-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a95b-114">\<Assert – ></span><span class="sxs-lookup"><span data-stu-id="7a95b-114">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="7a95b-115">Určuje, jestli se má zobrazit okno se zprávou při volání <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metoda; také určuje název souboru pro zápis zprávy.</span><span class="sxs-lookup"><span data-stu-id="7a95b-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="7a95b-116">\<čítače výkonu ></span><span class="sxs-lookup"><span data-stu-id="7a95b-116">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="7a95b-117">Určuje velikost globální paměť sdíleny čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="7a95b-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="7a95b-118">\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="7a95b-118">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="7a95b-119">Obsahuje naslouchací procesy, které může odkazovat všechny zdroje nebo element trasování.</span><span class="sxs-lookup"><span data-stu-id="7a95b-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="7a95b-120">Moduly pro naslouchání identifikovány jako sdílené moduly pro naslouchání mohou být přidány do zdroje nebo trasování podle názvu.</span><span class="sxs-lookup"><span data-stu-id="7a95b-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="7a95b-121">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="7a95b-121">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="7a95b-122">Určuje trasování zdrojů, které zahájí trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="7a95b-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="7a95b-123">\<přepínače ></span><span class="sxs-lookup"><span data-stu-id="7a95b-123">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="7a95b-124">Obsahuje trasování – přepínače a úrovně, kde jsou nastaveny trasování – přepínače.</span><span class="sxs-lookup"><span data-stu-id="7a95b-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="7a95b-125">\<trasování ></span><span class="sxs-lookup"><span data-stu-id="7a95b-125">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="7a95b-126">Obsahuje naslouchací procesy, které shromažďování, ukládání a směrovat trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="7a95b-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7a95b-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7a95b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="7a95b-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="7a95b-128">Element</span></span>|<span data-ttu-id="7a95b-129">Popis</span><span class="sxs-lookup"><span data-stu-id="7a95b-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7a95b-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7a95b-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7a95b-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a95b-131">Example</span></span>  
 <span data-ttu-id="7a95b-132">Následující příklad ukazuje, jak pro vložení přepínače trasování a naslouchací uvnitř  **\<system.diagnostics >** element.</span><span class="sxs-lookup"><span data-stu-id="7a95b-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="7a95b-133">`General` Přepínač trasování je nastaven na hodnotu <xref:System.Diagnostics.TraceLevel> úroveň.</span><span class="sxs-lookup"><span data-stu-id="7a95b-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="7a95b-134">Naslouchací proces trasování `myListener` vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="7a95b-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a95b-135">V rozhraní .NET Framework verze 2.0 můžete zadat hodnotu pro přepínač text.</span><span class="sxs-lookup"><span data-stu-id="7a95b-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="7a95b-136">Například můžete zadat `true` pro <xref:System.Diagnostics.BooleanSwitch> nebo použijte text, například představující hodnotu výčtu `Error` pro <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="7a95b-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="7a95b-137">Na řádku `<add name="myTraceSwitch" value="Error" />` je ekvivalentní `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="7a95b-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a95b-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a95b-138">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="7a95b-139">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="7a95b-139">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
