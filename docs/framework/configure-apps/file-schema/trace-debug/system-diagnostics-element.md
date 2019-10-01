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
ms.openlocfilehash: dc05c46cb1ba74baceaaeadc2959a6889faf19c9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699198"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="4d98a-102">\<system. Diagnostics – > – element</span><span class="sxs-lookup"><span data-stu-id="4d98a-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="4d98a-103">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="4d98a-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[<span data-ttu-id="4d98a-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="4d98a-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="4d98a-105">&nbsp; @ no__t-1 **\<system. diagnostics >**</span><span class="sxs-lookup"><span data-stu-id="4d98a-105">&nbsp;&nbsp;**\<system.diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d98a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d98a-106">Syntax</span></span>  
  
```xml  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d98a-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4d98a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4d98a-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4d98a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d98a-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="4d98a-109">Attributes</span></span>  
 <span data-ttu-id="4d98a-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="4d98a-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4d98a-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4d98a-111">Child Elements</span></span>  
  
|<span data-ttu-id="4d98a-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="4d98a-112">Element</span></span>|<span data-ttu-id="4d98a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4d98a-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d98a-114">@no__t – 1assert ></span><span class="sxs-lookup"><span data-stu-id="4d98a-114">\<assert></span></span>](assert-element.md)|<span data-ttu-id="4d98a-115">Určuje, zda se má při volání metody <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> zobrazit okno se zprávou; Určuje také název souboru, do kterého se mají zapisovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="4d98a-115">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="4d98a-116">@no__t – 1performanceCounters ></span><span class="sxs-lookup"><span data-stu-id="4d98a-116">\<performanceCounters></span></span>](performancecounters-element.md)|<span data-ttu-id="4d98a-117">Určuje velikost globální paměti sdílené čítači výkonu.</span><span class="sxs-lookup"><span data-stu-id="4d98a-117">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="4d98a-118">@no__t – 1sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="4d98a-118">\<sharedListeners></span></span>](sharedlisteners-element.md)|<span data-ttu-id="4d98a-119">Obsahuje naslouchací procesy, na které může odkazovat jakýkoliv element source nebo Trace.</span><span class="sxs-lookup"><span data-stu-id="4d98a-119">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="4d98a-120">Naslouchací procesy identifikované jako sdílené naslouchací procesy lze přidat do zdrojů nebo trasování podle názvu.</span><span class="sxs-lookup"><span data-stu-id="4d98a-120">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[<span data-ttu-id="4d98a-121">@no__t – 1sources ></span><span class="sxs-lookup"><span data-stu-id="4d98a-121">\<sources></span></span>](sources-element.md)|<span data-ttu-id="4d98a-122">Určuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="4d98a-122">Specifies trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="4d98a-123">@no__t – 1switches ></span><span class="sxs-lookup"><span data-stu-id="4d98a-123">\<switches></span></span>](switches-element.md)|<span data-ttu-id="4d98a-124">Obsahuje přepínače trasování a úrovně, kde jsou nastaveny přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="4d98a-124">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[<span data-ttu-id="4d98a-125">@no__t – 1trace ></span><span class="sxs-lookup"><span data-stu-id="4d98a-125">\<trace></span></span>](trace-element.md)|<span data-ttu-id="4d98a-126">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="4d98a-126">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d98a-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4d98a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4d98a-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="4d98a-128">Element</span></span>|<span data-ttu-id="4d98a-129">Popis</span><span class="sxs-lookup"><span data-stu-id="4d98a-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4d98a-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4d98a-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4d98a-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d98a-131">Example</span></span>  
 <span data-ttu-id="4d98a-132">Následující příklad ukazuje, jak vložit přepínač trasování a naslouchací proces trasování v rámci prvku **\<System. diagnostics >** .</span><span class="sxs-lookup"><span data-stu-id="4d98a-132">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="4d98a-133">Přepínač trasování `General` je nastaven na úroveň <xref:System.Diagnostics.TraceLevel>.</span><span class="sxs-lookup"><span data-stu-id="4d98a-133">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="4d98a-134">Naslouchací proces trasování `myListener` vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="4d98a-134">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d98a-135">V .NET Framework verze 2,0 můžete použít text a zadat hodnotu pro přepínač.</span><span class="sxs-lookup"><span data-stu-id="4d98a-135">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="4d98a-136">Můžete například zadat `true` pro <xref:System.Diagnostics.BooleanSwitch> nebo použít text reprezentující hodnotu výčtu, jako je například `Error` pro <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="4d98a-136">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="4d98a-137">Řádek `<add name="myTraceSwitch" value="Error" />` je ekvivalentem `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="4d98a-137">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4d98a-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d98a-138">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="4d98a-139">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="4d98a-139">Trace and Debug Settings Schema</span></span>](index.md)
