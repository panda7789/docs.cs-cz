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
manager: markl
ms.openlocfilehash: b7c2a71b129a0ad7d1c2a72b18b8a69a111f9495
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752569"
---
# <a name="ltsourcegt-element"></a><span data-ttu-id="dcd3f-102">&lt;Zdroj&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="dcd3f-102">&lt;source&gt; Element</span></span>
<span data-ttu-id="dcd3f-103">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
 <span data-ttu-id="dcd3f-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="dcd3f-104">\<configuration></span></span>  
<span data-ttu-id="dcd3f-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="dcd3f-105">\<system.diagnostics></span></span>  
<span data-ttu-id="dcd3f-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="dcd3f-106">\<sources></span></span>  
<span data-ttu-id="dcd3f-107">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="dcd3f-107">\<source></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcd3f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcd3f-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcd3f-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dcd3f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dcd3f-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcd3f-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="dcd3f-111">Attributes</span></span>  
  
|<span data-ttu-id="dcd3f-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="dcd3f-112">Attribute</span></span>|<span data-ttu-id="dcd3f-113">Popis</span><span class="sxs-lookup"><span data-stu-id="dcd3f-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="dcd3f-114">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="dcd3f-115">Určuje název zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="dcd3f-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="dcd3f-117">Určuje název instance přepínače trasování v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="dcd3f-118">Pokud přepínač není v identifikovat `<switches>` elementu, hodnota určuje úroveň přepínače.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="dcd3f-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="dcd3f-120">Určuje typ přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="dcd3f-121">Pokud je k dispozici, typ musí být platný název třídy a nemůže být prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="dcd3f-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="dcd3f-123">Určuje hodnotu pro atribut konkrétní zdroj trasování identifikovaný <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> metodu pro tento zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcd3f-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dcd3f-124">Child Elements</span></span>  
  
|<span data-ttu-id="dcd3f-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="dcd3f-125">Element</span></span>|<span data-ttu-id="dcd3f-126">Popis</span><span class="sxs-lookup"><span data-stu-id="dcd3f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcd3f-127">\<moduly pro naslouchání ></span><span class="sxs-lookup"><span data-stu-id="dcd3f-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="dcd3f-128">Obsahuje naslouchací procesy, které shromažďování, ukládání a směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dcd3f-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dcd3f-129">Parent Elements</span></span>  
  
|<span data-ttu-id="dcd3f-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="dcd3f-130">Element</span></span>|<span data-ttu-id="dcd3f-131">Popis</span><span class="sxs-lookup"><span data-stu-id="dcd3f-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dcd3f-132">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="dcd3f-133">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="dcd3f-134">Obsahuje trasování zdrojů, které zahájí trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcd3f-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcd3f-135">Remarks</span></span>  
 <span data-ttu-id="dcd3f-136">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcd3f-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="dcd3f-137">Example</span></span>  
 <span data-ttu-id="dcd3f-138">Následující příklad ukazuje, jak používat `<source>` elementu, který chcete přidat zdroj trasování `mySource` a nastaví úroveň přepínač zdroje s názvem `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="dcd3f-139">Naslouchací proces trasování konzoly je přidaná který informace trasování zapíše do konzoly.</span><span class="sxs-lookup"><span data-stu-id="dcd3f-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dcd3f-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="dcd3f-140">See Also</span></span>  
 [<span data-ttu-id="dcd3f-141">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="dcd3f-141">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="dcd3f-142">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="dcd3f-142">Trace Switches</span></span>](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
