---
title: '&lt;Filtr&gt; Element pro &lt;přidat&gt; pro &lt;sharedListeners&gt;'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3bbba1c805c6b300f7cf7b3d9112cde9df7607a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltsharedlistenersgt"></a><span data-ttu-id="44299-102">&lt;Filtr&gt; Element pro &lt;přidat&gt; pro &lt;sharedListeners&gt;</span><span class="sxs-lookup"><span data-stu-id="44299-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;sharedListeners&gt;</span></span>
<span data-ttu-id="44299-103">Přidá filtr do naslouchací proces ve `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="44299-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
 <span data-ttu-id="44299-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="44299-104">\<configuration></span></span>  
<span data-ttu-id="44299-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="44299-105">\<system.diagnostics></span></span>  
<span data-ttu-id="44299-106">\<sharedListeners > elementu</span><span class="sxs-lookup"><span data-stu-id="44299-106">\<sharedListeners> Element</span></span>  
<span data-ttu-id="44299-107">\<add></span><span class="sxs-lookup"><span data-stu-id="44299-107">\<add></span></span>  
<span data-ttu-id="44299-108">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="44299-108">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44299-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44299-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44299-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="44299-110">Attributes and Elements</span></span>  
 <span data-ttu-id="44299-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="44299-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44299-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="44299-112">Attributes</span></span>  
  
|<span data-ttu-id="44299-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="44299-113">Attribute</span></span>|<span data-ttu-id="44299-114">Popis</span><span class="sxs-lookup"><span data-stu-id="44299-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44299-115">**Typ**</span><span class="sxs-lookup"><span data-stu-id="44299-115">**type**</span></span>|<span data-ttu-id="44299-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="44299-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="44299-117">Určuje typ filtru.</span><span class="sxs-lookup"><span data-stu-id="44299-117">Specifies the type of the filter.</span></span> <span data-ttu-id="44299-118">Můžete použít jenom úplný název typu (ve formátu <xref:System.Type.FullName%2A?displayProperty=nameWithType> vlastnost), nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení (ve formátu <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> vlastnost).</span><span class="sxs-lookup"><span data-stu-id="44299-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="44299-119">Informace o vytváření úplný název typu, najdete v článku [určení plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="44299-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="44299-120">**initializeData –**</span><span class="sxs-lookup"><span data-stu-id="44299-120">**initializeData**</span></span>|<span data-ttu-id="44299-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="44299-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="44299-122">Řetězec předaný konstruktoru pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="44299-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44299-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="44299-123">Child Elements</span></span>  
 <span data-ttu-id="44299-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="44299-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44299-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="44299-125">Parent Elements</span></span>  
  
|<span data-ttu-id="44299-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="44299-126">Element</span></span>|<span data-ttu-id="44299-127">Popis</span><span class="sxs-lookup"><span data-stu-id="44299-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="44299-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44299-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="44299-129">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="44299-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="44299-130">Kolekce naslouchací procesy, které může odkazovat všechny zdroje nebo element trasování.</span><span class="sxs-lookup"><span data-stu-id="44299-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="44299-131">Přidá naslouchací proces a **sharedListeners** kolekce.</span><span class="sxs-lookup"><span data-stu-id="44299-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44299-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44299-132">Remarks</span></span>  
 <span data-ttu-id="44299-133">Pokud naslouchací proces je definována v `<add>` element `<sharedListeners>` elementu, filtr pro tento naslouchací proces nesmí být definován v `<filter>` element, který je podřízená `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="44299-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="44299-134">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="44299-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44299-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="44299-135">Example</span></span>  
 <span data-ttu-id="44299-136">Následující příklad ukazuje, jak používat `<filter>` elementu, který chcete přidat filtr pro naslouchací proces trasování `console` v `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="44299-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44299-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="44299-137">See Also</span></span>  
 <xref:System.Diagnostics.TraceFilter>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="44299-138">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="44299-138">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
