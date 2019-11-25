---
title: <remove> element pro <listeners> pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 75db45d4e868ce88e030ec6a43c8bdaf788a1102
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088857"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="22e01-102">\<odebrat > element pro \<naslouchací proces > pro \<zdrojového ></span><span class="sxs-lookup"><span data-stu-id="22e01-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="22e01-103">Odebere naslouchací proces z kolekce `Listeners` pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="22e01-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="22e01-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="22e01-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="22e01-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="22e01-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="22e01-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zdrojů >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="22e01-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="22e01-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zdroj >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="22e01-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="22e01-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Listeners**](listeners-element-for-source.md) ></span><span class="sxs-lookup"><span data-stu-id="22e01-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="22e01-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**</span><span class="sxs-lookup"><span data-stu-id="22e01-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="22e01-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22e01-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22e01-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="22e01-111">Attributes and Elements</span></span>  
 <span data-ttu-id="22e01-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="22e01-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22e01-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="22e01-113">Attributes</span></span>  
  
|<span data-ttu-id="22e01-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="22e01-114">Attribute</span></span>|<span data-ttu-id="22e01-115">Popis</span><span class="sxs-lookup"><span data-stu-id="22e01-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="22e01-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="22e01-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="22e01-117">Název naslouchacího procesu, který se má odebrat z kolekce `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="22e01-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22e01-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="22e01-118">Child Elements</span></span>  
 <span data-ttu-id="22e01-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="22e01-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22e01-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="22e01-120">Parent Elements</span></span>  
  
|<span data-ttu-id="22e01-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="22e01-121">Element</span></span>|<span data-ttu-id="22e01-122">Popis</span><span class="sxs-lookup"><span data-stu-id="22e01-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="22e01-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="22e01-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="22e01-124">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="22e01-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="22e01-125">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="22e01-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="22e01-126">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="22e01-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="22e01-127">Určuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="22e01-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22e01-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22e01-128">Remarks</span></span>  
 <span data-ttu-id="22e01-129">Element `<remove>` Odebere zadaný naslouchací proces z kolekce `Listeners` pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="22e01-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="22e01-130">Můžete odebrat prvek z kolekce `Listeners` pro zdroj trasování programově voláním metody <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> ve vlastnosti <xref:System.Diagnostics.TraceSource.Listeners%2A> instance <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="22e01-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="22e01-131">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="22e01-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22e01-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="22e01-132">Example</span></span>  
 <span data-ttu-id="22e01-133">Následující příklad ukazuje, jak použít prvek `<remove>` před použitím elementu `<add>` k přidání `console` naslouchacího procesu do kolekce `Listeners` pro `TraceSourceApp`zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="22e01-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22e01-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22e01-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="22e01-135">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="22e01-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="22e01-136">\<vymazat ></span><span class="sxs-lookup"><span data-stu-id="22e01-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="22e01-137">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="22e01-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
