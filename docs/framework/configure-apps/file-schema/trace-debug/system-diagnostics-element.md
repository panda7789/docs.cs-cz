---
title: <element System. Diagnostics>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics
helpviewer_keywords:
- <system.diagnostics> element
- system.diagnostics element
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
ms.openlocfilehash: 4f831592d7d178276b1625e1ef7d8512085342af
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153204"
---
# <a name="systemdiagnostics-element"></a><span data-ttu-id="9c843-102">Element \<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="9c843-102">\<system.diagnostics> Element</span></span>
<span data-ttu-id="9c843-103">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="9c843-103">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="9c843-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c843-104">Syntax</span></span>  
  
```xml  
<system.diagnostics>
</system.diagnostics>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c843-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9c843-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9c843-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9c843-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c843-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="9c843-107">Attributes</span></span>  
 <span data-ttu-id="9c843-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="9c843-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9c843-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9c843-109">Child Elements</span></span>  
  
|<span data-ttu-id="9c843-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="9c843-110">Element</span></span>|<span data-ttu-id="9c843-111">Description</span><span class="sxs-lookup"><span data-stu-id="9c843-111">Description</span></span>|  
|-------------|-----------------|  
|[\<assert>](assert-element.md)|<span data-ttu-id="9c843-112">Určuje, zda se má při volání metody zobrazit okno se zprávou <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> . určuje také název souboru, do kterého budou zapsány zprávy.</span><span class="sxs-lookup"><span data-stu-id="9c843-112">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[\<performanceCounters>](performancecounters-element.md)|<span data-ttu-id="9c843-113">Určuje velikost globální paměti sdílené čítači výkonu.</span><span class="sxs-lookup"><span data-stu-id="9c843-113">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[\<sharedListeners>](sharedlisteners-element.md)|<span data-ttu-id="9c843-114">Obsahuje naslouchací procesy, na které může odkazovat jakýkoliv element source nebo Trace.</span><span class="sxs-lookup"><span data-stu-id="9c843-114">Contains listeners that any source or trace element can reference.</span></span> <span data-ttu-id="9c843-115">Naslouchací procesy identifikované jako sdílené naslouchací procesy lze přidat do zdrojů nebo trasování podle názvu.</span><span class="sxs-lookup"><span data-stu-id="9c843-115">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>|  
|[\<sources>](sources-element.md)|<span data-ttu-id="9c843-116">Určuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="9c843-116">Specifies trace sources that initiate tracing messages.</span></span>|  
|[\<switches>](switches-element.md)|<span data-ttu-id="9c843-117">Obsahuje přepínače trasování a úrovně, kde jsou nastaveny přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="9c843-117">Contains trace switches and the levels where the trace switches are set.</span></span>|  
|[\<trace>](trace-element.md)|<span data-ttu-id="9c843-118">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="9c843-118">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c843-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9c843-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9c843-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="9c843-120">Element</span></span>|<span data-ttu-id="9c843-121">Description</span><span class="sxs-lookup"><span data-stu-id="9c843-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9c843-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c843-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9c843-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="9c843-123">Example</span></span>  
 <span data-ttu-id="9c843-124">Následující příklad ukazuje, jak vložit přepínač trasování a naslouchací proces trasování uvnitř **\<system.diagnostics>** elementu.</span><span class="sxs-lookup"><span data-stu-id="9c843-124">The following example shows how to embed a trace switch and a trace listener inside the **\<system.diagnostics>** element.</span></span> <span data-ttu-id="9c843-125">`General`Přepínač trasování je nastaven na <xref:System.Diagnostics.TraceLevel> úroveň.</span><span class="sxs-lookup"><span data-stu-id="9c843-125">The `General` trace switch is set to the <xref:System.Diagnostics.TraceLevel> level.</span></span> <span data-ttu-id="9c843-126">Naslouchací proces trasování `myListener` vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="9c843-126">The trace listener `myListener` creates a file called `MyListener.log` and writes the output to the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c843-127">V .NET Framework verze 2,0 můžete použít text a zadat hodnotu pro přepínač.</span><span class="sxs-lookup"><span data-stu-id="9c843-127">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="9c843-128">Například můžete zadat `true` pro <xref:System.Diagnostics.BooleanSwitch> nebo použít text představující hodnotu výčtu, například `Error` pro <xref:System.Diagnostics.TraceSwitch> .</span><span class="sxs-lookup"><span data-stu-id="9c843-128">For example, you can specify `true` for a <xref:System.Diagnostics.BooleanSwitch> or use the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="9c843-129">Čára `<add name="myTraceSwitch" value="Error" />` je ekvivalentem `<add name="myTraceSwitch" value="1" />` .</span><span class="sxs-lookup"><span data-stu-id="9c843-129">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9c843-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c843-130">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="9c843-131">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="9c843-131">Trace and Debug Settings Schema</span></span>](index.md)
