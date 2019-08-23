---
title: < element System. Diagnostics >
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: f3b4238a8d7028d47122a420526b38ee4f327332
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926935"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="21a65-102">\<System. Diagnostics > – element</span><span class="sxs-lookup"><span data-stu-id="21a65-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="21a65-103">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="21a65-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="21a65-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="21a65-104">\<configuration></span></span>  
<span data-ttu-id="21a65-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="21a65-105">\<system.diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21a65-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21a65-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21a65-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="21a65-107">Attributes and Elements</span></span>  
 <span data-ttu-id="21a65-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="21a65-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21a65-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="21a65-109">Attributes</span></span>  
 <span data-ttu-id="21a65-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="21a65-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="21a65-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="21a65-111">Child Elements</span></span>  
  
|<span data-ttu-id="21a65-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="21a65-112">Element</span></span>|<span data-ttu-id="21a65-113">Popis</span><span class="sxs-lookup"><span data-stu-id="21a65-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21a65-114">\<assert></span><span class="sxs-lookup"><span data-stu-id="21a65-114">\<assert></span></span>](assert-element.md)|<span data-ttu-id="21a65-115">Určuje, zda se má při volání <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metody zobrazit okno se zprávou. určuje také název souboru, do kterého budou zapsány zprávy.</span><span class="sxs-lookup"><span data-stu-id="21a65-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="21a65-116">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="21a65-116">\<performanceCounters></span></span>](performancecounters-element.md)|<span data-ttu-id="21a65-117">Určuje velikost globální paměti sdílené čítači výkonu.</span><span class="sxs-lookup"><span data-stu-id="21a65-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="21a65-118">\<> sharedListeners</span><span class="sxs-lookup"><span data-stu-id="21a65-118">\<sharedListeners></span></span>](sharedlisteners-element.md)|<span data-ttu-id="21a65-119">Obsahuje naslouchací procesy, na které může odkazovat jakýkoliv element source nebo Trace.</span><span class="sxs-lookup"><span data-stu-id="21a65-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="21a65-120">Naslouchací procesy identifikované jako sdílené naslouchací procesy lze přidat do zdrojů nebo trasování podle názvu.</span><span class="sxs-lookup"><span data-stu-id="21a65-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="21a65-121">\<> zdrojů</span><span class="sxs-lookup"><span data-stu-id="21a65-121">\<sources></span></span>](sources-element.md)|<span data-ttu-id="21a65-122">Určuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="21a65-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="21a65-123">\<switches></span><span class="sxs-lookup"><span data-stu-id="21a65-123">\<switches></span></span>](switches-element.md)|<span data-ttu-id="21a65-124">Obsahuje přepínače trasování a úrovně, kde jsou nastaveny přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="21a65-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="21a65-125">\<trace></span><span class="sxs-lookup"><span data-stu-id="21a65-125">\<trace></span></span>](trace-element.md)|<span data-ttu-id="21a65-126">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="21a65-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21a65-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="21a65-127">Parent Elements</span></span>  
  
|<span data-ttu-id="21a65-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="21a65-128">Element</span></span>|<span data-ttu-id="21a65-129">Popis</span><span class="sxs-lookup"><span data-stu-id="21a65-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="21a65-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21a65-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="21a65-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="21a65-131">Example</span></span>  
 <span data-ttu-id="21a65-132">Následující příklad ukazuje, jak vložit přepínač trasování a naslouchací proces trasování v rámci  **\<prvku System. Diagnostic >** .</span><span class="sxs-lookup"><span data-stu-id="21a65-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="21a65-133">Přepínač trasování je nastaven <xref:System.Diagnostics.TraceLevel> na úroveň. `General`</span><span class="sxs-lookup"><span data-stu-id="21a65-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="21a65-134">Naslouchací proces `myListener` trasování vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="21a65-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21a65-135">V .NET Framework verze 2,0 můžete použít text a zadat hodnotu pro přepínač.</span><span class="sxs-lookup"><span data-stu-id="21a65-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="21a65-136">Například `true` můžete zadat <xref:System.Diagnostics.BooleanSwitch> pro nebo použít text představující <xref:System.Diagnostics.TraceSwitch>hodnotu výčtu, například `Error` pro.</span><span class="sxs-lookup"><span data-stu-id="21a65-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="21a65-137">Čára `<add name="myTraceSwitch" value="Error" />` je`<add name="myTraceSwitch" value="1" />`ekvivalentem.</span><span class="sxs-lookup"><span data-stu-id="21a65-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21a65-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21a65-138">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="21a65-139">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="21a65-139">Trace and Debug Settings Schema</span></span>](index.md)
