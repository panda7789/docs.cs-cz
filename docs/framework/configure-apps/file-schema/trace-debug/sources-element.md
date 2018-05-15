---
title: '&lt;zdroje&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 73fe0fb13c191843516a2218c708851abc1851b0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltsourcesgt-element"></a><span data-ttu-id="79157-102">&lt;zdroje&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="79157-102">&lt;sources&gt; Element</span></span>
<span data-ttu-id="79157-103">Určuje trasování zdrojů, které zahájí trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="79157-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
 <span data-ttu-id="79157-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="79157-104">\<configuration></span></span>  
<span data-ttu-id="79157-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="79157-105">\<system.diagnostics></span></span>  
<span data-ttu-id="79157-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="79157-106">\<sources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79157-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79157-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79157-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="79157-108">Attributes and Elements</span></span>  
 <span data-ttu-id="79157-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="79157-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79157-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="79157-110">Attributes</span></span>  
 <span data-ttu-id="79157-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="79157-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="79157-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="79157-112">Child Elements</span></span>  
  
|<span data-ttu-id="79157-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="79157-113">Element</span></span>|<span data-ttu-id="79157-114">Popis</span><span class="sxs-lookup"><span data-stu-id="79157-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79157-115">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="79157-115">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="79157-116">Požadovaný element.</span><span class="sxs-lookup"><span data-stu-id="79157-116">Required element.</span></span><br /><br /> <span data-ttu-id="79157-117">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="79157-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="79157-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="79157-118">Parent Elements</span></span>  
  
|<span data-ttu-id="79157-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="79157-119">Element</span></span>|<span data-ttu-id="79157-120">Popis</span><span class="sxs-lookup"><span data-stu-id="79157-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="79157-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="79157-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="79157-122">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="79157-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79157-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79157-123">Remarks</span></span>  
 <span data-ttu-id="79157-124">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="79157-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79157-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="79157-125">Example</span></span>  
 <span data-ttu-id="79157-126">Následující příklad ukazuje, jak používat `<sources>` elementu, který chcete přidat zdroj trasování `mySource` a nastaví úroveň přepínač zdroje s názvem `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="79157-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="79157-127">Naslouchací proces trasování konzoly je přidaná který informace trasování zapíše do konzoly.</span><span class="sxs-lookup"><span data-stu-id="79157-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="mySource" switchName="sourceSwitch"   
            switchType="System.Diagnostics.SourceSwitch"  >  
            <listeners>  
               <add name="console"   
                  type="System.Diagnostics.ConsoleTraceListener" >  
                  <filter type="System.Diagnostics.EventTypeFilter"   
                     initializeData="Error" />  
               </add>  
               <remove name="Default" />  
            </listeners>  
         </source>  
      </sources>  
      <switches>  
         <add name="sourceSwitch" value="Warning" />  
      </switches>    
   </system.diagnostics>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="79157-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="79157-128">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 [<span data-ttu-id="79157-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="79157-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="79157-130">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="79157-130">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)
