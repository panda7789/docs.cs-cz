---
title: <clear>Prvek <listeners> pro pro<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 7f9ddd93d27c3619119702c82c9e8752dab1af7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153578"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="5cdf7-102">\<vymazat> \<element pro \<posluchače> pro zdrojové></span><span class="sxs-lookup"><span data-stu-id="5cdf7-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="5cdf7-103">Vymaže kolekci `Listeners` pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="5cdf7-103">Clears the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="5cdf7-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5cdf7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5cdf7-105">&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="5cdf7-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="5cdf7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdroje>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="5cdf7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="5cdf7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdrojové>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="5cdf7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="5cdf7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<posluchači>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="5cdf7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="5cdf7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<jasné>**</span><span class="sxs-lookup"><span data-stu-id="5cdf7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5cdf7-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cdf7-110">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5cdf7-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5cdf7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5cdf7-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5cdf7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5cdf7-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="5cdf7-113">Attributes</span></span>  
 <span data-ttu-id="5cdf7-114">Žádné.</span><span class="sxs-lookup"><span data-stu-id="5cdf7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5cdf7-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5cdf7-115">Child Elements</span></span>  
 <span data-ttu-id="5cdf7-116">Žádné.</span><span class="sxs-lookup"><span data-stu-id="5cdf7-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5cdf7-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5cdf7-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5cdf7-118">Element</span><span class="sxs-lookup"><span data-stu-id="5cdf7-118">Element</span></span>|<span data-ttu-id="5cdf7-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5cdf7-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5cdf7-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5cdf7-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5cdf7-121">Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="5cdf7-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="5cdf7-122">Obsahuje zdroje trasování, které iniciují tracing zprávy.</span><span class="sxs-lookup"><span data-stu-id="5cdf7-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="5cdf7-123">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="5cdf7-123">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="5cdf7-124">Určuje posluchače, kteří shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="5cdf7-124">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cdf7-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5cdf7-125">Remarks</span></span>  
 <span data-ttu-id="5cdf7-126">Prvek `<clear>` odebere všechny naslouchací `Listeners` procesy <xref:System.Diagnostics.DefaultTraceListener>z kolekce pro zdroj trasování, včetně .</span><span class="sxs-lookup"><span data-stu-id="5cdf7-126">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="5cdf7-127">Prvek můžete `<clear>` použít před `<add>` použitím prvku být jisti, že neexistují žádné další aktivní posluchače v kolekci.</span><span class="sxs-lookup"><span data-stu-id="5cdf7-127">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="5cdf7-128">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="5cdf7-128">Configuration File</span></span>  
 <span data-ttu-id="5cdf7-129">Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="5cdf7-129">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cdf7-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="5cdf7-130">Example</span></span>  
 <span data-ttu-id="5cdf7-131">Následující příklad ukazuje, jak `<clear>` použít prvek `<add>` před použitím elementů `textListener` k `Listeners` přidání posluchačů `TraceSourceApp` `console` a do kolekce pro zdroj trasování .</span><span class="sxs-lookup"><span data-stu-id="5cdf7-131">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="5cdf7-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cdf7-132">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="5cdf7-133">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="5cdf7-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5cdf7-134">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="5cdf7-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
