---
title: Element <filter> pro <add> <listeners> pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 766088b8a26ce3218031df74b193658ba8024280
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088908"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="43750-102">\<filtr > elementu \<přidat > pro \<naslouchací procesy > pro \<zdrojového ></span><span class="sxs-lookup"><span data-stu-id="43750-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="43750-103">Přidá filtr do naslouchacího procesu v kolekci `Listeners` pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="43750-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="43750-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="43750-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="43750-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="43750-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="43750-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zdrojů >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="43750-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="43750-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zdroj >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="43750-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="43750-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Listeners**](listeners-element-for-source.md) ></span><span class="sxs-lookup"><span data-stu-id="43750-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="43750-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<přidat >** ](add-element-for-listeners-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="43750-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)</span></span>\
<span data-ttu-id="43750-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filtr >**</span><span class="sxs-lookup"><span data-stu-id="43750-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="43750-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43750-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43750-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="43750-112">Attributes and Elements</span></span>  
 <span data-ttu-id="43750-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="43750-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43750-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="43750-114">Attributes</span></span>  
  
|<span data-ttu-id="43750-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="43750-115">Attribute</span></span>|<span data-ttu-id="43750-116">Popis</span><span class="sxs-lookup"><span data-stu-id="43750-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="43750-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="43750-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="43750-118">Určuje typ filtru, který by měl dědit z třídy <xref:System.Diagnostics.TraceFilter>.</span><span class="sxs-lookup"><span data-stu-id="43750-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="43750-119">Můžete použít název kvalifikovaný obor názvů typu, který odpovídá vlastnosti <xref:System.Type.FullName%2A> typu, nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení, který odpovídá vlastnosti <xref:System.Type.AssemblyQualifiedName%2A>.</span><span class="sxs-lookup"><span data-stu-id="43750-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="43750-120">Informace o plně kvalifikovaných názvech typů naleznete v tématu [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="43750-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="43750-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="43750-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="43750-122">Řetězec předaný konstruktoru pro určenou třídu filtru.</span><span class="sxs-lookup"><span data-stu-id="43750-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43750-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="43750-123">Child Elements</span></span>  
 <span data-ttu-id="43750-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="43750-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43750-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="43750-125">Parent Elements</span></span>  
  
|<span data-ttu-id="43750-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="43750-126">Element</span></span>|<span data-ttu-id="43750-127">Popis</span><span class="sxs-lookup"><span data-stu-id="43750-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="43750-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43750-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="43750-129">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="43750-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="43750-130">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="43750-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="43750-131">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="43750-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="43750-132">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="43750-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="43750-133">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="43750-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="43750-134">Přidá naslouchací proces do kolekce `Listeners` pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="43750-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43750-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43750-135">Remarks</span></span>  
 <span data-ttu-id="43750-136">Element `<filter>` musí být obsažen v elementu `<add>` pro naslouchací proces zdroje trasování, který určuje typ naslouchacího procesu, nikoli pouze název naslouchacího procesu definovaného v [\<ch sharedListeners >](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="43750-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="43750-137">Pokud je naslouchací proces definován ve [\<sharedListeners >](sharedlisteners-element.md), musí být v tomto elementu definován filtr pro tento naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="43750-137">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="43750-138">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="43750-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43750-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="43750-139">Example</span></span>  
 <span data-ttu-id="43750-140">Následující příklad ukazuje, jak použít `<filter>` element pro přidání filtru do `console` naslouchacího procesu v kolekci `Listeners` pro `myTraceSource`zdroj trasování a určení úrovně události filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="43750-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43750-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43750-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="43750-142">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="43750-142">Trace and Debug Settings Schema</span></span>](index.md)
