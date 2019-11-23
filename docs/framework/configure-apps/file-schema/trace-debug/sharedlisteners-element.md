---
title: Element <sharedListeners>
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
ms.openlocfilehash: b419ecf451b79808e545525c7b8761175f390200
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699292"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="03cf3-102">> prvek \<sharedListeners</span><span class="sxs-lookup"><span data-stu-id="03cf3-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="03cf3-103">Obsahuje naslouchací procesy, na které může odkazovat jakýkoliv element source nebo Trace.</span><span class="sxs-lookup"><span data-stu-id="03cf3-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="03cf3-104">Tyto naslouchací procesy neobdrží žádné trasování ve výchozím nastavení a není možné načíst tyto naslouchací procesy v době běhu.</span><span class="sxs-lookup"><span data-stu-id="03cf3-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="03cf3-105">Naslouchací procesy identifikované jako sdílené naslouchací procesy lze přidat do zdrojů nebo trasování podle názvu.</span><span class="sxs-lookup"><span data-stu-id="03cf3-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[<span data-ttu-id="03cf3-106">**Konfigurace \<>** </span><span class="sxs-lookup"><span data-stu-id="03cf3-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="03cf3-107">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="03cf3-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="03cf3-108">&nbsp;&nbsp;&nbsp;&nbsp; **\<sharedListeners >**</span><span class="sxs-lookup"><span data-stu-id="03cf3-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03cf3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03cf3-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03cf3-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03cf3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="03cf3-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03cf3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03cf3-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="03cf3-112">Attributes</span></span>  
 <span data-ttu-id="03cf3-113">Žádné.</span><span class="sxs-lookup"><span data-stu-id="03cf3-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="03cf3-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03cf3-114">Child Elements</span></span>  
  
|<span data-ttu-id="03cf3-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="03cf3-115">Element</span></span>|<span data-ttu-id="03cf3-116">Popis</span><span class="sxs-lookup"><span data-stu-id="03cf3-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03cf3-117">\<add></span><span class="sxs-lookup"><span data-stu-id="03cf3-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="03cf3-118">Přidá naslouchací proces do kolekce `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="03cf3-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="03cf3-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03cf3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="03cf3-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="03cf3-120">Element</span></span>|<span data-ttu-id="03cf3-121">Popis</span><span class="sxs-lookup"><span data-stu-id="03cf3-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="03cf3-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03cf3-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="03cf3-123">Určuje kořenový element konfiguračního oddílu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="03cf3-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03cf3-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03cf3-124">Remarks</span></span>  
 <span data-ttu-id="03cf3-125">Přidání naslouchacího procesu do kolekce Shared Listeners neprovádí aktivní naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="03cf3-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="03cf3-126">Ještě musí být přidán do zdroje trasování nebo do trasování přidáním do kolekce `Listeners` pro daný prvek Trace.</span><span class="sxs-lookup"><span data-stu-id="03cf3-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="03cf3-127">Třídy naslouchacího procesu v .NET Framework jsou odvozeny z <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="03cf3-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="03cf3-128">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="03cf3-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03cf3-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="03cf3-129">Example</span></span>  
 <span data-ttu-id="03cf3-130">Následující příklad ukazuje způsob použití prvku `<sharedListeners>` k přidání `console` naslouchacího procesu do kolekce `Listeners` pro třídy <xref:System.Diagnostics.TraceSource> a <xref:System.Diagnostics.Trace>.</span><span class="sxs-lookup"><span data-stu-id="03cf3-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="03cf3-131">Naslouchací proces trasování konzoly zapisuje trasovací informace do konzoly prostřednictvím volání buď <xref:System.Diagnostics.TraceSource> nebo <xref:System.Diagnostics.Trace>.</span><span class="sxs-lookup"><span data-stu-id="03cf3-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="03cf3-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03cf3-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="03cf3-133">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="03cf3-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="03cf3-134">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="03cf3-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
