---
title: <filter>Prvek <add> pro pro<sharedListeners>
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
ms.openlocfilehash: 6fb52cdfa5792ab6059b60d8dbb91c107cd666ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153450"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="03a24-102">\<filtr> \<Element pro \<přidání> pro> sharedListeners</span><span class="sxs-lookup"><span data-stu-id="03a24-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="03a24-103">Přidá filtr do naslouchací proces v kolekci. `sharedListeners`</span><span class="sxs-lookup"><span data-stu-id="03a24-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

<span data-ttu-id="03a24-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="03a24-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="03a24-105">&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="03a24-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="03a24-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="03a24-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="03a24-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<přidat>**](add-element-for-sharedlisteners.md)</span><span class="sxs-lookup"><span data-stu-id="03a24-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)</span></span>\
<span data-ttu-id="03a24-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>filtru**</span><span class="sxs-lookup"><span data-stu-id="03a24-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="03a24-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03a24-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03a24-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03a24-110">Attributes and Elements</span></span>  
 <span data-ttu-id="03a24-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03a24-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03a24-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="03a24-112">Attributes</span></span>  
  
|<span data-ttu-id="03a24-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="03a24-113">Attribute</span></span>|<span data-ttu-id="03a24-114">Popis</span><span class="sxs-lookup"><span data-stu-id="03a24-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="03a24-115">**Typ**</span><span class="sxs-lookup"><span data-stu-id="03a24-115">**type**</span></span>|<span data-ttu-id="03a24-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="03a24-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="03a24-117">Určuje typ filtru.</span><span class="sxs-lookup"><span data-stu-id="03a24-117">Specifies the type of the filter.</span></span> <span data-ttu-id="03a24-118">Můžete použít pouze úplný název typu (ve formátu <xref:System.Type.FullName%2A?displayProperty=nameWithType> vlastnosti), nebo můžete použít plně kvalifikovaný název typu včetně <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> informací o sestavení (ve formátu vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="03a24-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="03a24-119">Informace o vytvoření plně kvalifikovaného názvu typu naleznete [v tématu Určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="03a24-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="03a24-120">**inicializovatData**</span><span class="sxs-lookup"><span data-stu-id="03a24-120">**initializeData**</span></span>|<span data-ttu-id="03a24-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="03a24-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="03a24-122">Řetězec předán konstruktoru pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="03a24-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03a24-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03a24-123">Child Elements</span></span>  
 <span data-ttu-id="03a24-124">Žádné.</span><span class="sxs-lookup"><span data-stu-id="03a24-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03a24-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03a24-125">Parent Elements</span></span>  
  
|<span data-ttu-id="03a24-126">Element</span><span class="sxs-lookup"><span data-stu-id="03a24-126">Element</span></span>|<span data-ttu-id="03a24-127">Popis</span><span class="sxs-lookup"><span data-stu-id="03a24-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="03a24-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03a24-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="03a24-129">Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="03a24-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="03a24-130">Kolekce naslouchacích procesy, které může odkazovat libovolný zdroj nebo prvek trasování.</span><span class="sxs-lookup"><span data-stu-id="03a24-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="03a24-131">Přidá naslouchací proces do kolekce **sharedListeners.**</span><span class="sxs-lookup"><span data-stu-id="03a24-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03a24-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03a24-132">Remarks</span></span>  
 <span data-ttu-id="03a24-133">Pokud je definován `<add>` naslouchací proces v prvku `<sharedListeners>` prvku, `<filter>` filtr pro tento naslouchací proces by měl být definován v elementu, který je podřízeným `<add>` prvkem prvku.</span><span class="sxs-lookup"><span data-stu-id="03a24-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="03a24-134">Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="03a24-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03a24-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="03a24-135">Example</span></span>  
 <span data-ttu-id="03a24-136">Následující příklad ukazuje, jak `<filter>` použít prvek k přidání `console` filtru `sharedListeners` do naslouchací proces trasování v kolekci.</span><span class="sxs-lookup"><span data-stu-id="03a24-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03a24-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="03a24-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="03a24-138">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="03a24-138">Trace and Debug Settings Schema</span></span>](index.md)
