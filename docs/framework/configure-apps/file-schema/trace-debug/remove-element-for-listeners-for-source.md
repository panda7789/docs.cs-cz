---
title: <remove>Prvek <listeners> pro pro<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 657e6db2af9b99b3bbf03afc6aab02c58a830f2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153332"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="eb38d-102">\<odebrat> \<Element pro \<naslouchací> pro zdrojové></span><span class="sxs-lookup"><span data-stu-id="eb38d-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="eb38d-103">Odebere naslouchací proces z `Listeners` kolekce pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="eb38d-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="eb38d-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="eb38d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eb38d-105">&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="eb38d-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="eb38d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdroje>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="eb38d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="eb38d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdrojové>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="eb38d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="eb38d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<posluchači>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="eb38d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="eb38d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<odebrat>**</span><span class="sxs-lookup"><span data-stu-id="eb38d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="eb38d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb38d-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb38d-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eb38d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="eb38d-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eb38d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb38d-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="eb38d-113">Attributes</span></span>  
  
|<span data-ttu-id="eb38d-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="eb38d-114">Attribute</span></span>|<span data-ttu-id="eb38d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="eb38d-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="eb38d-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="eb38d-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="eb38d-117">Název naslouchací `Listeners` proces odebrat z kolekce.</span><span class="sxs-lookup"><span data-stu-id="eb38d-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb38d-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="eb38d-118">Child Elements</span></span>  
 <span data-ttu-id="eb38d-119">Žádné.</span><span class="sxs-lookup"><span data-stu-id="eb38d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb38d-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="eb38d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="eb38d-121">Element</span><span class="sxs-lookup"><span data-stu-id="eb38d-121">Element</span></span>|<span data-ttu-id="eb38d-122">Popis</span><span class="sxs-lookup"><span data-stu-id="eb38d-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="eb38d-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb38d-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="eb38d-124">Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="eb38d-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="eb38d-125">Obsahuje zdroje trasování, které iniciují tracing zprávy.</span><span class="sxs-lookup"><span data-stu-id="eb38d-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="eb38d-126">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="eb38d-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="eb38d-127">Určuje posluchače, kteří shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="eb38d-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb38d-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb38d-128">Remarks</span></span>  
 <span data-ttu-id="eb38d-129">Prvek `<remove>` odebere zadaný naslouchací `Listeners` proces z kolekce pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="eb38d-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="eb38d-130">Prvek můžete odebrat `Listeners` z kolekce pro zdroj trasování <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> programově <xref:System.Diagnostics.TraceSource.Listeners%2A> voláním <xref:System.Diagnostics.TraceSource> metody na vlastnost instance.</span><span class="sxs-lookup"><span data-stu-id="eb38d-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="eb38d-131">Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb38d-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb38d-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb38d-132">Example</span></span>  
 <span data-ttu-id="eb38d-133">Následující příklad ukazuje, jak `<remove>` použít prvek `<add>` před použitím `console` prvku `Listeners` k přidání naslouchací proces do kolekce pro zdroj `TraceSourceApp`trasování .</span><span class="sxs-lookup"><span data-stu-id="eb38d-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="eb38d-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb38d-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="eb38d-135">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="eb38d-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="eb38d-136">\<jasné></span><span class="sxs-lookup"><span data-stu-id="eb38d-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="eb38d-137">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="eb38d-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
