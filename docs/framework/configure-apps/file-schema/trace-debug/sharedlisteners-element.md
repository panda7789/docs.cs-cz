---
title: '&lt;sharedListeners&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 3069022287d469704cc7adac40d02ef3c6997b56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563042"
---
# <a name="ltsharedlistenersgt-element"></a><span data-ttu-id="d871d-102">&lt;sharedListeners&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="d871d-102">&lt;sharedListeners&gt; Element</span></span>
<span data-ttu-id="d871d-103">Obsahuje moduly pro naslouchání, které všechny zdroje nebo trasování – element může odkazovat.</span><span class="sxs-lookup"><span data-stu-id="d871d-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="d871d-104">Tyto moduly pro naslouchání se nezobrazí žádné trasování ve výchozím nastavení a není možné načíst tyto moduly pro naslouchání v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d871d-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="d871d-105">Naslouchací procesy, které jsou identifikovány jako sdílené moduly pro naslouchání lze přidat do zdroje nebo trasování podle názvu.</span><span class="sxs-lookup"><span data-stu-id="d871d-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
 <span data-ttu-id="d871d-106">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="d871d-106">\<configuration></span></span>  
<span data-ttu-id="d871d-107">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="d871d-107">\<system.diagnostics></span></span>  
<span data-ttu-id="d871d-108">\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="d871d-108">\<sharedListeners></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d871d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d871d-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d871d-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d871d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d871d-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d871d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d871d-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d871d-112">Attributes</span></span>  
 <span data-ttu-id="d871d-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="d871d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d871d-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d871d-114">Child Elements</span></span>  
  
|<span data-ttu-id="d871d-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="d871d-115">Element</span></span>|<span data-ttu-id="d871d-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d871d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d871d-117">\<add></span><span class="sxs-lookup"><span data-stu-id="d871d-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="d871d-118">Přidá naslouchací proces pro `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="d871d-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d871d-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d871d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d871d-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="d871d-120">Element</span></span>|<span data-ttu-id="d871d-121">Popis</span><span class="sxs-lookup"><span data-stu-id="d871d-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="d871d-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d871d-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d871d-123">Určuje kořenový element části o konfiguraci technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d871d-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d871d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d871d-124">Remarks</span></span>  
 <span data-ttu-id="d871d-125">Přidání posluchače do sdílené kolekce posluchačů neprovede aktivní naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="d871d-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="d871d-126">Musí stále se přidá do zdroje trasování nebo trasování tak, že přidáte tak, `Listeners` kolekce pro daný element trasování.</span><span class="sxs-lookup"><span data-stu-id="d871d-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="d871d-127">Naslouchací proces třídy v rozhraní .NET Framework jsou odvozeny od <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="d871d-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="d871d-128">Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="d871d-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d871d-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="d871d-129">Example</span></span>  
 <span data-ttu-id="d871d-130">Následující příklad ukazuje způsob použití `<sharedListeners>` prvek a přidat naslouchací proces `console` k `Listeners` kolekce pro obě <xref:System.Diagnostics.TraceSource> a <xref:System.Diagnostics.Trace> třídy.</span><span class="sxs-lookup"><span data-stu-id="d871d-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="d871d-131">Naslouchacího procesu trasování konzoly informace trasování zapíše do konzoly pomocí volání na buď <xref:System.Diagnostics.TraceSource> nebo <xref:System.Diagnostics.Trace>.</span><span class="sxs-lookup"><span data-stu-id="d871d-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration></system.diagnostics>   
```  
  
## <a name="see-also"></a><span data-ttu-id="d871d-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d871d-132">See also</span></span>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="d871d-133">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="d871d-133">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="d871d-134">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="d871d-134">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
