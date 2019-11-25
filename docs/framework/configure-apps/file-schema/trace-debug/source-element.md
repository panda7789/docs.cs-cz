---
title: Element <source>
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: b59144f4772c940f8c7e6ca19aa21666069b4b55
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088821"
---
# <a name="source-element"></a><span data-ttu-id="c4a2a-102">zdrojový > elementu \<</span><span class="sxs-lookup"><span data-stu-id="c4a2a-102">\<source> Element</span></span>
<span data-ttu-id="c4a2a-103">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-103">Specifies a trace source that initiates tracing messages.</span></span>  

<span data-ttu-id="c4a2a-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c4a2a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c4a2a-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="c4a2a-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="c4a2a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zdrojů >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="c4a2a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="c4a2a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zdroj >**</span><span class="sxs-lookup"><span data-stu-id="c4a2a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c4a2a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4a2a-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4a2a-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c4a2a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c4a2a-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4a2a-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="c4a2a-111">Attributes</span></span>  
  
|<span data-ttu-id="c4a2a-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="c4a2a-112">Attribute</span></span>|<span data-ttu-id="c4a2a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c4a2a-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="c4a2a-114">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c4a2a-115">Určuje název zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="c4a2a-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c4a2a-117">Určuje název instance přepínače trasování v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="c4a2a-118">Pokud není přepínač identifikován v prvku `<switches>`, hodnota určuje úroveň přepínače.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="c4a2a-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c4a2a-120">Určuje typ přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="c4a2a-121">Je-li k dispozici typ, musí být platný název třídy a nemůže být prázdným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="c4a2a-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c4a2a-123">Určuje hodnotu pro atribut specifický pro zdroj trasování identifikovaný metodou <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> pro daný zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4a2a-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c4a2a-124">Child Elements</span></span>  
  
|<span data-ttu-id="c4a2a-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="c4a2a-125">Element</span></span>|<span data-ttu-id="c4a2a-126">Popis</span><span class="sxs-lookup"><span data-stu-id="c4a2a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4a2a-127">naslouchací procesy \<</span><span class="sxs-lookup"><span data-stu-id="c4a2a-127">\<listeners></span></span>](listeners-element-for-source.md)|<span data-ttu-id="c4a2a-128">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4a2a-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c4a2a-129">Parent Elements</span></span>  
  
|<span data-ttu-id="c4a2a-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="c4a2a-130">Element</span></span>|<span data-ttu-id="c4a2a-131">Popis</span><span class="sxs-lookup"><span data-stu-id="c4a2a-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c4a2a-132">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c4a2a-133">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="c4a2a-134">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4a2a-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4a2a-135">Remarks</span></span>  
 <span data-ttu-id="c4a2a-136">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4a2a-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4a2a-137">Example</span></span>  
 <span data-ttu-id="c4a2a-138">Následující příklad ukazuje, jak použít element `<source>` k přidání `mySource` zdroje trasování a k nastavení úrovně pro zdrojový přepínač s názvem `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="c4a2a-139">Je přidán naslouchací proces trasování konzoly, který zapisuje trasovací informace do konzoly.</span><span class="sxs-lookup"><span data-stu-id="c4a2a-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c4a2a-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4a2a-140">See also</span></span>

- [<span data-ttu-id="c4a2a-141">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="c4a2a-141">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c4a2a-142">Přepínače trasování</span><span class="sxs-lookup"><span data-stu-id="c4a2a-142">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
