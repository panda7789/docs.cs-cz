---
title: <filter>Element pro <add> pro <listeners> pro<source>
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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153513"
---
# <a name="filter-element-for-add-for-listeners-for-source"></a><span data-ttu-id="f9ff3-102">\<filter>Element pro \<add> pro \<listeners> pro\<source></span><span class="sxs-lookup"><span data-stu-id="f9ff3-102">\<filter> Element for \<add> for \<listeners> for \<source></span></span>
<span data-ttu-id="f9ff3-103">Přidá filtr do naslouchacího procesu v `Listeners` kolekci pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="f9ff3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9ff3-104">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9ff3-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f9ff3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f9ff3-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9ff3-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="f9ff3-107">Attributes</span></span>  
  
|<span data-ttu-id="f9ff3-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="f9ff3-108">Attribute</span></span>|<span data-ttu-id="f9ff3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f9ff3-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="f9ff3-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="f9ff3-111">Určuje typ filtru, který by měl dědit z <xref:System.Diagnostics.TraceFilter> třídy.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-111">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="f9ff3-112">Můžete použít název kvalifikovaný obor názvů typu, který odpovídá <xref:System.Type.FullName%2A> vlastnosti typu, nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení, které odpovídají <xref:System.Type.AssemblyQualifiedName%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-112">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="f9ff3-113">Informace o plně kvalifikovaných názvech typů naleznete v tématu [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="f9ff3-113">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="f9ff3-114">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f9ff3-115">Řetězec předaný konstruktoru pro určenou třídu filtru.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-115">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9ff3-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f9ff3-116">Child Elements</span></span>  
 <span data-ttu-id="f9ff3-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="f9ff3-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9ff3-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f9ff3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f9ff3-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="f9ff3-119">Element</span></span>|<span data-ttu-id="f9ff3-120">Description</span><span class="sxs-lookup"><span data-stu-id="f9ff3-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f9ff3-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f9ff3-122">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="f9ff3-123">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-123">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="f9ff3-124">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-124">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="f9ff3-125">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-125">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="f9ff3-126">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-126">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="f9ff3-127">Přidá naslouchací proces do `Listeners` kolekce pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-127">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9ff3-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9ff3-128">Remarks</span></span>  
 <span data-ttu-id="f9ff3-129">`<filter>`Element musí být obsažen v `<add>` elementu pro naslouchací proces zdroje trasování, který určuje typ naslouchacího procesu, nikoli pouze název naslouchacího procesu definovaného v [\<sharedListeners>](sharedlisteners-element.md) .</span><span class="sxs-lookup"><span data-stu-id="f9ff3-129">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="f9ff3-130">Pokud je naslouchací proces definován v [\<sharedListeners>](sharedlisteners-element.md) , musí být v tomto elementu definován filtr pro tento naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-130">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="f9ff3-131">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f9ff3-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9ff3-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9ff3-132">Example</span></span>  
 <span data-ttu-id="f9ff3-133">Následující příklad ukazuje, jak použít `<filter>` element pro přidání filtru do naslouchacího procesu `console` v `Listeners` kolekci pro zdroj trasování `myTraceSource` a určení úrovně události filtru jako `Error` .</span><span class="sxs-lookup"><span data-stu-id="f9ff3-133">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f9ff3-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9ff3-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="f9ff3-135">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="f9ff3-135">Trace and Debug Settings Schema</span></span>](index.md)
