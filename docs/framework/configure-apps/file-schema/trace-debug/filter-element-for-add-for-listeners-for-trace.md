---
title: <filter>Element pro <add> pro <listeners> pro<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: b6c2c2bf7fe953a75f9d8129039ef33b4d8a3f56
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153463"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="a3ad6-102">\<filter>Element pro \<add> pro \<listeners> pro\<trace></span><span class="sxs-lookup"><span data-stu-id="a3ad6-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="a3ad6-103">Přidá filtr pro naslouchací proces v `Listeners` kolekci pro trasování.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="a3ad6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3ad6-104">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3ad6-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a3ad6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a3ad6-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3ad6-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="a3ad6-107">Attributes</span></span>  
  
|<span data-ttu-id="a3ad6-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="a3ad6-108">Attribute</span></span>|<span data-ttu-id="a3ad6-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a3ad6-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="a3ad6-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="a3ad6-111">Určuje typ filtru, který by měl dědit z <xref:System.Diagnostics.TraceFilter> třídy.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-111">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="a3ad6-112">Můžete použít název kvalifikovaný obor názvů typu, který odpovídá <xref:System.Type.FullName%2A> vlastnosti typu, nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení, které odpovídají <xref:System.Type.AssemblyQualifiedName%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-112">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="a3ad6-113">Informace o plně kvalifikovaných názvech typů naleznete v tématu [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="a3ad6-113">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="a3ad6-114">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a3ad6-115">Řetězec předaný konstruktoru pro určenou třídu filtru.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-115">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3ad6-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a3ad6-116">Child Elements</span></span>  
 <span data-ttu-id="a3ad6-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="a3ad6-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3ad6-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a3ad6-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a3ad6-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="a3ad6-119">Element</span></span>|<span data-ttu-id="a3ad6-120">Description</span><span class="sxs-lookup"><span data-stu-id="a3ad6-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a3ad6-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a3ad6-122">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="a3ad6-123">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-123">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="a3ad6-124">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-124">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="a3ad6-125">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="a3ad6-126">Přidá naslouchací proces do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-126">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3ad6-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3ad6-127">Remarks</span></span>  
 <span data-ttu-id="a3ad6-128">`<filter>`Element musí být obsažen v `<add>` elementu pro naslouchací proces trasování, který určuje typ naslouchacího procesu, nikoli pouze název naslouchacího procesu definovaného v [\<sharedListeners>](sharedlisteners-element.md) .</span><span class="sxs-lookup"><span data-stu-id="a3ad6-128">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="a3ad6-129">Pokud je naslouchací proces definován v [\<sharedListeners>](sharedlisteners-element.md) , musí být v tomto elementu definován filtr pro tento naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-129">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="a3ad6-130">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a3ad6-130">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3ad6-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3ad6-131">Example</span></span>  
 <span data-ttu-id="a3ad6-132">Následující příklad ukazuje, jak použít `<filter>` element pro přidání filtru do naslouchacího procesu `console` v `Listeners` kolekci pro trasování, určení úrovně události filtru jako `Error` .</span><span class="sxs-lookup"><span data-stu-id="a3ad6-132">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3ad6-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3ad6-133">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="a3ad6-134">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="a3ad6-134">Trace and Debug Settings Schema</span></span>](index.md)
