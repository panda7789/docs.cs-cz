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
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153318"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="6d820-102">Element \<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="6d820-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="6d820-103">Obsahuje naslouchací procesy, na které může odkazovat jakýkoliv element source nebo Trace.</span><span class="sxs-lookup"><span data-stu-id="6d820-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="6d820-104">Tyto naslouchací procesy neobdrží žádné trasování ve výchozím nastavení a není možné načíst tyto naslouchací procesy v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6d820-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="6d820-105">Naslouchací procesy identifikované jako sdílené naslouchací procesy lze přidat do zdrojů nebo trasování podle názvu.</span><span class="sxs-lookup"><span data-stu-id="6d820-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**  
  
## <a name="syntax"></a><span data-ttu-id="6d820-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d820-106">Syntax</span></span>  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d820-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6d820-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6d820-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6d820-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d820-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="6d820-109">Attributes</span></span>  
 <span data-ttu-id="6d820-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="6d820-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6d820-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6d820-111">Child Elements</span></span>  
  
|<span data-ttu-id="6d820-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="6d820-112">Element</span></span>|<span data-ttu-id="6d820-113">Description</span><span class="sxs-lookup"><span data-stu-id="6d820-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="6d820-114">Přidá naslouchací proces do `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="6d820-114">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6d820-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6d820-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6d820-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="6d820-116">Element</span></span>|<span data-ttu-id="6d820-117">Description</span><span class="sxs-lookup"><span data-stu-id="6d820-117">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="6d820-118">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6d820-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6d820-119">Určuje kořenový element konfiguračního oddílu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6d820-119">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d820-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d820-120">Remarks</span></span>  
 <span data-ttu-id="6d820-121">Přidání naslouchacího procesu do kolekce Shared Listeners neprovádí aktivní naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="6d820-121">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="6d820-122">Ještě musí být přidán do zdroje trasování nebo do trasování tím, že je přidáte do `Listeners` kolekce pro daný prvek Trace.</span><span class="sxs-lookup"><span data-stu-id="6d820-122">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="6d820-123">Třídy naslouchacího procesu v .NET Framework jsou odvozeny z <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="6d820-123">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="6d820-124">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d820-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d820-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d820-125">Example</span></span>  
 <span data-ttu-id="6d820-126">Následující příklad ukazuje, jak použít `<sharedListeners>` element pro přidání naslouchacího procesu `console` do `Listeners` kolekce pro <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace> třídy a.</span><span class="sxs-lookup"><span data-stu-id="6d820-126">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="6d820-127">Naslouchací proces trasování konzoly zapisuje trasovací informace do konzoly prostřednictvím volání <xref:System.Diagnostics.TraceSource> nebo <xref:System.Diagnostics.Trace> .</span><span class="sxs-lookup"><span data-stu-id="6d820-127">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6d820-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d820-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="6d820-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="6d820-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6d820-130">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="6d820-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
