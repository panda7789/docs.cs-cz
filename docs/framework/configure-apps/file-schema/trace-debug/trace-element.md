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
ms.openlocfilehash: 02fd794eb7b7b7f46f7f7bc4e43036cb4a4758ed
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699173"
---
# <a name="trace-element"></a><span data-ttu-id="32e71-102">@no__t – element > 0trace</span><span class="sxs-lookup"><span data-stu-id="32e71-102">\<trace> Element</span></span>
<span data-ttu-id="32e71-103">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="32e71-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[<span data-ttu-id="32e71-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="32e71-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="32e71-105">&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="32e71-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="32e71-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<trace >**</span><span class="sxs-lookup"><span data-stu-id="32e71-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32e71-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32e71-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32e71-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="32e71-108">Attributes and Elements</span></span>  
 <span data-ttu-id="32e71-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="32e71-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32e71-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="32e71-110">Attributes</span></span>  
  
|<span data-ttu-id="32e71-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="32e71-111">Attribute</span></span>|<span data-ttu-id="32e71-112">Popis</span><span class="sxs-lookup"><span data-stu-id="32e71-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="32e71-113">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="32e71-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="32e71-114">Určuje, zda naslouchací proces trasování po každé operaci zápisu automaticky vyprázdní výstupní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="32e71-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="32e71-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="32e71-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="32e71-116">Určuje počet mezer, které mají být odsazeny.</span><span class="sxs-lookup"><span data-stu-id="32e71-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="32e71-117">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="32e71-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="32e71-118">Určuje, zda má být použit globální zámek.</span><span class="sxs-lookup"><span data-stu-id="32e71-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="32e71-119">AutoFlush – atribut</span><span class="sxs-lookup"><span data-stu-id="32e71-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="32e71-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="32e71-120">Value</span></span>|<span data-ttu-id="32e71-121">Popis</span><span class="sxs-lookup"><span data-stu-id="32e71-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="32e71-122">Nevyprázdní výstupní vyrovnávací paměť automaticky.</span><span class="sxs-lookup"><span data-stu-id="32e71-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="32e71-123">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="32e71-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="32e71-124">Automaticky vyprázdní výstupní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="32e71-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="32e71-125">useGlobalLock – atribut</span><span class="sxs-lookup"><span data-stu-id="32e71-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="32e71-126">Hodnota</span><span class="sxs-lookup"><span data-stu-id="32e71-126">Value</span></span>|<span data-ttu-id="32e71-127">Popis</span><span class="sxs-lookup"><span data-stu-id="32e71-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="32e71-128">Nepoužívá globální zámek, pokud naslouchací proces je bezpečný pro přístup z více vláken; v opačném případě používá globální zámek.</span><span class="sxs-lookup"><span data-stu-id="32e71-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="32e71-129">Používá globální zámek bez ohledu na to, zda je naslouchací proces bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="32e71-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="32e71-130">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="32e71-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32e71-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="32e71-131">Child Elements</span></span>  
  
|<span data-ttu-id="32e71-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="32e71-132">Element</span></span>|<span data-ttu-id="32e71-133">Popis</span><span class="sxs-lookup"><span data-stu-id="32e71-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32e71-134">@no__t – 1listeners ></span><span class="sxs-lookup"><span data-stu-id="32e71-134">\<listeners></span></span>](listeners-element-for-trace.md)|<span data-ttu-id="32e71-135">Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy.</span><span class="sxs-lookup"><span data-stu-id="32e71-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32e71-136">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="32e71-136">Parent Elements</span></span>  
  
|<span data-ttu-id="32e71-137">Prvek</span><span class="sxs-lookup"><span data-stu-id="32e71-137">Element</span></span>|<span data-ttu-id="32e71-138">Popis</span><span class="sxs-lookup"><span data-stu-id="32e71-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="32e71-139">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32e71-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="32e71-140">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="32e71-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="32e71-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="32e71-141">Example</span></span>  
 <span data-ttu-id="32e71-142">Následující příklad ukazuje způsob použití prvku `<trace>` pro přidání naslouchacího procesu `MyListener` do kolekce `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="32e71-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="32e71-143">`MyListener` vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="32e71-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="32e71-144">Atribut `useGlobalLock` je nastaven na hodnotu `false`, což způsobí, že globální zámek nebude použit, pokud je naslouchací proces trasování bezpečný pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="32e71-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="32e71-145">Atribut `autoflush` je nastaven na hodnotu `true`, což způsobí, že naslouchací proces trasování zapisuje do souboru bez ohledu na to, zda je volána metoda <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="32e71-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="32e71-146">Atribut `indentsize` je nastaven na hodnotu 0 (nula), což způsobí, že naslouchací proces odsadí nula mezer při volání metody <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="32e71-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32e71-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32e71-147">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="32e71-148">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="32e71-148">Trace and Debug Settings Schema</span></span>](index.md)
