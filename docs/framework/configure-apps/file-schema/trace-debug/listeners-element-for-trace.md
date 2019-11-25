---
title: <listeners> – element pro <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 10530cfadf2e182f912c699e50294af4b57f47b5
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088866"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="5ac95-102">> elementu \<Listeners pro \<trasování ></span><span class="sxs-lookup"><span data-stu-id="5ac95-102">\<listeners> Element for \<trace></span></span>
<span data-ttu-id="5ac95-103">Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy.</span><span class="sxs-lookup"><span data-stu-id="5ac95-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="5ac95-104">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="5ac95-104">Listeners direct the tracing output to an appropriate target.</span></span>  

<span data-ttu-id="5ac95-105">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5ac95-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5ac95-106">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="5ac95-106">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="5ac95-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="5ac95-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="5ac95-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<listeners >**</span><span class="sxs-lookup"><span data-stu-id="5ac95-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5ac95-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ac95-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ac95-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5ac95-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ac95-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5ac95-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ac95-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="5ac95-112">Attributes</span></span>  
 <span data-ttu-id="5ac95-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="5ac95-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5ac95-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5ac95-114">Child Elements</span></span>  
  
|<span data-ttu-id="5ac95-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ac95-115">Element</span></span>|<span data-ttu-id="5ac95-116">Popis</span><span class="sxs-lookup"><span data-stu-id="5ac95-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ac95-117">\<přidat ></span><span class="sxs-lookup"><span data-stu-id="5ac95-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="5ac95-118">Přidá naslouchací proces do kolekce `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="5ac95-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="5ac95-119">\<vymazat ></span><span class="sxs-lookup"><span data-stu-id="5ac95-119">\<clear></span></span>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="5ac95-120">Vymaže kolekci `Listeners` pro trasování.</span><span class="sxs-lookup"><span data-stu-id="5ac95-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="5ac95-121">\<odebrat ></span><span class="sxs-lookup"><span data-stu-id="5ac95-121">\<remove></span></span>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="5ac95-122">Odebere naslouchací proces z kolekce `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="5ac95-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ac95-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5ac95-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5ac95-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ac95-124">Element</span></span>|<span data-ttu-id="5ac95-125">Popis</span><span class="sxs-lookup"><span data-stu-id="5ac95-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5ac95-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5ac95-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5ac95-127">Určuje kořenový element konfiguračního oddílu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5ac95-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="5ac95-128">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="5ac95-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ac95-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ac95-129">Remarks</span></span>  
 <span data-ttu-id="5ac95-130">Třídy <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> sdílejí stejnou kolekci **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="5ac95-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="5ac95-131">Pokud přidáte objekt naslouchacího procesu do kolekce v jedné z těchto tříd, použije druhá třída stejný naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="5ac95-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="5ac95-132">Třídy naslouchacího procesu dodávané s .NET Framework jsou odvozeny z <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="5ac95-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="5ac95-133">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="5ac95-133">Configuration File</span></span>  
 <span data-ttu-id="5ac95-134">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="5ac95-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ac95-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ac95-135">Example</span></span>  
 <span data-ttu-id="5ac95-136">Následující příklad ukazuje, jak použít > elementu **\<Listeners** k přidání `MyListener` posluchačů a `MyEventListener` do kolekce **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="5ac95-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="5ac95-137">`MyListener` vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="5ac95-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="5ac95-138">`MyEventListener` vytvoří položku v protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="5ac95-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ac95-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ac95-139">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="5ac95-140">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="5ac95-140">Trace and Debug Settings Schema</span></span>](index.md)
