---
title: Element <trace>
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
ms.openlocfilehash: 7d8a989219d84e8604e767456c84c0092bc73b22
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153163"
---
# <a name="trace-element"></a><span data-ttu-id="29c4e-102">Element \<trace></span><span class="sxs-lookup"><span data-stu-id="29c4e-102">\<trace> Element</span></span>
<span data-ttu-id="29c4e-103">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="29c4e-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
## <a name="syntax"></a><span data-ttu-id="29c4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29c4e-104">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29c4e-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="29c4e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="29c4e-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="29c4e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29c4e-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="29c4e-107">Attributes</span></span>  
  
|<span data-ttu-id="29c4e-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="29c4e-108">Attribute</span></span>|<span data-ttu-id="29c4e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="29c4e-109">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="29c4e-110">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="29c4e-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="29c4e-111">Určuje, zda naslouchací proces trasování po každé operaci zápisu automaticky vyprázdní výstupní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="29c4e-111">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="29c4e-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="29c4e-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="29c4e-113">Určuje počet mezer, které mají být odsazeny.</span><span class="sxs-lookup"><span data-stu-id="29c4e-113">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="29c4e-114">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="29c4e-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="29c4e-115">Určuje, zda má být použit globální zámek.</span><span class="sxs-lookup"><span data-stu-id="29c4e-115">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="29c4e-116">AutoFlush – atribut</span><span class="sxs-lookup"><span data-stu-id="29c4e-116">autoflush Attribute</span></span>  
  
|<span data-ttu-id="29c4e-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="29c4e-117">Value</span></span>|<span data-ttu-id="29c4e-118">Description</span><span class="sxs-lookup"><span data-stu-id="29c4e-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="29c4e-119">Nevyprázdní výstupní vyrovnávací paměť automaticky.</span><span class="sxs-lookup"><span data-stu-id="29c4e-119">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="29c4e-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="29c4e-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="29c4e-121">Automaticky vyprázdní výstupní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="29c4e-121">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="29c4e-122">useGlobalLock – atribut</span><span class="sxs-lookup"><span data-stu-id="29c4e-122">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="29c4e-123">Hodnota</span><span class="sxs-lookup"><span data-stu-id="29c4e-123">Value</span></span>|<span data-ttu-id="29c4e-124">Description</span><span class="sxs-lookup"><span data-stu-id="29c4e-124">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="29c4e-125">Nepoužívá globální zámek, pokud naslouchací proces je bezpečný pro přístup z více vláken; v opačném případě používá globální zámek.</span><span class="sxs-lookup"><span data-stu-id="29c4e-125">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="29c4e-126">Používá globální zámek bez ohledu na to, zda je naslouchací proces bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="29c4e-126">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="29c4e-127">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="29c4e-127">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29c4e-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="29c4e-128">Child Elements</span></span>  
  
|<span data-ttu-id="29c4e-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="29c4e-129">Element</span></span>|<span data-ttu-id="29c4e-130">Description</span><span class="sxs-lookup"><span data-stu-id="29c4e-130">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="29c4e-131">Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy.</span><span class="sxs-lookup"><span data-stu-id="29c4e-131">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29c4e-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="29c4e-132">Parent Elements</span></span>  
  
|<span data-ttu-id="29c4e-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="29c4e-133">Element</span></span>|<span data-ttu-id="29c4e-134">Description</span><span class="sxs-lookup"><span data-stu-id="29c4e-134">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="29c4e-135">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29c4e-135">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="29c4e-136">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="29c4e-136">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="29c4e-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="29c4e-137">Example</span></span>  
 <span data-ttu-id="29c4e-138">Následující příklad ukazuje, jak použít `<trace>` element k přidání naslouchacího procesu `MyListener` do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="29c4e-138">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="29c4e-139">`MyListener`Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="29c4e-139">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="29c4e-140">`useGlobalLock`Atribut je nastaven na `false` , což způsobí, že globální zámek nebude použit, pokud je naslouchací proces trasování bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="29c4e-140">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="29c4e-141">`autoflush`Atribut je nastaven na `true` , což způsobí, že naslouchací proces trasování zapisuje do souboru bez ohledu na to, zda <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> je metoda volána.</span><span class="sxs-lookup"><span data-stu-id="29c4e-141">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="29c4e-142">`indentsize`Atribut je nastaven na hodnotu 0 (nula), což způsobí, že naslouchací proces při volání metody odsadí nula mezer <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="29c4e-142">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="29c4e-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="29c4e-143">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="29c4e-144">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="29c4e-144">Trace and Debug Settings Schema</span></span>](index.md)
