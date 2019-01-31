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
ms.openlocfilehash: d7d92f91838a8d1914ffe574f018cc701477d767
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262501"
---
# <a name="sources-element"></a><span data-ttu-id="ec234-102">\<zdroje > – Element</span><span class="sxs-lookup"><span data-stu-id="ec234-102">\<sources> Element</span></span>
<span data-ttu-id="ec234-103">Určuje zdrojů trasování, které se zahájí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec234-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
 <span data-ttu-id="ec234-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="ec234-104">\<configuration></span></span>  
<span data-ttu-id="ec234-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="ec234-105">\<system.diagnostics></span></span>  
<span data-ttu-id="ec234-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="ec234-106">\<sources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec234-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec234-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec234-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ec234-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ec234-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ec234-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec234-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ec234-110">Attributes</span></span>  
 <span data-ttu-id="ec234-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="ec234-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ec234-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ec234-112">Child Elements</span></span>  
  
|<span data-ttu-id="ec234-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="ec234-113">Element</span></span>|<span data-ttu-id="ec234-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ec234-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec234-115">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="ec234-115">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="ec234-116">Požadovaný element.</span><span class="sxs-lookup"><span data-stu-id="ec234-116">Required element.</span></span><br /><br /> <span data-ttu-id="ec234-117">Určuje zdroj trasování, který iniciuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="ec234-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec234-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ec234-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ec234-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="ec234-119">Element</span></span>|<span data-ttu-id="ec234-120">Popis</span><span class="sxs-lookup"><span data-stu-id="ec234-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ec234-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ec234-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ec234-122">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="ec234-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec234-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec234-123">Remarks</span></span>  
 <span data-ttu-id="ec234-124">Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec234-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec234-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec234-125">Example</span></span>  
 <span data-ttu-id="ec234-126">Následující příklad ukazuje způsob použití `<sources>` prvek a přidat zdroj trasování `mySource` a nastavit úroveň pro přepínač zdroje s názvem `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="ec234-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="ec234-127">Naslouchacího procesu trasování konzoly je přidat informace o trasování, která zapisuje do konzoly.</span><span class="sxs-lookup"><span data-stu-id="ec234-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ec234-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec234-128">See also</span></span>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="ec234-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="ec234-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="ec234-130">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="ec234-130">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)
