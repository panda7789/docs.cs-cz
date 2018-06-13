---
title: '&lt;Vymazat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;zdroje&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8c6ef51dae36e94fa4a4fdc5ad8983380e78bde3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746849"
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="83d22-102">&lt;Vymazat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;zdroje&gt;</span><span class="sxs-lookup"><span data-stu-id="83d22-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="83d22-103">Vymaže `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="83d22-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="83d22-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="83d22-104">\<configuration></span></span>  
<span data-ttu-id="83d22-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="83d22-105">\<system.diagnostics></span></span>  
<span data-ttu-id="83d22-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="83d22-106">\<sources></span></span>  
<span data-ttu-id="83d22-107">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="83d22-107">\<source></span></span>  
<span data-ttu-id="83d22-108">\<moduly pro naslouchání ></span><span class="sxs-lookup"><span data-stu-id="83d22-108">\<listeners></span></span>  
<span data-ttu-id="83d22-109">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="83d22-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83d22-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83d22-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83d22-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="83d22-111">Attributes and Elements</span></span>  
 <span data-ttu-id="83d22-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="83d22-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83d22-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="83d22-113">Attributes</span></span>  
 <span data-ttu-id="83d22-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="83d22-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="83d22-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="83d22-115">Child Elements</span></span>  
 <span data-ttu-id="83d22-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="83d22-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83d22-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="83d22-117">Parent Elements</span></span>  
  
|<span data-ttu-id="83d22-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="83d22-118">Element</span></span>|<span data-ttu-id="83d22-119">Popis</span><span class="sxs-lookup"><span data-stu-id="83d22-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="83d22-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="83d22-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="83d22-121">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="83d22-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="83d22-122">Obsahuje trasování zdrojů, které zahájí trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="83d22-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="83d22-123">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="83d22-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="83d22-124">Určuje naslouchací procesy, které shromažďování, ukládání a směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="83d22-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83d22-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83d22-125">Remarks</span></span>  
 <span data-ttu-id="83d22-126">`<clear>` Element odebere všechny moduly pro naslouchání z `Listeners` kolekce pro zdroj trasování, včetně <xref:System.Diagnostics.DefaultTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="83d22-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="83d22-127">Můžete použít `<clear>` element před použitím `<add>` elementu, který chcete být jisti, nejsou žádné aktivní naslouchací procesy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="83d22-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="83d22-128">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="83d22-128">Configuration File</span></span>  
 <span data-ttu-id="83d22-129">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="83d22-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83d22-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="83d22-130">Example</span></span>  
 <span data-ttu-id="83d22-131">Následující příklad ukazuje, jak používat `<clear>` element před použitím `<add>` elementy přidat posluchače `console` a `textListener` k `Listeners` kolekci pro zdroj trasování `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="83d22-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="83d22-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="83d22-132">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="83d22-133">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="83d22-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="83d22-134">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="83d22-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
