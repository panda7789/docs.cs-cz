---
title: <filter> – Element pro <add> pro <listeners> pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 3abfd0bdd40f98a9e4774677fc2cd5068c14333f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673768"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="11490-102">\<Filtr > – Element pro \<Přidat > pro \<naslouchacích procesů > pro \<zdroje ></span><span class="sxs-lookup"><span data-stu-id="11490-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="11490-103">Přidá filtr do naslouchacího procesu v `Listeners` kolekci pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="11490-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="11490-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="11490-104">\<configuration></span></span>  
<span data-ttu-id="11490-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="11490-105">\<system.diagnostics></span></span>  
<span data-ttu-id="11490-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="11490-106">\<sources></span></span>  
<span data-ttu-id="11490-107">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="11490-107">\<source></span></span>  
<span data-ttu-id="11490-108">\<naslouchací procesy ></span><span class="sxs-lookup"><span data-stu-id="11490-108">\<listeners></span></span>  
<span data-ttu-id="11490-109">\<add></span><span class="sxs-lookup"><span data-stu-id="11490-109">\<add></span></span>  
<span data-ttu-id="11490-110">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="11490-110">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11490-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11490-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11490-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11490-112">Attributes and Elements</span></span>  
 <span data-ttu-id="11490-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11490-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11490-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="11490-114">Attributes</span></span>  
  
|<span data-ttu-id="11490-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="11490-115">Attribute</span></span>|<span data-ttu-id="11490-116">Popis</span><span class="sxs-lookup"><span data-stu-id="11490-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="11490-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="11490-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="11490-118">Určuje typ filtru, která by měla dědit z <xref:System.Diagnostics.TraceFilter> třídy.</span><span class="sxs-lookup"><span data-stu-id="11490-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="11490-119">Můžete použít název kvalifikovaný v oboru názvů typu, který odpovídá typu <xref:System.Type.FullName%2A> vlastnost, nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení, která odpovídá <xref:System.Type.AssemblyQualifiedName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="11490-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="11490-120">Informace o úplných názvů typů najdete v tématu [zadání plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="11490-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="11490-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="11490-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="11490-122">Řetězec předaný konstruktoru pro třídu zadaný filtr.</span><span class="sxs-lookup"><span data-stu-id="11490-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11490-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="11490-123">Child Elements</span></span>  
 <span data-ttu-id="11490-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="11490-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11490-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="11490-125">Parent Elements</span></span>  
  
|<span data-ttu-id="11490-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="11490-126">Element</span></span>|<span data-ttu-id="11490-127">Popis</span><span class="sxs-lookup"><span data-stu-id="11490-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="11490-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="11490-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="11490-129">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="11490-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="11490-130">Obsahuje zdrojů trasování, které se zahájí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="11490-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="11490-131">Určuje zdroj trasování, který iniciuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="11490-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="11490-132">Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="11490-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="11490-133">Posluchači přímý výstup trasování příslušný cíli.</span><span class="sxs-lookup"><span data-stu-id="11490-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="11490-134">Přidá naslouchací proces pro `Listeners` kolekci pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="11490-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11490-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11490-135">Remarks</span></span>  
 <span data-ttu-id="11490-136">`<filter>` Elementu musí být součástí `<add>` element pro zdroj trasování naslouchací proces, který určuje typ naslouchací proces, ne jenom název naslouchacího procesu definovaný v [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="11490-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="11490-137">Pokud je definován naslouchací proces ve [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtr pro tuto naslouchací proces musí být definován v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="11490-137">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="11490-138">Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="11490-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11490-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="11490-139">Example</span></span>  
 <span data-ttu-id="11490-140">Následující příklad ukazuje způsob použití `<filter>` prvek přidejte filtr k naslouchacímu procesu `console` v `Listeners` kolekce pro zdroj trasování `myTraceSource`, určení úroveň filtru událostí jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="11490-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11490-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11490-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="11490-142">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="11490-142">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
