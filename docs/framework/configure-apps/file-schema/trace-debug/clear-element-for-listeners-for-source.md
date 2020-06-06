---
title: <clear>Element pro <listeners> pro<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 7f9ddd93d27c3619119702c82c9e8752dab1af7b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153578"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="399f1-102">\<clear>Element pro \<listeners> pro\<source></span><span class="sxs-lookup"><span data-stu-id="399f1-102">\<clear> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="399f1-103">Vymaže `Listeners` kolekci zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="399f1-103">Clears the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="399f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="399f1-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="399f1-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="399f1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="399f1-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="399f1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="399f1-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="399f1-107">Attributes</span></span>  
 <span data-ttu-id="399f1-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="399f1-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="399f1-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="399f1-109">Child Elements</span></span>  
 <span data-ttu-id="399f1-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="399f1-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="399f1-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="399f1-111">Parent Elements</span></span>  
  
|<span data-ttu-id="399f1-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="399f1-112">Element</span></span>|<span data-ttu-id="399f1-113">Description</span><span class="sxs-lookup"><span data-stu-id="399f1-113">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="399f1-114">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="399f1-114">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="399f1-115">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="399f1-115">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="399f1-116">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="399f1-116">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="399f1-117">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="399f1-117">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="399f1-118">Určuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="399f1-118">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="399f1-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="399f1-119">Remarks</span></span>  
 <span data-ttu-id="399f1-120">`<clear>`Prvek odebere všechny naslouchací procesy z `Listeners` kolekce pro zdroj trasování, včetně <xref:System.Diagnostics.DefaultTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="399f1-120">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="399f1-121">Element lze použít `<clear>` před použitím `<add>` prvku, aby bylo jisté, že v kolekci nejsou žádné další aktivní naslouchací procesy.</span><span class="sxs-lookup"><span data-stu-id="399f1-121">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="399f1-122">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="399f1-122">Configuration File</span></span>  
 <span data-ttu-id="399f1-123">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="399f1-123">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="399f1-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="399f1-124">Example</span></span>  
 <span data-ttu-id="399f1-125">Následující příklad ukazuje, jak použít `<clear>` element před použitím `<add>` prvků pro přidání posluchačů `console` a `textListener` do `Listeners` kolekce pro zdroj trasování `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="399f1-125">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="399f1-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="399f1-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="399f1-127">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="399f1-127">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="399f1-128">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="399f1-128">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
