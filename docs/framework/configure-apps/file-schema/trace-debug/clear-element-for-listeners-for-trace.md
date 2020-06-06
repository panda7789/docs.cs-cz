---
title: <clear>Element pro <listeners> pro<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 905dad8274fede80f4809ff3c7a014049f9df450
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153539"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="3c182-102">\<clear>Element pro \<listeners> pro\<trace></span><span class="sxs-lookup"><span data-stu-id="3c182-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="3c182-103">Vymaže `Listeners` kolekci pro Trace.</span><span class="sxs-lookup"><span data-stu-id="3c182-103">Clears the `Listeners` collection for trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="3c182-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c182-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c182-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3c182-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3c182-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3c182-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c182-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3c182-107">Attributes</span></span>  
 <span data-ttu-id="3c182-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="3c182-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3c182-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3c182-109">Child Elements</span></span>  
 <span data-ttu-id="3c182-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="3c182-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c182-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3c182-111">Parent Elements</span></span>  
  
|<span data-ttu-id="3c182-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="3c182-112">Element</span></span>|<span data-ttu-id="3c182-113">Description</span><span class="sxs-lookup"><span data-stu-id="3c182-113">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3c182-114">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3c182-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3c182-115">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="3c182-115">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="3c182-116">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="3c182-116">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="3c182-117">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="3c182-117">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="3c182-118">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="3c182-118">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c182-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c182-119">Remarks</span></span>  
 <span data-ttu-id="3c182-120">`<clear>`Element odebere všechny naslouchací procesy z `Listeners` kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="3c182-120">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="3c182-121">Element lze použít `<clear>` před použitím `<add>` prvku, aby bylo jisté, že v kolekci nejsou žádné další aktivní naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="3c182-121">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="3c182-122">Kolekci můžete vymazat `Listeners` programově voláním <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> metody pro <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> vlastnost ( `System.Diagnostics.Trace.Listeners.Clear()` ).</span><span class="sxs-lookup"><span data-stu-id="3c182-122">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="3c182-123">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="3c182-123">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c182-124">`<clear>`Prvek odebere <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekce a změní chování <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> metod,, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3c182-124">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="3c182-125">Volání `Assert` metody nebo `Fail` obvykle vede k zobrazení okna se zprávou.</span><span class="sxs-lookup"><span data-stu-id="3c182-125">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="3c182-126">Okno se zprávou se ale nezobrazí, pokud není <xref:System.Diagnostics.DefaultTraceListener> v `Listeners` kolekci.</span><span class="sxs-lookup"><span data-stu-id="3c182-126">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c182-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c182-127">Example</span></span>  
 <span data-ttu-id="3c182-128">Následující příklad ukazuje, jak použít `<clear>` element před použitím `<add>` elementu pro přidání naslouchacího procesu `console` do `Listeners` kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="3c182-128">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3c182-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c182-129">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="3c182-130">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="3c182-130">Trace and Debug Settings Schema</span></span>](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="3c182-131">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="3c182-131">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
