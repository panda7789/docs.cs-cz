---
title: <filter> element pro <add> pro <sharedListeners>
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
ms.openlocfilehash: 4e92f80e9f6069b5fa70501e13a55d5a6fe95e7a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697328"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="cceb8-102">> element \<filter pro \<add > pro \<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="cceb8-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="cceb8-103">Přidá filtr do naslouchacího procesu v kolekci `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="cceb8-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
[<span data-ttu-id="cceb8-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="cceb8-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="cceb8-105">&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="cceb8-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="cceb8-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sharedListeners >** ](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="cceb8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>  
<span data-ttu-id="cceb8-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<add >** ](add-element-for-sharedlisteners.md)</span><span class="sxs-lookup"><span data-stu-id="cceb8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)</span></span>  
<span data-ttu-id="cceb8-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<filter >**</span><span class="sxs-lookup"><span data-stu-id="cceb8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cceb8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cceb8-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cceb8-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cceb8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cceb8-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cceb8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cceb8-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="cceb8-112">Attributes</span></span>  
  
|<span data-ttu-id="cceb8-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="cceb8-113">Attribute</span></span>|<span data-ttu-id="cceb8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="cceb8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cceb8-115">**textový**</span><span class="sxs-lookup"><span data-stu-id="cceb8-115">**type**</span></span>|<span data-ttu-id="cceb8-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="cceb8-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="cceb8-117">Určuje typ filtru.</span><span class="sxs-lookup"><span data-stu-id="cceb8-117">Specifies the type of the filter.</span></span> <span data-ttu-id="cceb8-118">Můžete použít pouze úplný název typu (ve formátu vlastnosti <xref:System.Type.FullName%2A?displayProperty=nameWithType>), nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení (ve formátu <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="cceb8-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="cceb8-119">Informace o vytvoření plně kvalifikovaného názvu typu naleznete v tématu [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="cceb8-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="cceb8-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="cceb8-120">**initializeData**</span></span>|<span data-ttu-id="cceb8-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="cceb8-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="cceb8-122">Řetězec předaný konstruktoru pro určenou třídu.</span><span class="sxs-lookup"><span data-stu-id="cceb8-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cceb8-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cceb8-123">Child Elements</span></span>  
 <span data-ttu-id="cceb8-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="cceb8-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cceb8-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cceb8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="cceb8-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="cceb8-126">Element</span></span>|<span data-ttu-id="cceb8-127">Popis</span><span class="sxs-lookup"><span data-stu-id="cceb8-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cceb8-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cceb8-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="cceb8-129">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="cceb8-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="cceb8-130">Kolekce posluchačů, na které může odkazovat jakýkoliv element source nebo Trace.</span><span class="sxs-lookup"><span data-stu-id="cceb8-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="cceb8-131">Přidá naslouchací proces do kolekce **sharedListeners** .</span><span class="sxs-lookup"><span data-stu-id="cceb8-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cceb8-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cceb8-132">Remarks</span></span>  
 <span data-ttu-id="cceb8-133">Pokud je naslouchací proces definován v elementu `<add>` elementu `<sharedListeners>`, filtr pro tento naslouchací proces by měl být definován v prvku `<filter>`, který je podřízenou položkou prvku `<add>`.</span><span class="sxs-lookup"><span data-stu-id="cceb8-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="cceb8-134">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="cceb8-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cceb8-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="cceb8-135">Example</span></span>  
 <span data-ttu-id="cceb8-136">Následující příklad ukazuje způsob použití prvku `<filter>` pro přidání filtru do naslouchacího procesu trasování `console` v kolekci `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="cceb8-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cceb8-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cceb8-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="cceb8-138">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="cceb8-138">Trace and Debug Settings Schema</span></span>](index.md)
