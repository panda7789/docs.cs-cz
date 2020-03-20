---
title: <filter>Prvek <add> pro <listeners> pro pro<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: b6c2c2bf7fe953a75f9d8129039ef33b4d8a3f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153463"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="6b2a0-102">\<filtr> \<Element pro \<přidání> \<pro posluchače> pro trasování></span><span class="sxs-lookup"><span data-stu-id="6b2a0-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="6b2a0-103">Přidá filtr naslouchací proces v kolekci `Listeners` pro trasování.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

<span data-ttu-id="6b2a0-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b2a0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6b2a0-105">&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b2a0-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="6b2a0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trasovací>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b2a0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="6b2a0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<posluchači>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="6b2a0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="6b2a0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<přidat>**](add-element-for-listeners-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="6b2a0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)</span></span>\
<span data-ttu-id="6b2a0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>filtru**</span><span class="sxs-lookup"><span data-stu-id="6b2a0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6b2a0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b2a0-110">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b2a0-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6b2a0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6b2a0-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b2a0-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="6b2a0-113">Attributes</span></span>  
  
|<span data-ttu-id="6b2a0-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="6b2a0-114">Attribute</span></span>|<span data-ttu-id="6b2a0-115">Popis</span><span class="sxs-lookup"><span data-stu-id="6b2a0-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="6b2a0-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="6b2a0-117">Určuje typ filtru, který by měl <xref:System.Diagnostics.TraceFilter> dědit z třídy.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="6b2a0-118">Můžete použít název s kvalifikací oboru názvů typu, který odpovídá <xref:System.Type.FullName%2A> vlastnosti typu, nebo můžete použít plně kvalifikovaný název typu včetně <xref:System.Type.AssemblyQualifiedName%2A> informací o sestavení, které odpovídají vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="6b2a0-119">Informace o plně kvalifikovaných názvech typů naleznete [v tématu Určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="6b2a0-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="6b2a0-120">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6b2a0-121">Řetězec předaný konstruktoru pro zadanou třídu filtru.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b2a0-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6b2a0-122">Child Elements</span></span>  
 <span data-ttu-id="6b2a0-123">Žádné.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b2a0-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6b2a0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6b2a0-125">Element</span><span class="sxs-lookup"><span data-stu-id="6b2a0-125">Element</span></span>|<span data-ttu-id="6b2a0-126">Popis</span><span class="sxs-lookup"><span data-stu-id="6b2a0-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6b2a0-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6b2a0-128">Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="6b2a0-129">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="6b2a0-130">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="6b2a0-131">Naslouchací procesy nasměrují výstup trasování na příslušný cíl.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="6b2a0-132">Přidá naslouchací proces do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b2a0-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b2a0-133">Remarks</span></span>  
 <span data-ttu-id="6b2a0-134">Prvek `<filter>` musí být obsažen `<add>` v elementu pro naslouchací proces trasování, který určuje typ posluchače, nikoli pouze název posluchače definovaného [ \<v sharedListeners>](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="6b2a0-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="6b2a0-135">Pokud je naslouchací [ \< ](sharedlisteners-element.md)proces definován v sharedListeners>, filtr pro tento naslouchací proces musí být definován v tomto prvku.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="6b2a0-136">Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="6b2a0-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b2a0-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b2a0-137">Example</span></span>  
 <span data-ttu-id="6b2a0-138">Následující příklad ukazuje, jak `<filter>` pomocí prvku přidat filtr `console` do `Listeners` naslouchací proces v `Error`kolekci pro trasování, určení úrovně události filtru jako .</span><span class="sxs-lookup"><span data-stu-id="6b2a0-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b2a0-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b2a0-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="6b2a0-140">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="6b2a0-140">Trace and Debug Settings Schema</span></span>](index.md)
