---
title: Element <source>
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 417722ce2f3865350158413307495e3ab435d386
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153292"
---
# <a name="source-element"></a><span data-ttu-id="ff378-102">\<zdroj> Element</span><span class="sxs-lookup"><span data-stu-id="ff378-102">\<source> Element</span></span>
<span data-ttu-id="ff378-103">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="ff378-103">Specifies a trace source that initiates tracing messages.</span></span>  

<span data-ttu-id="ff378-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ff378-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ff378-105">&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="ff378-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="ff378-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdroje>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="ff378-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="ff378-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<zdrojové>**</span><span class="sxs-lookup"><span data-stu-id="ff378-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ff378-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff378-108">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff378-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ff378-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ff378-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ff378-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff378-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ff378-111">Attributes</span></span>  
  
|<span data-ttu-id="ff378-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="ff378-112">Attribute</span></span>|<span data-ttu-id="ff378-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ff378-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="ff378-114">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ff378-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ff378-115">Určuje název zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="ff378-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="ff378-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ff378-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ff378-117">Určuje název instance přepínače trasování v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ff378-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="ff378-118">Pokud přepínač není v `<switches>` prvku identifikován, hodnota určuje úroveň přepínače.</span><span class="sxs-lookup"><span data-stu-id="ff378-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="ff378-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ff378-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ff378-120">Určuje typ přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="ff378-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="ff378-121">Pokud je k dispozici, musí být typ platný název třídy a nemůže být prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="ff378-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="ff378-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ff378-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ff378-123">Určuje hodnotu atributu specifického pro zdroj <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> trasování identifikovaného metodou pro daný zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="ff378-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff378-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ff378-124">Child Elements</span></span>  
  
|<span data-ttu-id="ff378-125">Element</span><span class="sxs-lookup"><span data-stu-id="ff378-125">Element</span></span>|<span data-ttu-id="ff378-126">Popis</span><span class="sxs-lookup"><span data-stu-id="ff378-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff378-127">\<posluchači></span><span class="sxs-lookup"><span data-stu-id="ff378-127">\<listeners></span></span>](listeners-element-for-source.md)|<span data-ttu-id="ff378-128">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="ff378-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff378-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ff378-129">Parent Elements</span></span>  
  
|<span data-ttu-id="ff378-130">Element</span><span class="sxs-lookup"><span data-stu-id="ff378-130">Element</span></span>|<span data-ttu-id="ff378-131">Popis</span><span class="sxs-lookup"><span data-stu-id="ff378-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ff378-132">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ff378-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="ff378-133">Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="ff378-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="ff378-134">Obsahuje zdroje trasování, které iniciují tracing zprávy.</span><span class="sxs-lookup"><span data-stu-id="ff378-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff378-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff378-135">Remarks</span></span>  
 <span data-ttu-id="ff378-136">Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ff378-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff378-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff378-137">Example</span></span>  
 <span data-ttu-id="ff378-138">Následující příklad ukazuje, jak `<source>` pomocí prvku přidat `mySource` zdroj trasování a nastavit `sourceSwitch`úroveň pro zdrojový přepínač s názvem .</span><span class="sxs-lookup"><span data-stu-id="ff378-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="ff378-139">Je přidán naslouchací proces trasování konzoly, který zapisuje informace o trasování do konzoly.</span><span class="sxs-lookup"><span data-stu-id="ff378-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff378-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff378-140">See also</span></span>

- [<span data-ttu-id="ff378-141">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="ff378-141">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ff378-142">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="ff378-142">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
