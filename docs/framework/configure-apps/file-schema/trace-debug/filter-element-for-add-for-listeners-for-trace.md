---
title: <filter> element pro <add> pro <listeners> pro <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: f6b1ec99c5aab8e85df7f1920aca32f49a5be066
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699366"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="6da84-102">\<filter > element pro \<add > pro \<listeners > pro \<trace ></span><span class="sxs-lookup"><span data-stu-id="6da84-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="6da84-103">Přidá filtr do naslouchacího procesu v kolekci `Listeners` pro trasování.</span><span class="sxs-lookup"><span data-stu-id="6da84-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
[<span data-ttu-id="6da84-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="6da84-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="6da84-105">&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="6da84-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="6da84-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="6da84-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="6da84-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<listeners >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="6da84-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>  
<span data-ttu-id="6da84-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0add >** ](add-element-for-listeners-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="6da84-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)</span></span>  
<span data-ttu-id="6da84-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9 **&nbsp;1filter >**</span><span class="sxs-lookup"><span data-stu-id="6da84-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6da84-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6da84-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6da84-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6da84-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6da84-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6da84-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6da84-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="6da84-113">Attributes</span></span>  
  
|<span data-ttu-id="6da84-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="6da84-114">Attribute</span></span>|<span data-ttu-id="6da84-115">Popis</span><span class="sxs-lookup"><span data-stu-id="6da84-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="6da84-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="6da84-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="6da84-117">Určuje typ filtru, který by měl dědit z třídy <xref:System.Diagnostics.TraceFilter>.</span><span class="sxs-lookup"><span data-stu-id="6da84-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="6da84-118">Můžete použít název kvalifikovaný obor názvů typu, který odpovídá vlastnosti <xref:System.Type.FullName%2A>, nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení, který odpovídá vlastnosti <xref:System.Type.AssemblyQualifiedName%2A>.</span><span class="sxs-lookup"><span data-stu-id="6da84-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="6da84-119">Informace o plně kvalifikovaných názvech typů naleznete v tématu [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="6da84-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="6da84-120">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6da84-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6da84-121">Řetězec předaný konstruktoru pro určenou třídu filtru.</span><span class="sxs-lookup"><span data-stu-id="6da84-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6da84-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6da84-122">Child Elements</span></span>  
 <span data-ttu-id="6da84-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="6da84-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6da84-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6da84-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6da84-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="6da84-125">Element</span></span>|<span data-ttu-id="6da84-126">Popis</span><span class="sxs-lookup"><span data-stu-id="6da84-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6da84-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6da84-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6da84-128">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="6da84-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="6da84-129">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="6da84-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="6da84-130">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="6da84-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="6da84-131">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="6da84-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="6da84-132">Přidá naslouchací proces do kolekce `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="6da84-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6da84-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6da84-133">Remarks</span></span>  
 <span data-ttu-id="6da84-134">Element `<filter>` musí být obsažen v elementu `<add>` pro naslouchací proces trasování, který určuje typ naslouchacího procesu, nikoli pouze název naslouchacího procesu definovaného v [> \<sharedListeners](sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="6da84-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="6da84-135">Pokud je naslouchací proces definován v [> \<sharedListeners](sharedlisteners-element.md), musí být v tomto elementu definován filtr pro tento naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="6da84-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="6da84-136">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="6da84-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6da84-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="6da84-137">Example</span></span>  
 <span data-ttu-id="6da84-138">Následující příklad ukazuje způsob použití prvku `<filter>` pro přidání filtru do naslouchacího procesu `console` v kolekci `Listeners` pro trasování, určení úrovně události filtru jako `Error`.</span><span class="sxs-lookup"><span data-stu-id="6da84-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6da84-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6da84-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="6da84-140">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="6da84-140">Trace and Debug Settings Schema</span></span>](index.md)
