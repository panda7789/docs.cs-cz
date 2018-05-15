---
title: '&lt;Vymazat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;trasování&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1705ed7cc847d60ecf8b42f4615d77f2cc569e21
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="128ea-102">&lt;Vymazat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;trasování&gt;</span><span class="sxs-lookup"><span data-stu-id="128ea-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="128ea-103">Vymaže `Listeners` kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="128ea-103">Clears the `Listeners` collection for trace.</span></span>  
  
 <span data-ttu-id="128ea-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="128ea-104">\<configuration></span></span>  
<span data-ttu-id="128ea-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="128ea-105">\<system.diagnostics></span></span>  
<span data-ttu-id="128ea-106">\<trasování ></span><span class="sxs-lookup"><span data-stu-id="128ea-106">\<trace></span></span>  
<span data-ttu-id="128ea-107">\<moduly pro naslouchání ></span><span class="sxs-lookup"><span data-stu-id="128ea-107">\<listeners></span></span>  
<span data-ttu-id="128ea-108">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="128ea-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="128ea-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="128ea-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="128ea-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="128ea-110">Attributes and Elements</span></span>  
 <span data-ttu-id="128ea-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="128ea-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="128ea-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="128ea-112">Attributes</span></span>  
 <span data-ttu-id="128ea-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="128ea-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="128ea-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="128ea-114">Child Elements</span></span>  
 <span data-ttu-id="128ea-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="128ea-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="128ea-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="128ea-116">Parent Elements</span></span>  
  
|<span data-ttu-id="128ea-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="128ea-117">Element</span></span>|<span data-ttu-id="128ea-118">Popis</span><span class="sxs-lookup"><span data-stu-id="128ea-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="128ea-119">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="128ea-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="128ea-120">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="128ea-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="128ea-121">Obsahuje naslouchací procesy, které shromažďování, ukládání a směrovat trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="128ea-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="128ea-122">Obsahuje naslouchací procesy, které shromažďování, ukládání a směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="128ea-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="128ea-123">Moduly pro naslouchání přesměrujte výstup trasování do příslušné cílové.</span><span class="sxs-lookup"><span data-stu-id="128ea-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="128ea-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="128ea-124">Remarks</span></span>  
 <span data-ttu-id="128ea-125">`<clear>` Element odebere všechny moduly pro naslouchání z `Listeners` kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="128ea-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="128ea-126">Můžete použít `<clear>` element před použitím `<add>` elementu, který chcete být jisti, nejsou žádné aktivní naslouchací procesy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="128ea-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="128ea-127">Můžete vymazat `Listeners` kolekce programově zavoláním <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> metodu <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> vlastnost (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="128ea-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="128ea-128">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="128ea-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="128ea-129">`<clear>` Odebere element <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekce, změna chování <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="128ea-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="128ea-130">Volání metody `Assert` nebo `Fail` metoda obvykle výsledkem zobrazení okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="128ea-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="128ea-131">Do pole zpráva se ale nezobrazí, pokud <xref:System.Diagnostics.DefaultTraceListener> není v `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="128ea-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="128ea-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="128ea-132">Example</span></span>  
 <span data-ttu-id="128ea-133">Následující příklad ukazuje, jak používat `<clear>` element před použitím `<add>` elementu, který chcete přidat naslouchací proces `console` k `Listeners` kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="128ea-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="128ea-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="128ea-134">See Also</span></span>  
 <xref:System.Diagnostics.Trace.Listeners%2A>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="128ea-135">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="128ea-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="128ea-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="128ea-136">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)  
 [<span data-ttu-id="128ea-137">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="128ea-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
