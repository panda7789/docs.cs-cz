---
title: <clear> – element pro element <listeners> pro element <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: ee4d5f1880cf6b7aac871149bf7bf59a06903bf2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286738"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="0979b-102">\<Vymazat > – Element pro \<naslouchacích procesů > pro \<zdroje ></span><span class="sxs-lookup"><span data-stu-id="0979b-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="0979b-103">Vymaže `Listeners` kolekci pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="0979b-103">Clears the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="0979b-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="0979b-104">\<configuration></span></span>  
<span data-ttu-id="0979b-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="0979b-105">\<system.diagnostics></span></span>  
<span data-ttu-id="0979b-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="0979b-106">\<sources></span></span>  
<span data-ttu-id="0979b-107">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="0979b-107">\<source></span></span>  
<span data-ttu-id="0979b-108">\<naslouchací procesy ></span><span class="sxs-lookup"><span data-stu-id="0979b-108">\<listeners></span></span>  
<span data-ttu-id="0979b-109">\<clear></span><span class="sxs-lookup"><span data-stu-id="0979b-109">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0979b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0979b-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0979b-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0979b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0979b-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0979b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0979b-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="0979b-113">Attributes</span></span>  
 <span data-ttu-id="0979b-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="0979b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0979b-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0979b-115">Child Elements</span></span>  
 <span data-ttu-id="0979b-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="0979b-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0979b-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0979b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0979b-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="0979b-118">Element</span></span>|<span data-ttu-id="0979b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="0979b-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0979b-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0979b-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="0979b-121">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="0979b-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="0979b-122">Obsahuje zdrojů trasování, které se zahájí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="0979b-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="0979b-123">Určuje zdroj trasování, který iniciuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="0979b-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="0979b-124">Určuje naslouchací procesy, které shromažďování, ukládání a směrovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="0979b-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0979b-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0979b-125">Remarks</span></span>  
 <span data-ttu-id="0979b-126">`<clear>` Element odebere všechny moduly pro naslouchání z `Listeners` kolekce pro zdroj trasování, včetně <xref:System.Diagnostics.DefaultTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="0979b-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="0979b-127">Můžete použít `<clear>` prvek před použitím `<add>` element je potřeba mít jistotu, nejsou žádné aktivní naslouchací procesy v kolekci.</span><span class="sxs-lookup"><span data-stu-id="0979b-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="0979b-128">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="0979b-128">Configuration File</span></span>  
 <span data-ttu-id="0979b-129">Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="0979b-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0979b-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="0979b-130">Example</span></span>  
 <span data-ttu-id="0979b-131">Následující příklad ukazuje způsob použití `<clear>` prvek před použitím `<add>` prvky pro přidání posluchače `console` a `textListener` k `Listeners` kolekce pro zdroj trasování `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="0979b-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0979b-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0979b-132">See also</span></span>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="0979b-133">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="0979b-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="0979b-134">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="0979b-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
