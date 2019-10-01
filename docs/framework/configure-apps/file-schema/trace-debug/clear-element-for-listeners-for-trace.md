---
title: <clear> element pro <listeners> pro <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 0361580724351f8f42d058d5e20354e3335bac2f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699370"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="4a202-102">> element \<clear pro \<listeners > pro \<trace ></span><span class="sxs-lookup"><span data-stu-id="4a202-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="4a202-103">Vymaže kolekci `Listeners` pro trasování.</span><span class="sxs-lookup"><span data-stu-id="4a202-103">Clears the `Listeners` collection for trace.</span></span>  
  
[<span data-ttu-id="4a202-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="4a202-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="4a202-105">&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="4a202-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="4a202-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="4a202-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="4a202-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="4a202-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>  
<span data-ttu-id="4a202-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="4a202-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a202-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a202-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a202-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4a202-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4a202-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4a202-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a202-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4a202-112">Attributes</span></span>  
 <span data-ttu-id="4a202-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="4a202-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4a202-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4a202-114">Child Elements</span></span>  
 <span data-ttu-id="4a202-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="4a202-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a202-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4a202-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4a202-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="4a202-117">Element</span></span>|<span data-ttu-id="4a202-118">Popis</span><span class="sxs-lookup"><span data-stu-id="4a202-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4a202-119">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4a202-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4a202-120">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="4a202-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="4a202-121">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="4a202-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="4a202-122">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="4a202-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="4a202-123">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="4a202-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a202-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a202-124">Remarks</span></span>  
 <span data-ttu-id="4a202-125">Element `<clear>` odebere všechny naslouchací procesy z kolekce `Listeners` pro trasování.</span><span class="sxs-lookup"><span data-stu-id="4a202-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="4a202-126">Element `<clear>` lze použít před použitím prvku `<add>`, aby bylo jisté, že v kolekci nejsou žádné další aktivní naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="4a202-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="4a202-127">Kolekci `Listeners` můžete programově vymazat voláním metody <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> na vlastnosti <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="4a202-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="4a202-128">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="4a202-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a202-129">Element `<clear>` odebere <xref:System.Diagnostics.DefaultTraceListener> z kolekce `Listeners` a změní chování metod <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a202-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="4a202-130">Volání metody `Assert` nebo `Fail` obvykle vede k zobrazení okna se zprávou.</span><span class="sxs-lookup"><span data-stu-id="4a202-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="4a202-131">Okno se zprávou se ale nezobrazí, pokud <xref:System.Diagnostics.DefaultTraceListener> není v kolekci `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="4a202-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a202-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="4a202-132">Example</span></span>  
 <span data-ttu-id="4a202-133">Následující příklad ukazuje, jak použít prvek `<clear>` před použitím prvku `<add>` pro přidání naslouchacího procesu `console` do kolekce `Listeners` pro trasování.</span><span class="sxs-lookup"><span data-stu-id="4a202-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4a202-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a202-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="4a202-135">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="4a202-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4a202-136">@no__t – 1remove ></span><span class="sxs-lookup"><span data-stu-id="4a202-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="4a202-137">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="4a202-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
