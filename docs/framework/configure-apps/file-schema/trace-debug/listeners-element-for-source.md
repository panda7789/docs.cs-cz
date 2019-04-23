---
title: <listeners> – element pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: b15a30fb6d356f92312bf33bc1964c7922ba1383
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089650"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="d54d8-102">\<naslouchací procesy > – Element pro \<zdroje ></span><span class="sxs-lookup"><span data-stu-id="d54d8-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="d54d8-103">Přidá nebo odebere naslouchacích procesů v <xref:System.Diagnostics.TraceSource.Listeners%2A> kolekce <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="d54d8-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="d54d8-104">Naslouchací proces bude směrovat výstup trasování příslušný cíli, jako je protokol, okno nebo textový soubor.</span><span class="sxs-lookup"><span data-stu-id="d54d8-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="d54d8-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="d54d8-105">\<configuration></span></span>  
<span data-ttu-id="d54d8-106">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="d54d8-106">\<system.diagnostics></span></span>  
<span data-ttu-id="d54d8-107">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="d54d8-107">\<sources></span></span>  
<span data-ttu-id="d54d8-108">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="d54d8-108">\<source></span></span>  
<span data-ttu-id="d54d8-109">\<naslouchací procesy > – Element</span><span class="sxs-lookup"><span data-stu-id="d54d8-109">\<listeners> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d54d8-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d54d8-110">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d54d8-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d54d8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d54d8-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d54d8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d54d8-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d54d8-113">Attributes</span></span>  
 <span data-ttu-id="d54d8-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="d54d8-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d54d8-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d54d8-115">Child Elements</span></span>  
  
|<span data-ttu-id="d54d8-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="d54d8-116">Element</span></span>|<span data-ttu-id="d54d8-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d54d8-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d54d8-118">\<add></span><span class="sxs-lookup"><span data-stu-id="d54d8-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="d54d8-119">Přidá naslouchací proces pro `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="d54d8-119">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="d54d8-120">\<remove></span><span class="sxs-lookup"><span data-stu-id="d54d8-120">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="d54d8-121">Odebere z naslouchacího procesu `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="d54d8-121">Removes a listener from the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="d54d8-122">\<clear></span><span class="sxs-lookup"><span data-stu-id="d54d8-122">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="d54d8-123">Vymaže `Listeners` kolekci pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="d54d8-123">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d54d8-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d54d8-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d54d8-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="d54d8-125">Element</span></span>|<span data-ttu-id="d54d8-126">Popis</span><span class="sxs-lookup"><span data-stu-id="d54d8-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d54d8-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d54d8-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d54d8-128">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="d54d8-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="d54d8-129">Obsahuje zdrojů trasování, které se zahájí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="d54d8-129">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="d54d8-130">Určuje zdroj trasování, který iniciuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="d54d8-130">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d54d8-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d54d8-131">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="d54d8-132">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="d54d8-132">Configuration File</span></span>  
 <span data-ttu-id="d54d8-133">Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="d54d8-133">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d54d8-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="d54d8-134">Example</span></span>  
 <span data-ttu-id="d54d8-135">Následující příklad ukazuje způsob použití `<listeners>` prvku pro přidání naslouchacího procesu trasování konzoly pro `mySource` zdroje dat a Vymazat výchozí naslouchací služby stopy.</span><span class="sxs-lookup"><span data-stu-id="d54d8-135">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d54d8-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d54d8-136">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="d54d8-137">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="d54d8-137">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="d54d8-138">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="d54d8-138">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
