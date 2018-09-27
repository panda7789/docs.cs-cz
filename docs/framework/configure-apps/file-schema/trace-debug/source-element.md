---
title: '&lt;Zdroj&gt; – Element'
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 818324077322fffb40a192c9197efde6e8ff7591
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231886"
---
# <a name="ltsourcegt-element"></a><span data-ttu-id="48fe5-102">&lt;Zdroj&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="48fe5-102">&lt;source&gt; Element</span></span>
<span data-ttu-id="48fe5-103">Určuje zdroj trasování, který iniciuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="48fe5-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
 <span data-ttu-id="48fe5-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="48fe5-104">\<configuration></span></span>  
<span data-ttu-id="48fe5-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="48fe5-105">\<system.diagnostics></span></span>  
<span data-ttu-id="48fe5-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="48fe5-106">\<sources></span></span>  
<span data-ttu-id="48fe5-107">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="48fe5-107">\<source></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48fe5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48fe5-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48fe5-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="48fe5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="48fe5-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="48fe5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48fe5-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="48fe5-111">Attributes</span></span>  
  
|<span data-ttu-id="48fe5-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="48fe5-112">Attribute</span></span>|<span data-ttu-id="48fe5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="48fe5-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="48fe5-114">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="48fe5-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="48fe5-115">Určuje název zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="48fe5-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="48fe5-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="48fe5-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="48fe5-117">Určuje název instance přepínače trasování v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="48fe5-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="48fe5-118">Pokud přepínač není identifikované v `<switches>` elementu, hodnota určuje úroveň pro přepínač.</span><span class="sxs-lookup"><span data-stu-id="48fe5-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="48fe5-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="48fe5-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="48fe5-120">Určuje typ přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="48fe5-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="48fe5-121">Pokud jsou k dispozici, typ musí být platný název třídy a nemůže být prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="48fe5-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="48fe5-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="48fe5-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="48fe5-123">Určuje hodnotu pro atribut specifická pro zdroj trasování identifikován <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> metoda u tohoto zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="48fe5-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48fe5-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="48fe5-124">Child Elements</span></span>  
  
|<span data-ttu-id="48fe5-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="48fe5-125">Element</span></span>|<span data-ttu-id="48fe5-126">Popis</span><span class="sxs-lookup"><span data-stu-id="48fe5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48fe5-127">\<naslouchací procesy ></span><span class="sxs-lookup"><span data-stu-id="48fe5-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="48fe5-128">Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="48fe5-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48fe5-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="48fe5-129">Parent Elements</span></span>  
  
|<span data-ttu-id="48fe5-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="48fe5-130">Element</span></span>|<span data-ttu-id="48fe5-131">Popis</span><span class="sxs-lookup"><span data-stu-id="48fe5-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="48fe5-132">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48fe5-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="48fe5-133">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="48fe5-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="48fe5-134">Obsahuje zdrojů trasování, které se zahájí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="48fe5-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48fe5-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48fe5-135">Remarks</span></span>  
 <span data-ttu-id="48fe5-136">Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="48fe5-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48fe5-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="48fe5-137">Example</span></span>  
 <span data-ttu-id="48fe5-138">Následující příklad ukazuje způsob použití `<source>` prvek a přidat zdroj trasování `mySource` a nastavit úroveň pro přepínač zdroje s názvem `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="48fe5-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="48fe5-139">Naslouchacího procesu trasování konzoly je přidat informace o trasování, která zapisuje do konzoly.</span><span class="sxs-lookup"><span data-stu-id="48fe5-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
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
  
## <a name="see-also"></a><span data-ttu-id="48fe5-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="48fe5-140">See Also</span></span>  
 [<span data-ttu-id="48fe5-141">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="48fe5-141">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="48fe5-142">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="48fe5-142">Trace Switches</span></span>](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
