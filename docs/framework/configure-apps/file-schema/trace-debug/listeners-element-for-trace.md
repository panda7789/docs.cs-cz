---
title: <listeners> – element pro <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: fd12be1b775d7611ef3f16d23147470313bf9866
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153370"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="d761f-102">\<listeners> – element pro \<trace></span><span class="sxs-lookup"><span data-stu-id="d761f-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="d761f-103">Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy.</span><span class="sxs-lookup"><span data-stu-id="d761f-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="d761f-104">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="d761f-104">Listeners direct the tracing output to an appropriate target.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**

## <a name="syntax"></a><span data-ttu-id="d761f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d761f-105">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d761f-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d761f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d761f-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d761f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d761f-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="d761f-108">Attributes</span></span>  
 <span data-ttu-id="d761f-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="d761f-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d761f-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d761f-110">Child Elements</span></span>  
  
|<span data-ttu-id="d761f-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="d761f-111">Element</span></span>|<span data-ttu-id="d761f-112">Description</span><span class="sxs-lookup"><span data-stu-id="d761f-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="d761f-113">Přidá naslouchací proces do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="d761f-113">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="d761f-114">Vymaže `Listeners` kolekci pro Trace.</span><span class="sxs-lookup"><span data-stu-id="d761f-114">Clears the `Listeners` collection for trace.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="d761f-115">Odebere naslouchací proces z `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="d761f-115">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d761f-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d761f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d761f-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="d761f-117">Element</span></span>|<span data-ttu-id="d761f-118">Description</span><span class="sxs-lookup"><span data-stu-id="d761f-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d761f-119">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d761f-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d761f-120">Určuje kořenový element konfiguračního oddílu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d761f-120">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="d761f-121">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="d761f-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d761f-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d761f-122">Remarks</span></span>  
 <span data-ttu-id="d761f-123"><xref:System.Diagnostics.Debug>Třídy a <xref:System.Diagnostics.Trace> sdílejí stejnou kolekci **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="d761f-123">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="d761f-124">Pokud přidáte objekt naslouchacího procesu do kolekce v jedné z těchto tříd, použije druhá třída stejný naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="d761f-124">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="d761f-125">Třídy naslouchacího procesu dodávané s .NET Framework jsou odvozeny z <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="d761f-125">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="d761f-126">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="d761f-126">Configuration File</span></span>  
 <span data-ttu-id="d761f-127">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="d761f-127">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d761f-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="d761f-128">Example</span></span>  
 <span data-ttu-id="d761f-129">Následující příklad ukazuje, jak použít **\<listeners>** element pro přidání posluchačů `MyListener` a `MyEventListener` do kolekce **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="d761f-129">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="d761f-130">`MyListener`Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="d761f-130">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="d761f-131">`MyEventListener`vytvoří položku v protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="d761f-131">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"
          type="System.Diagnostics.TextWriterTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d761f-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="d761f-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="d761f-133">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="d761f-133">Trace and Debug Settings Schema</span></span>](index.md)
