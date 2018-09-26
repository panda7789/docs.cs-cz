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
ms.openlocfilehash: 35fe167beb53c27aa511e08507415a26b1749ca2
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193223"
---
# <a name="ltsystemdiagnosticsgt-element"></a><span data-ttu-id="165c4-102">&lt;System.Diagnostics&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="165c4-102">&lt;system.diagnostics&gt; Element</span></span>
<span data-ttu-id="165c4-103">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="165c4-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="165c4-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="165c4-104">\<configuration></span></span>  
<span data-ttu-id="165c4-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="165c4-105">\<system.diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="165c4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="165c4-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="165c4-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="165c4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="165c4-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="165c4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="165c4-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="165c4-109">Attributes</span></span>  
 <span data-ttu-id="165c4-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="165c4-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="165c4-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="165c4-111">Child Elements</span></span>  
  
|<span data-ttu-id="165c4-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="165c4-112">Element</span></span>|<span data-ttu-id="165c4-113">Popis</span><span class="sxs-lookup"><span data-stu-id="165c4-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="165c4-114">\<vyhodnocení ></span><span class="sxs-lookup"><span data-stu-id="165c4-114">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="165c4-115">Určuje, jestli se má zobrazit okno se zprávou, když zavoláte <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metoda; také určuje název souboru pro zápis zpráv do.</span><span class="sxs-lookup"><span data-stu-id="165c4-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="165c4-116">\<čítače výkonu ></span><span class="sxs-lookup"><span data-stu-id="165c4-116">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="165c4-117">Určuje velikost globální paměť sdílenou čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="165c4-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="165c4-118">\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="165c4-118">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="165c4-119">Obsahuje moduly pro naslouchání, které všechny zdroje nebo trasování – element může odkazovat.</span><span class="sxs-lookup"><span data-stu-id="165c4-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="165c4-120">Naslouchací procesy, které jsou identifikovány jako sdílené moduly pro naslouchání lze přidat do zdroje nebo trasování podle názvu.</span><span class="sxs-lookup"><span data-stu-id="165c4-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="165c4-121">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="165c4-121">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="165c4-122">Určuje zdrojů trasování, které se zahájí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="165c4-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="165c4-123">\<přepínače ></span><span class="sxs-lookup"><span data-stu-id="165c4-123">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="165c4-124">Obsahuje přepínače trasování a úrovně, ve kterém jsou nastavené přepínačů trasování.</span><span class="sxs-lookup"><span data-stu-id="165c4-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="165c4-125">\<trasování ></span><span class="sxs-lookup"><span data-stu-id="165c4-125">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="165c4-126">Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="165c4-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="165c4-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="165c4-127">Parent Elements</span></span>  
  
|<span data-ttu-id="165c4-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="165c4-128">Element</span></span>|<span data-ttu-id="165c4-129">Popis</span><span class="sxs-lookup"><span data-stu-id="165c4-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="165c4-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="165c4-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="165c4-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="165c4-131">Example</span></span>  
 <span data-ttu-id="165c4-132">Následující příklad ukazuje postup vložení přepínače trasování a posluchače trasování uvnitř  **\<system.diagnostics >** elementu.</span><span class="sxs-lookup"><span data-stu-id="165c4-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="165c4-133">`General` Trasování přepínač nastavený na <xref:System.Diagnostics.TraceLevel> úroveň.</span><span class="sxs-lookup"><span data-stu-id="165c4-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="165c4-134">Naslouchací proces trasování `myListener` vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="165c4-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="165c4-135">V rozhraní .NET Framework verze 2.0 můžete zadat hodnotu pro přepínač text.</span><span class="sxs-lookup"><span data-stu-id="165c4-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="165c4-136">Například můžete zadat `true` pro <xref:System.Diagnostics.BooleanSwitch> nebo textů představující hodnotu výčtu, jako `Error` pro <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="165c4-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="165c4-137">Na řádku `<add name="myTraceSwitch" value="Error" />` je ekvivalentní `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="165c4-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="165c4-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="165c4-138">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="165c4-139">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="165c4-139">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
