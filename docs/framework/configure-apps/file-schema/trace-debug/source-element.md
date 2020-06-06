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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153292"
---
# <a name="source-element"></a><span data-ttu-id="fd3bc-102">Element \<source></span><span class="sxs-lookup"><span data-stu-id="fd3bc-102">\<source> Element</span></span>
<span data-ttu-id="fd3bc-103">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-103">Specifies a trace source that initiates tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**

## <a name="syntax"></a><span data-ttu-id="fd3bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd3bc-104">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd3bc-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fd3bc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fd3bc-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd3bc-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="fd3bc-107">Attributes</span></span>  
  
|<span data-ttu-id="fd3bc-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="fd3bc-108">Attribute</span></span>|<span data-ttu-id="fd3bc-109">Popis</span><span class="sxs-lookup"><span data-stu-id="fd3bc-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="fd3bc-110">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fd3bc-111">Určuje název zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-111">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="fd3bc-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fd3bc-113">Určuje název instance přepínače trasování v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-113">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="fd3bc-114">Pokud není přepínač identifikován v `<switches>` prvku, hodnota určuje úroveň přepínače.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-114">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="fd3bc-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fd3bc-116">Určuje typ přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-116">Specifies the type of the trace switch.</span></span> <span data-ttu-id="fd3bc-117">Je-li k dispozici typ, musí být platný název třídy a nemůže být prázdným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-117">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="fd3bc-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fd3bc-119">Určuje hodnotu pro atribut specifický pro zdroj trasování identifikovaný <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> metodou pro daný zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-119">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd3bc-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fd3bc-120">Child Elements</span></span>  
  
|<span data-ttu-id="fd3bc-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="fd3bc-121">Element</span></span>|<span data-ttu-id="fd3bc-122">Description</span><span class="sxs-lookup"><span data-stu-id="fd3bc-122">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="fd3bc-123">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-123">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fd3bc-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fd3bc-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fd3bc-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="fd3bc-125">Element</span></span>|<span data-ttu-id="fd3bc-126">Description</span><span class="sxs-lookup"><span data-stu-id="fd3bc-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fd3bc-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fd3bc-128">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="fd3bc-129">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-129">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd3bc-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd3bc-130">Remarks</span></span>  
 <span data-ttu-id="fd3bc-131">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd3bc-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd3bc-132">Example</span></span>  
 <span data-ttu-id="fd3bc-133">Následující příklad ukazuje, jak použít `<source>` element k přidání zdroje trasování `mySource` a k nastavení úrovně pro zdrojový přepínač s názvem `sourceSwitch` .</span><span class="sxs-lookup"><span data-stu-id="fd3bc-133">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="fd3bc-134">Je přidán naslouchací proces trasování konzoly, který zapisuje trasovací informace do konzoly.</span><span class="sxs-lookup"><span data-stu-id="fd3bc-134">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd3bc-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd3bc-135">See also</span></span>

- [<span data-ttu-id="fd3bc-136">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="fd3bc-136">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fd3bc-137">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="fd3bc-137">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
