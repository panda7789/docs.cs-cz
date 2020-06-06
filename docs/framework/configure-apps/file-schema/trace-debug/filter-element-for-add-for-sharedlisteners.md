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
ms.openlocfilehash: 6fb52cdfa5792ab6059b60d8dbb91c107cd666ca
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153450"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="722f6-102">\<filter>Element pro \<add> pro\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="722f6-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="722f6-103">Přidá filtr do naslouchacího procesu v `sharedListeners` kolekci.</span><span class="sxs-lookup"><span data-stu-id="722f6-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="722f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="722f6-104">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="722f6-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="722f6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="722f6-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="722f6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="722f6-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="722f6-107">Attributes</span></span>  
  
|<span data-ttu-id="722f6-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="722f6-108">Attribute</span></span>|<span data-ttu-id="722f6-109">Popis</span><span class="sxs-lookup"><span data-stu-id="722f6-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="722f6-110">**textový**</span><span class="sxs-lookup"><span data-stu-id="722f6-110">**type**</span></span>|<span data-ttu-id="722f6-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="722f6-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="722f6-112">Určuje typ filtru.</span><span class="sxs-lookup"><span data-stu-id="722f6-112">Specifies the type of the filter.</span></span> <span data-ttu-id="722f6-113">Můžete použít pouze úplný název typu (ve formátu <xref:System.Type.FullName%2A?displayProperty=nameWithType> Vlastnosti), nebo můžete použít plně kvalifikovaný název typu včetně informací o sestavení (ve formátu <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> Vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="722f6-113">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="722f6-114">Informace o vytvoření plně kvalifikovaného názvu typu naleznete v tématu [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="722f6-114">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="722f6-115">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="722f6-115">**initializeData**</span></span>|<span data-ttu-id="722f6-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="722f6-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="722f6-117">Řetězec předaný konstruktoru pro určenou třídu.</span><span class="sxs-lookup"><span data-stu-id="722f6-117">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="722f6-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="722f6-118">Child Elements</span></span>  
 <span data-ttu-id="722f6-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="722f6-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="722f6-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="722f6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="722f6-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="722f6-121">Element</span></span>|<span data-ttu-id="722f6-122">Description</span><span class="sxs-lookup"><span data-stu-id="722f6-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="722f6-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="722f6-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="722f6-124">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="722f6-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="722f6-125">Kolekce posluchačů, na které může odkazovat jakýkoliv element source nebo Trace.</span><span class="sxs-lookup"><span data-stu-id="722f6-125">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="722f6-126">Přidá naslouchací proces do kolekce **sharedListeners** .</span><span class="sxs-lookup"><span data-stu-id="722f6-126">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="722f6-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="722f6-127">Remarks</span></span>  
 <span data-ttu-id="722f6-128">Pokud je naslouchací proces definován v `<add>` prvku elementu `<sharedListeners>` , filtr pro tento naslouchací proces by měl být definován v `<filter>` prvku, který je podřízeným `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="722f6-128">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="722f6-129">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="722f6-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="722f6-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="722f6-130">Example</span></span>  
 <span data-ttu-id="722f6-131">Následující příklad ukazuje, jak použít `<filter>` element pro přidání filtru do naslouchacího procesu trasování `console` v `sharedListeners` kolekci.</span><span class="sxs-lookup"><span data-stu-id="722f6-131">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="722f6-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="722f6-132">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="722f6-133">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="722f6-133">Trace and Debug Settings Schema</span></span>](index.md)
