---
title: Element <sources>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
ms.openlocfilehash: 2a76816ee73f516b3c7544877a77531acaa8e09c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153266"
---
# <a name="sources-element"></a><span data-ttu-id="e72a0-102">\<zdroje> Element</span><span class="sxs-lookup"><span data-stu-id="e72a0-102">\<sources> Element</span></span>
<span data-ttu-id="e72a0-103">Určuje zdroje trasování, které iniciují zprávy trasování.</span><span class="sxs-lookup"><span data-stu-id="e72a0-103">Specifies trace sources that initiate tracing messages.</span></span>  

<span data-ttu-id="e72a0-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e72a0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e72a0-105">&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="e72a0-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="e72a0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<zdroje>**</span><span class="sxs-lookup"><span data-stu-id="e72a0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e72a0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e72a0-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e72a0-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e72a0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e72a0-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e72a0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e72a0-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e72a0-110">Attributes</span></span>  
 <span data-ttu-id="e72a0-111">Žádné.</span><span class="sxs-lookup"><span data-stu-id="e72a0-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e72a0-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e72a0-112">Child Elements</span></span>  
  
|<span data-ttu-id="e72a0-113">Element</span><span class="sxs-lookup"><span data-stu-id="e72a0-113">Element</span></span>|<span data-ttu-id="e72a0-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e72a0-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e72a0-115">\<zdrojové></span><span class="sxs-lookup"><span data-stu-id="e72a0-115">\<source></span></span>](source-element.md)|<span data-ttu-id="e72a0-116">Požadovaný element.</span><span class="sxs-lookup"><span data-stu-id="e72a0-116">Required element.</span></span><br /><br /> <span data-ttu-id="e72a0-117">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="e72a0-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e72a0-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e72a0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e72a0-119">Element</span><span class="sxs-lookup"><span data-stu-id="e72a0-119">Element</span></span>|<span data-ttu-id="e72a0-120">Popis</span><span class="sxs-lookup"><span data-stu-id="e72a0-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e72a0-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e72a0-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e72a0-122">Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="e72a0-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e72a0-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e72a0-123">Remarks</span></span>  
 <span data-ttu-id="e72a0-124">Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="e72a0-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e72a0-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="e72a0-125">Example</span></span>  
 <span data-ttu-id="e72a0-126">Následující příklad ukazuje, jak `<sources>` pomocí prvku přidat `mySource` zdroj trasování a nastavit `sourceSwitch`úroveň pro zdrojový přepínač s názvem .</span><span class="sxs-lookup"><span data-stu-id="e72a0-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="e72a0-127">Je přidán naslouchací proces trasování konzoly, který zapisuje informace o trasování do konzoly.</span><span class="sxs-lookup"><span data-stu-id="e72a0-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e72a0-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="e72a0-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="e72a0-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="e72a0-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e72a0-130">\<zdrojové></span><span class="sxs-lookup"><span data-stu-id="e72a0-130">\<source></span></span>](source-element.md)
