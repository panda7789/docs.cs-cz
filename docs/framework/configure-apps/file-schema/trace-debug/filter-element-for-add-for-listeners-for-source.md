---
title: <filter>Prvek <add> pro <listeners> pro pro<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
ms.openlocfilehash: 0cb668782de263d5f784691f46cb8b74541d942b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153513"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="75687-102">\<filtr> \<Element pro \<přidání> \<pro naslouchací> pro zdrojové></span><span class="sxs-lookup"><span data-stu-id="75687-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="75687-103">Přidá filtr do naslouchací proces v kolekci `Listeners` pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="75687-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="75687-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="75687-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="75687-105">&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="75687-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="75687-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdroje>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="75687-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="75687-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdrojové>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="75687-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="75687-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<posluchači>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="75687-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="75687-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<přidat>**](add-element-for-listeners-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="75687-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)</span></span>\
<span data-ttu-id="75687-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>filtru**</span><span class="sxs-lookup"><span data-stu-id="75687-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="75687-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75687-111">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75687-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="75687-112">Attributes and Elements</span></span>  
 <span data-ttu-id="75687-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="75687-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75687-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="75687-114">Attributes</span></span>  
  
|<span data-ttu-id="75687-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="75687-115">Attribute</span></span>|<span data-ttu-id="75687-116">Popis</span><span class="sxs-lookup"><span data-stu-id="75687-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="75687-117">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="75687-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="75687-118">Určuje typ filtru, který by měl <xref:System.Diagnostics.TraceFilter> dědit z třídy.</span><span class="sxs-lookup"><span data-stu-id="75687-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="75687-119">Můžete použít název s kvalifikací oboru názvů typu, který odpovídá <xref:System.Type.FullName%2A> vlastnosti typu, nebo můžete použít plně kvalifikovaný název typu včetně <xref:System.Type.AssemblyQualifiedName%2A> informací o sestavení, které odpovídají vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="75687-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="75687-120">Informace o plně kvalifikovaných názvech typů naleznete [v tématu Určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="75687-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="75687-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="75687-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="75687-122">Řetězec předaný konstruktoru pro zadanou třídu filtru.</span><span class="sxs-lookup"><span data-stu-id="75687-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75687-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="75687-123">Child Elements</span></span>  
 <span data-ttu-id="75687-124">Žádné.</span><span class="sxs-lookup"><span data-stu-id="75687-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75687-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="75687-125">Parent Elements</span></span>  
  
|<span data-ttu-id="75687-126">Element</span><span class="sxs-lookup"><span data-stu-id="75687-126">Element</span></span>|<span data-ttu-id="75687-127">Popis</span><span class="sxs-lookup"><span data-stu-id="75687-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="75687-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75687-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="75687-129">Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="75687-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="75687-130">Obsahuje zdroje trasování, které iniciují tracing zprávy.</span><span class="sxs-lookup"><span data-stu-id="75687-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="75687-131">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="75687-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="75687-132">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="75687-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="75687-133">Naslouchací procesy nasměrují výstup trasování na příslušný cíl.</span><span class="sxs-lookup"><span data-stu-id="75687-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="75687-134">Přidá naslouchací proces do `Listeners` kolekce pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="75687-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75687-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75687-135">Remarks</span></span>  
 <span data-ttu-id="75687-136">Prvek `<filter>` musí být obsažen `<add>` v elementu pro posluchače zdroje trasování, který určuje typ posluchače, nikoli pouze název posluchače definovaného [ \<v sharedListeners>](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="75687-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="75687-137">Pokud je naslouchací [ \< ](sharedlisteners-element.md)proces definován v sharedListeners>, filtr pro tento naslouchací proces musí být definován v tomto prvku.</span><span class="sxs-lookup"><span data-stu-id="75687-137">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="75687-138">Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="75687-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75687-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="75687-139">Example</span></span>  
 <span data-ttu-id="75687-140">Následující příklad ukazuje, jak `<filter>` pomocí prvku přidat filtr `console` do `Listeners` naslouchací proces v kolekci pro zdroj `myTraceSource`trasování , určení úrovně události filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="75687-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="75687-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="75687-141">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="75687-142">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="75687-142">Trace and Debug Settings Schema</span></span>](index.md)
