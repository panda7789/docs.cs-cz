---
title: <listeners> – element pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 0eee325e01b41a15a19e4f40f479596f9d70f73b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153409"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="6ff35-102">\<listeners> – element pro \<source></span><span class="sxs-lookup"><span data-stu-id="6ff35-102">\<listeners> Element for \<source></span></span>
<span data-ttu-id="6ff35-103">Přidá nebo odebere naslouchací procesy v <xref:System.Diagnostics.TraceSource.Listeners%2A> kolekci pro <xref:System.Diagnostics.TraceSource> .</span><span class="sxs-lookup"><span data-stu-id="6ff35-103">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="6ff35-104">Naslouchací proces směruje výstup trasování do příslušného cíle, jako je protokol, okno nebo textový soubor.</span><span class="sxs-lookup"><span data-stu-id="6ff35-104">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**  
  
## <a name="syntax"></a><span data-ttu-id="6ff35-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ff35-105">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ff35-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6ff35-106">Attributes and Elements</span></span>  
 <span data-ttu-id="6ff35-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6ff35-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ff35-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="6ff35-108">Attributes</span></span>  
 <span data-ttu-id="6ff35-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="6ff35-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6ff35-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6ff35-110">Child Elements</span></span>  
  
|<span data-ttu-id="6ff35-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="6ff35-111">Element</span></span>|<span data-ttu-id="6ff35-112">Description</span><span class="sxs-lookup"><span data-stu-id="6ff35-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="6ff35-113">Přidá naslouchací proces do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="6ff35-113">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="6ff35-114">Odebere naslouchací proces z `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="6ff35-114">Removes a listener from the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="6ff35-115">Vymaže `Listeners` kolekci zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="6ff35-115">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6ff35-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6ff35-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6ff35-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="6ff35-117">Element</span></span>|<span data-ttu-id="6ff35-118">Description</span><span class="sxs-lookup"><span data-stu-id="6ff35-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6ff35-119">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ff35-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="6ff35-120">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="6ff35-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="6ff35-121">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="6ff35-121">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="6ff35-122">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="6ff35-122">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ff35-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ff35-123">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="6ff35-124">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="6ff35-124">Configuration File</span></span>  
 <span data-ttu-id="6ff35-125">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ff35-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ff35-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ff35-126">Example</span></span>  
 <span data-ttu-id="6ff35-127">Následující příklad ukazuje, jak použít `<listeners>` element k přidání naslouchacího procesu trasování konzoly ke `mySource` zdroji a k odebrání výchozího naslouchacího procesu trasování.</span><span class="sxs-lookup"><span data-stu-id="6ff35-127">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ff35-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ff35-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="6ff35-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="6ff35-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6ff35-130">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="6ff35-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
