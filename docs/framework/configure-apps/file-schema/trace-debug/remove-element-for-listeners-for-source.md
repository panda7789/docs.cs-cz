---
title: <remove> element pro <listeners> pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 4a11308278f755ec8271477352d91d8797d105c5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699490"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="177d3-102">> element \<remove pro \<listeners > pro \<source ></span><span class="sxs-lookup"><span data-stu-id="177d3-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="177d3-103">Odebere naslouchací proces z kolekce `Listeners` pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="177d3-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
[<span data-ttu-id="177d3-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="177d3-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="177d3-105">&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="177d3-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="177d3-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sources >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="177d3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>  
<span data-ttu-id="177d3-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<source >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="177d3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>  
<span data-ttu-id="177d3-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0listeners >** ](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="177d3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>  
<span data-ttu-id="177d3-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1remove >**</span><span class="sxs-lookup"><span data-stu-id="177d3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="177d3-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="177d3-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="177d3-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="177d3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="177d3-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="177d3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="177d3-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="177d3-113">Attributes</span></span>  
  
|<span data-ttu-id="177d3-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="177d3-114">Attribute</span></span>|<span data-ttu-id="177d3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="177d3-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="177d3-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="177d3-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="177d3-117">Název naslouchacího procesu, který se má odebrat z kolekce `Listeners`</span><span class="sxs-lookup"><span data-stu-id="177d3-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="177d3-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="177d3-118">Child Elements</span></span>  
 <span data-ttu-id="177d3-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="177d3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="177d3-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="177d3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="177d3-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="177d3-121">Element</span></span>|<span data-ttu-id="177d3-122">Popis</span><span class="sxs-lookup"><span data-stu-id="177d3-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="177d3-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="177d3-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="177d3-124">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="177d3-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="177d3-125">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="177d3-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="177d3-126">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="177d3-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="177d3-127">Určuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="177d3-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="177d3-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="177d3-128">Remarks</span></span>  
 <span data-ttu-id="177d3-129">Element `<remove>` odebere zadaného naslouchacího procesu z kolekce `Listeners` pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="177d3-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="177d3-130">Můžete odebrat prvek z kolekce `Listeners` pro zdroj trasování programově voláním metody <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> u vlastnosti <xref:System.Diagnostics.TraceSource.Listeners%2A> instance <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="177d3-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="177d3-131">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="177d3-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="177d3-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="177d3-132">Example</span></span>  
 <span data-ttu-id="177d3-133">Následující příklad ukazuje, jak použít prvek `<remove>` před použitím prvku `<add>` pro přidání naslouchacího procesu `console` do kolekce `Listeners` pro zdroj trasování `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="177d3-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="177d3-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="177d3-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="177d3-135">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="177d3-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="177d3-136">@no__t – 1clear ></span><span class="sxs-lookup"><span data-stu-id="177d3-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="177d3-137">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="177d3-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
