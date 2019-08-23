---
title: <clear>Element pro <listeners> pro<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 768d51a74b4c31d1250d2f5d6517f760f886e0a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920560"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="481cc-102">\<Clear > element pro \<naslouchací procesy > \<pro zdroj ></span><span class="sxs-lookup"><span data-stu-id="481cc-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="481cc-103">`Listeners` Vymaže kolekci zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="481cc-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="481cc-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="481cc-104">\<configuration></span></span>  
<span data-ttu-id="481cc-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="481cc-105">\<system.diagnostics></span></span>  
<span data-ttu-id="481cc-106">\<> zdrojů</span><span class="sxs-lookup"><span data-stu-id="481cc-106">\<sources></span></span>  
<span data-ttu-id="481cc-107">\<> zdroje</span><span class="sxs-lookup"><span data-stu-id="481cc-107">\<source></span></span>  
<span data-ttu-id="481cc-108">\<> naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="481cc-108">\<listeners></span></span>  
<span data-ttu-id="481cc-109">\<Vymazat ></span><span class="sxs-lookup"><span data-stu-id="481cc-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="481cc-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="481cc-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="481cc-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="481cc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="481cc-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="481cc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="481cc-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="481cc-113">Attributes</span></span>  
 <span data-ttu-id="481cc-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="481cc-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="481cc-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="481cc-115">Child Elements</span></span>  
 <span data-ttu-id="481cc-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="481cc-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="481cc-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="481cc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="481cc-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="481cc-118">Element</span></span>|<span data-ttu-id="481cc-119">Popis</span><span class="sxs-lookup"><span data-stu-id="481cc-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="481cc-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="481cc-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="481cc-121">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="481cc-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="481cc-122">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="481cc-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="481cc-123">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="481cc-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="481cc-124">Určuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="481cc-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="481cc-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="481cc-125">Remarks</span></span>  
 <span data-ttu-id="481cc-126">Prvek odebere všechny naslouchací procesy `Listeners` z kolekce pro zdroj <xref:System.Diagnostics.DefaultTraceListener>trasování, včetně. `<clear>`</span><span class="sxs-lookup"><span data-stu-id="481cc-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="481cc-127">`<clear>` Element lze použít před `<add>` použitím prvku, aby bylo jisté, že v kolekci nejsou žádné další aktivní naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="481cc-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="481cc-128">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="481cc-128">Configuration File</span></span>  
 <span data-ttu-id="481cc-129">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="481cc-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="481cc-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="481cc-130">Example</span></span>  
 <span data-ttu-id="481cc-131">Následující příklad `<clear>` ukazuje, jak použít element před `<add>` použitím prvků pro přidání posluchačů `console` a `textListener` do `Listeners` kolekce pro zdroj `TraceSourceApp`trasování.</span><span class="sxs-lookup"><span data-stu-id="481cc-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="481cc-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="481cc-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="481cc-133">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="481cc-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="481cc-134">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="481cc-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
