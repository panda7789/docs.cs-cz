---
title: <clear> element pro <listeners> pro <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 049b8e7ed17633c0f34b062915afaf719927dad6
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088918"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="555d9-102">\<Clear > elementu pro \<naslouchací proces > pro \<trace ></span><span class="sxs-lookup"><span data-stu-id="555d9-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="555d9-103">Vymaže kolekci `Listeners` pro trasování.</span><span class="sxs-lookup"><span data-stu-id="555d9-103">Clears the `Listeners` collection for trace.</span></span>  

<span data-ttu-id="555d9-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="555d9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="555d9-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="555d9-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="555d9-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="555d9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="555d9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<naslouchacího procesu >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="555d9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="555d9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vymazat >**</span><span class="sxs-lookup"><span data-stu-id="555d9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="555d9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="555d9-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="555d9-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="555d9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="555d9-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="555d9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="555d9-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="555d9-112">Attributes</span></span>  
 <span data-ttu-id="555d9-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="555d9-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="555d9-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="555d9-114">Child Elements</span></span>  
 <span data-ttu-id="555d9-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="555d9-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="555d9-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="555d9-116">Parent Elements</span></span>  
  
|<span data-ttu-id="555d9-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="555d9-117">Element</span></span>|<span data-ttu-id="555d9-118">Popis</span><span class="sxs-lookup"><span data-stu-id="555d9-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="555d9-119">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="555d9-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="555d9-120">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="555d9-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="555d9-121">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="555d9-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="555d9-122">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="555d9-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="555d9-123">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="555d9-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="555d9-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="555d9-124">Remarks</span></span>  
 <span data-ttu-id="555d9-125">Element `<clear>` odebere všechny naslouchací procesy z kolekce `Listeners` pro trasování.</span><span class="sxs-lookup"><span data-stu-id="555d9-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="555d9-126">Element `<clear>` lze použít před použitím elementu `<add>`, aby bylo jisté, že v kolekci nejsou žádné další aktivní naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="555d9-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="555d9-127">Kolekci `Listeners` lze odstranit programově voláním metody <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> na vlastnosti <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="555d9-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="555d9-128">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="555d9-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="555d9-129">Element `<clear>` odebere <xref:System.Diagnostics.DefaultTraceListener> z kolekce `Listeners`, přičemž upraví chování <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>ch metod.</span><span class="sxs-lookup"><span data-stu-id="555d9-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="555d9-130">Volání metody `Assert` nebo `Fail` obvykle vede k zobrazení okna se zprávou.</span><span class="sxs-lookup"><span data-stu-id="555d9-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="555d9-131">Okno se zprávou se ale nezobrazí, pokud <xref:System.Diagnostics.DefaultTraceListener> není v kolekci `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="555d9-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="555d9-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="555d9-132">Example</span></span>  
 <span data-ttu-id="555d9-133">Následující příklad ukazuje, jak použít prvek `<clear>` před použitím elementu `<add>` k přidání `console` naslouchacího procesu do kolekce `Listeners` pro trasování.</span><span class="sxs-lookup"><span data-stu-id="555d9-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="555d9-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="555d9-134">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="555d9-135">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="555d9-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="555d9-136">\<odebrat ></span><span class="sxs-lookup"><span data-stu-id="555d9-136">\<remove></span></span>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="555d9-137">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="555d9-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
