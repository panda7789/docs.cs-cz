---
title: <clear>Element pro <listeners> pro<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 9816ba0f8e4ddd4c38537eb4e014a4240ff20407
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927174"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="7efe6-102">\<Clear > element pro \<naslouchací procesy > \<pro > trasování</span><span class="sxs-lookup"><span data-stu-id="7efe6-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="7efe6-103">`Listeners` Vymaže kolekci pro Trace.</span><span class="sxs-lookup"><span data-stu-id="7efe6-103">Clears the `Listeners` collection for trace.</span></span>  
  
 <span data-ttu-id="7efe6-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="7efe6-104">\<configuration></span></span>  
<span data-ttu-id="7efe6-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="7efe6-105">\<system.diagnostics></span></span>  
<span data-ttu-id="7efe6-106">\<> trasování</span><span class="sxs-lookup"><span data-stu-id="7efe6-106">\<trace></span></span>  
<span data-ttu-id="7efe6-107">\<> naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="7efe6-107">\<listeners></span></span>  
<span data-ttu-id="7efe6-108">\<Vymazat ></span><span class="sxs-lookup"><span data-stu-id="7efe6-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7efe6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7efe6-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7efe6-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7efe6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7efe6-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7efe6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7efe6-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7efe6-112">Attributes</span></span>  
 <span data-ttu-id="7efe6-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="7efe6-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7efe6-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7efe6-114">Child Elements</span></span>  
 <span data-ttu-id="7efe6-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="7efe6-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7efe6-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7efe6-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7efe6-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="7efe6-117">Element</span></span>|<span data-ttu-id="7efe6-118">Popis</span><span class="sxs-lookup"><span data-stu-id="7efe6-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7efe6-119">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7efe6-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="7efe6-120">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="7efe6-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="7efe6-121">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="7efe6-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="7efe6-122">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="7efe6-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="7efe6-123">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="7efe6-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7efe6-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7efe6-124">Remarks</span></span>  
 <span data-ttu-id="7efe6-125">Element odebere všechny naslouchací procesy `Listeners` z kolekce pro trasování. `<clear>`</span><span class="sxs-lookup"><span data-stu-id="7efe6-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="7efe6-126">`<clear>` Element lze použít před `<add>` použitím prvku, aby bylo jisté, že v kolekci nejsou žádné další aktivní naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="7efe6-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="7efe6-127">`Listeners` Kolekci můžete vymazat programově <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> voláním metody pro <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> vlastnost (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="7efe6-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="7efe6-128">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="7efe6-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7efe6-129">`<clear>` Prvek odebere<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> z kolekce`Listeners`a <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>změní chování metod<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>,,a. <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.DefaultTraceListener></span><span class="sxs-lookup"><span data-stu-id="7efe6-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="7efe6-130">Volání metody `Fail` nebo obvykle vede k zobrazení okna se zprávou. `Assert`</span><span class="sxs-lookup"><span data-stu-id="7efe6-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="7efe6-131">Okno se zprávou se ale nezobrazí, pokud <xref:System.Diagnostics.DefaultTraceListener> není `Listeners` v kolekci.</span><span class="sxs-lookup"><span data-stu-id="7efe6-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7efe6-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="7efe6-132">Example</span></span>  
 <span data-ttu-id="7efe6-133">Následující příklad ukazuje `<clear>` , jak použít element před `<add>` použitím elementu pro `Listeners` přidání naslouchacího procesu `console` do kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="7efe6-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7efe6-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7efe6-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="7efe6-135">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="7efe6-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7efe6-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="7efe6-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="7efe6-137">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="7efe6-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
