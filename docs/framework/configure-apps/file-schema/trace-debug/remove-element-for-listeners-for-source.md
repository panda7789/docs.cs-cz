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
ms.workload: dotnet
ms.openlocfilehash: b983c5eb80f958098b6991970559d077b97a0759
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="2e2d0-102">&lt;Odebrat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;zdroje&gt;</span><span class="sxs-lookup"><span data-stu-id="2e2d0-102">&lt;remove&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="2e2d0-103">Odebere naslouchací proces z `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="2e2d0-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="2e2d0-104">\<configuration></span></span>  
<span data-ttu-id="2e2d0-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="2e2d0-105">\<system.diagnostics></span></span>  
<span data-ttu-id="2e2d0-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="2e2d0-106">\<sources></span></span>  
<span data-ttu-id="2e2d0-107">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="2e2d0-107">\<source></span></span>  
<span data-ttu-id="2e2d0-108">\<moduly pro naslouchání ></span><span class="sxs-lookup"><span data-stu-id="2e2d0-108">\<listeners></span></span>  
<span data-ttu-id="2e2d0-109">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="2e2d0-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e2d0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e2d0-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e2d0-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2e2d0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2e2d0-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e2d0-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="2e2d0-113">Attributes</span></span>  
  
|<span data-ttu-id="2e2d0-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="2e2d0-114">Attribute</span></span>|<span data-ttu-id="2e2d0-115">Popis</span><span class="sxs-lookup"><span data-stu-id="2e2d0-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="2e2d0-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="2e2d0-117">Název naslouchací proces odebrání `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2e2d0-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2e2d0-118">Child Elements</span></span>  
 <span data-ttu-id="2e2d0-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="2e2d0-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2e2d0-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2e2d0-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2e2d0-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="2e2d0-121">Element</span></span>|<span data-ttu-id="2e2d0-122">Popis</span><span class="sxs-lookup"><span data-stu-id="2e2d0-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2e2d0-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2e2d0-124">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="2e2d0-125">Obsahuje trasování zdrojů, které zahájí trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="2e2d0-126">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="2e2d0-127">Určuje naslouchací procesy, které shromažďování, ukládání a směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e2d0-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e2d0-128">Remarks</span></span>  
 <span data-ttu-id="2e2d0-129">`<remove>` Element Odebere zadaný naslouchací proces z `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="2e2d0-130">Můžete odebrat element z `Listeners` kolekci pro zdroj trasování programově zavoláním <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> metodu <xref:System.Diagnostics.TraceSource.Listeners%2A> vlastnost <xref:System.Diagnostics.TraceSource> instance.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="2e2d0-131">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e2d0-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e2d0-132">Example</span></span>  
 <span data-ttu-id="2e2d0-133">Následující příklad ukazuje, jak používat `<remove>` element před použitím `<add>` elementu, který chcete přidat naslouchací proces `console` k `Listeners` kolekci pro zdroj trasování `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2e2d0-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e2d0-134">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource.Listeners%2A>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="2e2d0-135">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="2e2d0-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="2e2d0-136">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="2e2d0-136">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)  
 [<span data-ttu-id="2e2d0-137">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="2e2d0-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
