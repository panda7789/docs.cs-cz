---
title: Element <source>
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 55120e292ac2a2c822c5510563d1aa167ca921e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920452"
---
# <a name="source-element"></a><span data-ttu-id="3bc63-102">\<Element > zdroje</span><span class="sxs-lookup"><span data-stu-id="3bc63-102">\<source> Element</span></span>
<span data-ttu-id="3bc63-103">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="3bc63-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
 <span data-ttu-id="3bc63-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="3bc63-104">\<configuration></span></span>  
<span data-ttu-id="3bc63-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="3bc63-105">\<system.diagnostics></span></span>  
<span data-ttu-id="3bc63-106">\<> zdrojů</span><span class="sxs-lookup"><span data-stu-id="3bc63-106">\<sources></span></span>  
<span data-ttu-id="3bc63-107">\<> zdroje</span><span class="sxs-lookup"><span data-stu-id="3bc63-107">\<source></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bc63-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bc63-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bc63-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3bc63-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3bc63-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3bc63-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bc63-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="3bc63-111">Attributes</span></span>  
  
|<span data-ttu-id="3bc63-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="3bc63-112">Attribute</span></span>|<span data-ttu-id="3bc63-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3bc63-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="3bc63-114">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3bc63-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3bc63-115">Určuje název zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="3bc63-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="3bc63-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3bc63-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3bc63-117">Určuje název instance přepínače trasování v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3bc63-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="3bc63-118">Pokud není přepínač identifikován v `<switches>` prvku, hodnota určuje úroveň přepínače.</span><span class="sxs-lookup"><span data-stu-id="3bc63-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="3bc63-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3bc63-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3bc63-120">Určuje typ přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="3bc63-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="3bc63-121">Je-li k dispozici typ, musí být platný název třídy a nemůže být prázdným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="3bc63-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="3bc63-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3bc63-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3bc63-123">Určuje hodnotu pro atribut specifický pro zdroj trasování identifikovaný <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> metodou pro daný zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="3bc63-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bc63-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3bc63-124">Child Elements</span></span>  
  
|<span data-ttu-id="3bc63-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="3bc63-125">Element</span></span>|<span data-ttu-id="3bc63-126">Popis</span><span class="sxs-lookup"><span data-stu-id="3bc63-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bc63-127">\<> naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="3bc63-127">\<listeners></span></span>](listeners-element-for-source.md)|<span data-ttu-id="3bc63-128">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="3bc63-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3bc63-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3bc63-129">Parent Elements</span></span>  
  
|<span data-ttu-id="3bc63-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="3bc63-130">Element</span></span>|<span data-ttu-id="3bc63-131">Popis</span><span class="sxs-lookup"><span data-stu-id="3bc63-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3bc63-132">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3bc63-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3bc63-133">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="3bc63-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="3bc63-134">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="3bc63-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bc63-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3bc63-135">Remarks</span></span>  
 <span data-ttu-id="3bc63-136">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="3bc63-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bc63-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="3bc63-137">Example</span></span>  
 <span data-ttu-id="3bc63-138">Následující příklad ukazuje, jak použít `<source>` element k přidání zdroje `mySource` trasování a k nastavení úrovně pro zdrojový přepínač s názvem `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="3bc63-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="3bc63-139">Je přidán naslouchací proces trasování konzoly, který zapisuje trasovací informace do konzoly.</span><span class="sxs-lookup"><span data-stu-id="3bc63-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3bc63-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3bc63-140">See also</span></span>

- [<span data-ttu-id="3bc63-141">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="3bc63-141">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3bc63-142">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="3bc63-142">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
