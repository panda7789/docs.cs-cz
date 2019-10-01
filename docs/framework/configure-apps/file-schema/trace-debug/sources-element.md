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
ms.openlocfilehash: 0ca35d9be5e1eaf36a2c9cae99efc2736ef3403d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699212"
---
# <a name="sources-element"></a><span data-ttu-id="5959e-102">@no__t – element > 0sources</span><span class="sxs-lookup"><span data-stu-id="5959e-102">\<sources> Element</span></span>
<span data-ttu-id="5959e-103">Určuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="5959e-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
[<span data-ttu-id="5959e-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="5959e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="5959e-105">&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="5959e-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="5959e-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<sources >**</span><span class="sxs-lookup"><span data-stu-id="5959e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5959e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5959e-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5959e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5959e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5959e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5959e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5959e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="5959e-110">Attributes</span></span>  
 <span data-ttu-id="5959e-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="5959e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5959e-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5959e-112">Child Elements</span></span>  
  
|<span data-ttu-id="5959e-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="5959e-113">Element</span></span>|<span data-ttu-id="5959e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5959e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5959e-115">@no__t – 1source ></span><span class="sxs-lookup"><span data-stu-id="5959e-115">\<source></span></span>](source-element.md)|<span data-ttu-id="5959e-116">Požadovaný element.</span><span class="sxs-lookup"><span data-stu-id="5959e-116">Required element.</span></span><br /><br /> <span data-ttu-id="5959e-117">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="5959e-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5959e-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5959e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5959e-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="5959e-119">Element</span></span>|<span data-ttu-id="5959e-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5959e-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5959e-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5959e-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5959e-122">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="5959e-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5959e-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5959e-123">Remarks</span></span>  
 <span data-ttu-id="5959e-124">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="5959e-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5959e-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="5959e-125">Example</span></span>  
 <span data-ttu-id="5959e-126">Následující příklad ukazuje způsob použití prvku `<sources>` pro přidání zdroje trasování `mySource` a nastavení úrovně pro zdrojový přepínač s názvem `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="5959e-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="5959e-127">Je přidán naslouchací proces trasování konzoly, který zapisuje trasovací informace do konzoly.</span><span class="sxs-lookup"><span data-stu-id="5959e-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5959e-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5959e-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="5959e-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="5959e-129">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5959e-130">@no__t – 1source ></span><span class="sxs-lookup"><span data-stu-id="5959e-130">\<source></span></span>](source-element.md)
