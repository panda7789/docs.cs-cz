---
title: <listeners> – element pro <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 84b67532825372e7f69d86e1ef6060f4263587eb
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699353"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="2d9e1-102">> element \<listeners pro \<trace ></span><span class="sxs-lookup"><span data-stu-id="2d9e1-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="2d9e1-103">Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy.</span><span class="sxs-lookup"><span data-stu-id="2d9e1-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="2d9e1-104">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="2d9e1-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
[<span data-ttu-id="2d9e1-105"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="2d9e1-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="2d9e1-106">&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="2d9e1-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="2d9e1-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="2d9e1-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>  
<span data-ttu-id="2d9e1-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<listeners >**</span><span class="sxs-lookup"><span data-stu-id="2d9e1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d9e1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d9e1-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d9e1-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2d9e1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2d9e1-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2d9e1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d9e1-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="2d9e1-112">Attributes</span></span>  
 <span data-ttu-id="2d9e1-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="2d9e1-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2d9e1-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2d9e1-114">Child Elements</span></span>  
  
|<span data-ttu-id="2d9e1-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="2d9e1-115">Element</span></span>|<span data-ttu-id="2d9e1-116">Popis</span><span class="sxs-lookup"><span data-stu-id="2d9e1-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d9e1-117">@no__t – 1add ></span><span class="sxs-lookup"><span data-stu-id="2d9e1-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="2d9e1-118">Přidá naslouchací proces do kolekce `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="2d9e1-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="2d9e1-119">@no__t – 1clear ></span><span class="sxs-lookup"><span data-stu-id="2d9e1-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="2d9e1-120">Vymaže kolekci `Listeners` pro trasování.</span><span class="sxs-lookup"><span data-stu-id="2d9e1-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="2d9e1-121">@no__t – 1remove ></span><span class="sxs-lookup"><span data-stu-id="2d9e1-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="2d9e1-122">Odebere naslouchací proces z kolekce `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="2d9e1-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2d9e1-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2d9e1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2d9e1-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="2d9e1-124">Element</span></span>|<span data-ttu-id="2d9e1-125">Popis</span><span class="sxs-lookup"><span data-stu-id="2d9e1-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2d9e1-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d9e1-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2d9e1-127">Určuje kořenový element konfiguračního oddílu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2d9e1-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="2d9e1-128">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="2d9e1-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d9e1-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d9e1-129">Remarks</span></span>  
 <span data-ttu-id="2d9e1-130">Třídy <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> sdílejí stejnou kolekci **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="2d9e1-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="2d9e1-131">Pokud přidáte objekt naslouchacího procesu do kolekce v jedné z těchto tříd, použije druhá třída stejný naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="2d9e1-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="2d9e1-132">Třídy naslouchacího procesu dodávané s .NET Framework jsou odvozeny z třídy <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="2d9e1-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="2d9e1-133">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="2d9e1-133">Configuration File</span></span>  
 <span data-ttu-id="2d9e1-134">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d9e1-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d9e1-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d9e1-135">Example</span></span>  
 <span data-ttu-id="2d9e1-136">Následující příklad ukazuje, jak použít prvek **> @no__t 1listeners** k přidání posluchačů `MyListener` a `MyEventListener` do kolekce **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="2d9e1-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="2d9e1-137">`MyListener` vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="2d9e1-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="2d9e1-138">`MyEventListener` vytvoří položku v protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="2d9e1-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2d9e1-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d9e1-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="2d9e1-140">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="2d9e1-140">Trace and Debug Settings Schema</span></span>](index.md)
