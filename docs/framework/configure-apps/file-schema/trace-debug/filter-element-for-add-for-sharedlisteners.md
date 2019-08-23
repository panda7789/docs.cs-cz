---
title: <filter>Element pro <add> pro<sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: 571a3add232f3e4f9747040dc104b85e8cc3085e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920510"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="c6842-102">\<Filtrovat > element pro \<přidání > pro \<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="c6842-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="c6842-103">Přidá filtr do naslouchacího procesu v `sharedListeners` kolekci.</span><span class="sxs-lookup"><span data-stu-id="c6842-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
 <span data-ttu-id="c6842-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c6842-104">\<configuration></span></span>  
<span data-ttu-id="c6842-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="c6842-105">\<system.diagnostics></span></span>  
<span data-ttu-id="c6842-106">\<sharedListeners – > element</span><span class="sxs-lookup"><span data-stu-id="c6842-106">\<sharedListeners> Element</span></span>  
<span data-ttu-id="c6842-107">\<add></span><span class="sxs-lookup"><span data-stu-id="c6842-107">\<add></span></span>  
<span data-ttu-id="c6842-108">\<Filtrovat ></span><span class="sxs-lookup"><span data-stu-id="c6842-108">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6842-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6842-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6842-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c6842-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c6842-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c6842-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6842-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c6842-112">Attributes</span></span>  
  
|<span data-ttu-id="c6842-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c6842-113">Attribute</span></span>|<span data-ttu-id="c6842-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c6842-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6842-115">**type**</span><span class="sxs-lookup"><span data-stu-id="c6842-115">**type**</span></span>|<span data-ttu-id="c6842-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c6842-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="c6842-117">Určuje typ filtru.</span><span class="sxs-lookup"><span data-stu-id="c6842-117">Specifies the type of the filter.</span></span> <span data-ttu-id="c6842-118">Můžete použít pouze úplný název typu (ve formátu <xref:System.Type.FullName%2A?displayProperty=nameWithType> vlastnosti), nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení (ve formátu <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="c6842-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="c6842-119">Informace o vytvoření plně kvalifikovaného názvu typu naleznete v tématu [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="c6842-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="c6842-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="c6842-120">**initializeData**</span></span>|<span data-ttu-id="c6842-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="c6842-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c6842-122">Řetězec předaný konstruktoru pro určenou třídu.</span><span class="sxs-lookup"><span data-stu-id="c6842-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6842-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c6842-123">Child Elements</span></span>  
 <span data-ttu-id="c6842-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="c6842-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6842-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c6842-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c6842-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="c6842-126">Element</span></span>|<span data-ttu-id="c6842-127">Popis</span><span class="sxs-lookup"><span data-stu-id="c6842-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c6842-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6842-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c6842-129">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="c6842-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="c6842-130">Kolekce posluchačů, na které může odkazovat jakýkoliv element source nebo Trace.</span><span class="sxs-lookup"><span data-stu-id="c6842-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="c6842-131">Přidá naslouchací proces do kolekce **sharedListeners** .</span><span class="sxs-lookup"><span data-stu-id="c6842-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6842-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6842-132">Remarks</span></span>  
 <span data-ttu-id="c6842-133">Pokud je naslouchací proces definován `<add>` v prvku `<sharedListeners>` elementu, filtr pro tento naslouchací proces `<filter>` by měl být definován v prvku, který je podřízeným `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="c6842-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="c6842-134">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6842-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6842-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6842-135">Example</span></span>  
 <span data-ttu-id="c6842-136">Následující příklad ukazuje, jak použít `<filter>` element pro přidání filtru do naslouchacího procesu `console` trasování v `sharedListeners` kolekci.</span><span class="sxs-lookup"><span data-stu-id="c6842-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6842-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6842-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="c6842-138">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="c6842-138">Trace and Debug Settings Schema</span></span>](index.md)
