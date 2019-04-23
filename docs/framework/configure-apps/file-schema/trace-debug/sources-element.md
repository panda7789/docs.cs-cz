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
ms.openlocfilehash: 9104a4a302aa9c6094adbc13396074fdd4db4bbc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215778"
---
# <a name="sources-element"></a><span data-ttu-id="25f24-102">\<zdroje > – Element</span><span class="sxs-lookup"><span data-stu-id="25f24-102">\<sources> Element</span></span>
<span data-ttu-id="25f24-103">Určuje zdrojů trasování, které se zahájí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="25f24-103">Specifies trace sources that initiate tracing messages.</span></span>  
  
 <span data-ttu-id="25f24-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="25f24-104">\<configuration></span></span>  
<span data-ttu-id="25f24-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="25f24-105">\<system.diagnostics></span></span>  
<span data-ttu-id="25f24-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="25f24-106">\<sources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25f24-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25f24-107">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25f24-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="25f24-108">Attributes and Elements</span></span>  
 <span data-ttu-id="25f24-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="25f24-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25f24-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="25f24-110">Attributes</span></span>  
 <span data-ttu-id="25f24-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="25f24-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="25f24-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="25f24-112">Child Elements</span></span>  
  
|<span data-ttu-id="25f24-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="25f24-113">Element</span></span>|<span data-ttu-id="25f24-114">Popis</span><span class="sxs-lookup"><span data-stu-id="25f24-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25f24-115">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="25f24-115">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="25f24-116">Požadovaný element.</span><span class="sxs-lookup"><span data-stu-id="25f24-116">Required element.</span></span><br /><br /> <span data-ttu-id="25f24-117">Určuje zdroj trasování, který iniciuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="25f24-117">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25f24-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="25f24-118">Parent Elements</span></span>  
  
|<span data-ttu-id="25f24-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="25f24-119">Element</span></span>|<span data-ttu-id="25f24-120">Popis</span><span class="sxs-lookup"><span data-stu-id="25f24-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="25f24-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="25f24-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="25f24-122">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="25f24-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25f24-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25f24-123">Remarks</span></span>  
 <span data-ttu-id="25f24-124">Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="25f24-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25f24-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="25f24-125">Example</span></span>  
 <span data-ttu-id="25f24-126">Následující příklad ukazuje způsob použití `<sources>` prvek a přidat zdroj trasování `mySource` a nastavit úroveň pro přepínač zdroje s názvem `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="25f24-126">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="25f24-127">Naslouchacího procesu trasování konzoly je přidat informace o trasování, která zapisuje do konzoly.</span><span class="sxs-lookup"><span data-stu-id="25f24-127">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="25f24-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25f24-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="25f24-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="25f24-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="25f24-130">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="25f24-130">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)
