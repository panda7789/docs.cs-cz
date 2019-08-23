---
title: <filter><add> Element<listeners> pro pro pro<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: afde5381a7dd7dfe6a1a9d238a2029511bd9bae2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927139"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="75c6a-102">\<Filter > element pro \<Add > for \<Listeners > \<for trace ></span><span class="sxs-lookup"><span data-stu-id="75c6a-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="75c6a-103">Přidá filtr pro naslouchací proces v `Listeners` kolekci pro trasování.</span><span class="sxs-lookup"><span data-stu-id="75c6a-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
 <span data-ttu-id="75c6a-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="75c6a-104">\<configuration></span></span>  
<span data-ttu-id="75c6a-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="75c6a-105">\<system.diagnostics></span></span>  
<span data-ttu-id="75c6a-106">\<> trasování</span><span class="sxs-lookup"><span data-stu-id="75c6a-106">\<trace></span></span>  
<span data-ttu-id="75c6a-107">\<> naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="75c6a-107">\<listeners></span></span>  
<span data-ttu-id="75c6a-108">\<add></span><span class="sxs-lookup"><span data-stu-id="75c6a-108">\<add></span></span>  
<span data-ttu-id="75c6a-109">\<Filtrovat ></span><span class="sxs-lookup"><span data-stu-id="75c6a-109">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75c6a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75c6a-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75c6a-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="75c6a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="75c6a-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="75c6a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75c6a-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="75c6a-113">Attributes</span></span>  
  
|<span data-ttu-id="75c6a-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="75c6a-114">Attribute</span></span>|<span data-ttu-id="75c6a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="75c6a-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="75c6a-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="75c6a-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="75c6a-117">Určuje typ filtru, který by měl dědit z <xref:System.Diagnostics.TraceFilter> třídy.</span><span class="sxs-lookup"><span data-stu-id="75c6a-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="75c6a-118">Můžete použít název kvalifikovaný obor názvů typu, který odpovídá <xref:System.Type.FullName%2A> vlastnosti typu, nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení, které odpovídají <xref:System.Type.AssemblyQualifiedName%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="75c6a-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="75c6a-119">Informace o plně kvalifikovaných názvech typů naleznete v tématu [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="75c6a-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="75c6a-120">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="75c6a-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="75c6a-121">Řetězec předaný konstruktoru pro určenou třídu filtru.</span><span class="sxs-lookup"><span data-stu-id="75c6a-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75c6a-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="75c6a-122">Child Elements</span></span>  
 <span data-ttu-id="75c6a-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="75c6a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75c6a-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="75c6a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="75c6a-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="75c6a-125">Element</span></span>|<span data-ttu-id="75c6a-126">Popis</span><span class="sxs-lookup"><span data-stu-id="75c6a-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="75c6a-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75c6a-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="75c6a-128">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="75c6a-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="75c6a-129">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="75c6a-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="75c6a-130">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="75c6a-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="75c6a-131">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="75c6a-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="75c6a-132">Přidá naslouchací proces do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="75c6a-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75c6a-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75c6a-133">Remarks</span></span>  
 <span data-ttu-id="75c6a-134">Element musí být obsažen `<add>` v elementu pro naslouchací proces trasování, který určuje typ naslouchacího procesu, nikoli pouze název naslouchacího procesu definovaného v [ \<> sharedListeners.](sharedlisteners-element.md) `<filter>`</span><span class="sxs-lookup"><span data-stu-id="75c6a-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="75c6a-135">Pokud je naslouchací proces definován v [ \<> sharedListeners](sharedlisteners-element.md), filtr pro tento naslouchací proces musí být definován v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="75c6a-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="75c6a-136">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="75c6a-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75c6a-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="75c6a-137">Example</span></span>  
 <span data-ttu-id="75c6a-138">Následující příklad ukazuje, jak `<filter>` použít element pro přidání filtru do naslouchacího procesu `console` v `Listeners` kolekci pro trasování, určení úrovně události filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="75c6a-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="75c6a-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75c6a-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="75c6a-140">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="75c6a-140">Trace and Debug Settings Schema</span></span>](index.md)
