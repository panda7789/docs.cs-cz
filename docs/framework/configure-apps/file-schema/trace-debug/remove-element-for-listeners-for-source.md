---
title: "&lt;Odebrat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;zdroje&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6170c02296859d9c47e5288f287a4371d7cb0c56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="f3203-102">&lt;Odebrat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;zdroje&gt;</span><span class="sxs-lookup"><span data-stu-id="f3203-102">&lt;remove&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="f3203-103">Odebere naslouchací proces z `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="f3203-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="f3203-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="f3203-104">\<configuration></span></span>  
<span data-ttu-id="f3203-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="f3203-105">\<system.diagnostics></span></span>  
<span data-ttu-id="f3203-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="f3203-106">\<sources></span></span>  
<span data-ttu-id="f3203-107">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="f3203-107">\<source></span></span>  
<span data-ttu-id="f3203-108">\<moduly pro naslouchání ></span><span class="sxs-lookup"><span data-stu-id="f3203-108">\<listeners></span></span>  
<span data-ttu-id="f3203-109">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="f3203-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3203-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3203-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3203-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3203-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f3203-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3203-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3203-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3203-113">Attributes</span></span>  
  
|<span data-ttu-id="f3203-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="f3203-114">Attribute</span></span>|<span data-ttu-id="f3203-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f3203-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="f3203-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f3203-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="f3203-117">Název naslouchací proces odebrání `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="f3203-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3203-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3203-118">Child Elements</span></span>  
 <span data-ttu-id="f3203-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3203-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3203-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3203-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f3203-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3203-121">Element</span></span>|<span data-ttu-id="f3203-122">Popis</span><span class="sxs-lookup"><span data-stu-id="f3203-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f3203-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f3203-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f3203-124">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="f3203-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="f3203-125">Obsahuje trasování zdrojů, které zahájí trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="f3203-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="f3203-126">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="f3203-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="f3203-127">Určuje naslouchací procesy, které shromažďování, ukládání a směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="f3203-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3203-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3203-128">Remarks</span></span>  
 <span data-ttu-id="f3203-129">`<remove>` Element Odebere zadaný naslouchací proces z `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="f3203-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="f3203-130">Můžete odebrat element z `Listeners` kolekci pro zdroj trasování programově zavoláním <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> metodu <xref:System.Diagnostics.TraceSource.Listeners%2A> vlastnost <xref:System.Diagnostics.TraceSource> instance.</span><span class="sxs-lookup"><span data-stu-id="f3203-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="f3203-131">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="f3203-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3203-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3203-132">Example</span></span>  
 <span data-ttu-id="f3203-133">Následující příklad ukazuje, jak používat `<remove>` element před použitím `<add>` elementu, který chcete přidat naslouchací proces `console` k `Listeners` kolekci pro zdroj trasování `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="f3203-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3203-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3203-134">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource.Listeners%2A>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="f3203-135">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="f3203-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="f3203-136">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="f3203-136">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)  
 [<span data-ttu-id="f3203-137">Trasování – moduly naslouchání</span><span class="sxs-lookup"><span data-stu-id="f3203-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
