---
title: "&lt;zdroje&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 58e9ff8787916132406a7e63aff511c9fb221b73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltsourcesgt-element"></a><span data-ttu-id="d7372-102">&lt;zdroje&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="d7372-102">&lt;sources&gt; Element</span></span>
<span data-ttu-id="d7372-103">Určuje trasování zdrojů, které zahájí trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="d7372-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
 <span data-ttu-id="d7372-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="d7372-104">\<configuration></span></span>  
<span data-ttu-id="d7372-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="d7372-105">\<system.diagnostics></span></span>  
<span data-ttu-id="d7372-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="d7372-106">\<sources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7372-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7372-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7372-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d7372-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d7372-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d7372-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7372-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d7372-110">Attributes</span></span>  
 <span data-ttu-id="d7372-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="d7372-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d7372-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d7372-112">Child Elements</span></span>  
  
|<span data-ttu-id="d7372-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="d7372-113">Element</span></span>|<span data-ttu-id="d7372-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d7372-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7372-115">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="d7372-115">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="d7372-116">Požadovaný element.</span><span class="sxs-lookup"><span data-stu-id="d7372-116">Required element.</span></span><br /><br /> <span data-ttu-id="d7372-117">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="d7372-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7372-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d7372-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d7372-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="d7372-119">Element</span></span>|<span data-ttu-id="d7372-120">Popis</span><span class="sxs-lookup"><span data-stu-id="d7372-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d7372-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7372-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d7372-122">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="d7372-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7372-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7372-123">Remarks</span></span>  
 <span data-ttu-id="d7372-124">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="d7372-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7372-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7372-125">Example</span></span>  
 <span data-ttu-id="d7372-126">Následující příklad ukazuje, jak používat `<sources>` elementu, který chcete přidat zdroj trasování `mySource` a nastaví úroveň přepínač zdroje s názvem `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="d7372-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="d7372-127">Naslouchací proces trasování konzoly je přidaná který informace trasování zapíše do konzoly.</span><span class="sxs-lookup"><span data-stu-id="d7372-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d7372-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7372-128">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 [<span data-ttu-id="d7372-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="d7372-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="d7372-130">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="d7372-130">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)
