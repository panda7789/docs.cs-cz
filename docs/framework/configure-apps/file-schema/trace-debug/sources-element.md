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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153266"
---
# <a name="sources-element"></a><span data-ttu-id="744fc-102">Element \<sources></span><span class="sxs-lookup"><span data-stu-id="744fc-102">\<sources> Element</span></span>
<span data-ttu-id="744fc-103">Určuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="744fc-103">Specifies trace sources that initiate tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**

## <a name="syntax"></a><span data-ttu-id="744fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="744fc-104">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="744fc-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="744fc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="744fc-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="744fc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="744fc-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="744fc-107">Attributes</span></span>  
 <span data-ttu-id="744fc-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="744fc-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="744fc-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="744fc-109">Child Elements</span></span>  
  
|<span data-ttu-id="744fc-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="744fc-110">Element</span></span>|<span data-ttu-id="744fc-111">Description</span><span class="sxs-lookup"><span data-stu-id="744fc-111">Description</span></span>|  
|-------------|-----------------|  
|[\<source>](source-element.md)|<span data-ttu-id="744fc-112">Požadovaný element.</span><span class="sxs-lookup"><span data-stu-id="744fc-112">Required element.</span></span><br /><br /> <span data-ttu-id="744fc-113">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="744fc-113">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="744fc-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="744fc-114">Parent Elements</span></span>  
  
|<span data-ttu-id="744fc-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="744fc-115">Element</span></span>|<span data-ttu-id="744fc-116">Description</span><span class="sxs-lookup"><span data-stu-id="744fc-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="744fc-117">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="744fc-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="744fc-118">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="744fc-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="744fc-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="744fc-119">Remarks</span></span>  
 <span data-ttu-id="744fc-120">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="744fc-120">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="744fc-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="744fc-121">Example</span></span>  
 <span data-ttu-id="744fc-122">Následující příklad ukazuje, jak použít `<sources>` element k přidání zdroje trasování `mySource` a k nastavení úrovně pro zdrojový přepínač s názvem `sourceSwitch` .</span><span class="sxs-lookup"><span data-stu-id="744fc-122">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="744fc-123">Je přidán naslouchací proces trasování konzoly, který zapisuje trasovací informace do konzoly.</span><span class="sxs-lookup"><span data-stu-id="744fc-123">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="744fc-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="744fc-124">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="744fc-125">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="744fc-125">Trace and Debug Settings Schema</span></span>](index.md)
- [\<source>](source-element.md)
