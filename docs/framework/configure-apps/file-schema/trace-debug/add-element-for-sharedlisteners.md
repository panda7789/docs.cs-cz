---
title: Element <add> pro <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: 5588892ec75a791eda1eb043936c0af95e79354e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153604"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="f2f8a-102">\<přidat prvek \<> pro> sharedListeners</span><span class="sxs-lookup"><span data-stu-id="f2f8a-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="f2f8a-103">Přidá naslouchací proces do `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="f2f8a-104">`sharedListeners`je kolekce naslouchacích procesy, které všechny [ \<zdrojové>](source-element.md) nebo [ \<trasování>](trace-element.md) může odkazovat.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="f2f8a-105">Ve výchozím nastavení naslouchací procesy v kolekci `sharedListeners` nejsou umístěny v kolekci. `Listeners`</span><span class="sxs-lookup"><span data-stu-id="f2f8a-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="f2f8a-106">Musí být přidány názvem do [ \<zdrojového>](source-element.md) nebo [ \<trasování>](trace-element.md).</span><span class="sxs-lookup"><span data-stu-id="f2f8a-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="f2f8a-107">Není možné získat naslouchací procesy v kolekci `sharedListeners` v kódu za běhu.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

<span data-ttu-id="f2f8a-108">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2f8a-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f2f8a-109">&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2f8a-109">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="f2f8a-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2f8a-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="f2f8a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**</span><span class="sxs-lookup"><span data-stu-id="f2f8a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f2f8a-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2f8a-112">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2f8a-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f2f8a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f2f8a-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2f8a-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="f2f8a-115">Attributes</span></span>  
  
|<span data-ttu-id="f2f8a-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="f2f8a-116">Attribute</span></span>|<span data-ttu-id="f2f8a-117">Popis</span><span class="sxs-lookup"><span data-stu-id="f2f8a-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="f2f8a-118">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="f2f8a-119">Určuje název naslouchací proces, který se `Listeners` používá k přidání sdíleného naslouchací proces do kolekce.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="f2f8a-120">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="f2f8a-121">Určuje typ naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-121">Specifies the type of the listener.</span></span> <span data-ttu-id="f2f8a-122">Je nutné použít řetězec, který splňuje požadavky zadané v [poli Určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="f2f8a-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="f2f8a-123">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f2f8a-124">Řetězec předán konstruktoru pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="f2f8a-125">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="f2f8a-126">Řetězcová reprezentace jednoho <xref:System.Diagnostics.TraceOptions> nebo více členů výčtu, která označuje data, která mají být zapsána do výstupu trasování.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="f2f8a-127">Více položek je odděleno čárkami.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="f2f8a-128">Výchozí hodnota je "Žádný".</span><span class="sxs-lookup"><span data-stu-id="f2f8a-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f2f8a-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f2f8a-129">Child Elements</span></span>  
  
|<span data-ttu-id="f2f8a-130">Element</span><span class="sxs-lookup"><span data-stu-id="f2f8a-130">Element</span></span>|<span data-ttu-id="f2f8a-131">Popis</span><span class="sxs-lookup"><span data-stu-id="f2f8a-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2f8a-132">\<>filtru</span><span class="sxs-lookup"><span data-stu-id="f2f8a-132">\<filter></span></span>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="f2f8a-133">Přidá filtr do naslouchací proces v kolekci. `sharedListeners`</span><span class="sxs-lookup"><span data-stu-id="f2f8a-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2f8a-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f2f8a-134">Parent Elements</span></span>  
  
|<span data-ttu-id="f2f8a-135">Element</span><span class="sxs-lookup"><span data-stu-id="f2f8a-135">Element</span></span>|<span data-ttu-id="f2f8a-136">Popis</span><span class="sxs-lookup"><span data-stu-id="f2f8a-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f2f8a-137">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f2f8a-138">Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="f2f8a-139">Kolekce naslouchacích procesy, které může odkazovat libovolný zdroj nebo prvek trasování.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2f8a-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2f8a-140">Remarks</span></span>  
 <span data-ttu-id="f2f8a-141">Třídy posluchače dodávané s rozhraním <xref:System.Diagnostics.TraceListener> .NET Framework jsou odvozeny z třídy.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="f2f8a-142">Hodnota atributu `name` se používá k přidání sdíleného naslouchací proces do `Listeners` kolekce pro trasování nebo zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="f2f8a-143">Hodnota atributu `initializeData` závisí na typu naslouchacího procesu, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="f2f8a-144">Ne všechny naslouchací procesy trasování vyžadují, abyste zadali `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2f8a-145">Při použití `initializeData` atributu se může dostat upozornění kompilátoru "Atribut initializeData' není deklarován."</span><span class="sxs-lookup"><span data-stu-id="f2f8a-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="f2f8a-146">K tomuto upozornění dochází, protože nastavení konfigurace <xref:System.Diagnostics.TraceListener>jsou ověřeny proti `initializeData` abstraktní základní třídy , která nerozpozná atribut.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="f2f8a-147">Obvykle můžete ignorovat toto upozornění pro implementace posluchače trasování, které mají konstruktor, který přebírá parametr.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="f2f8a-148">V následující tabulce jsou uvedeny posluchače trasování, které jsou součástí `initializeData` rozhraní .NET Framework a popisuje hodnotu jejich atributů.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="f2f8a-149">Třída posluchače trasování</span><span class="sxs-lookup"><span data-stu-id="f2f8a-149">Trace listener class</span></span>|<span data-ttu-id="f2f8a-150">hodnota atributu initializeData</span><span class="sxs-lookup"><span data-stu-id="f2f8a-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="f2f8a-151">Hodnota `useErrorStream` pro <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="f2f8a-152">Nastavte `initializeData` atribut na`true`" " pro zápis výstupu trasování a ladění do standardního datového proudu chyb; nastavte jej`false`na " " pro zápis do standardního výstupního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="f2f8a-153">Název souboru, <xref:System.Diagnostics.DelimitedListTraceListener> do který zapisuje.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f2f8a-154">Název existujícího zdroje protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f2f8a-155">Název souboru, do <xref:System.Diagnostics.EventSchemaTraceListener> kterého zapisuje.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="f2f8a-156">Název souboru, do <xref:System.Diagnostics.TextWriterTraceListener> kterého zapisuje.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="f2f8a-157">Název souboru, do <xref:System.Diagnostics.XmlWriterTraceListener> kterého zapisuje.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="f2f8a-158">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="f2f8a-158">Configuration File</span></span>  
 <span data-ttu-id="f2f8a-159">Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2f8a-160">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2f8a-160">Example</span></span>  
 <span data-ttu-id="f2f8a-161">Následující příklad ukazuje, `<add>` jak použít <xref:System.Diagnostics.TextWriterTraceListener> `textListener` prvky `sharedListeners` přidat do kolekce.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="f2f8a-162">`textListener`je přidán podle `Listeners` názvu do kolekce `TraceSourceApp`pro zdroj trasování .</span><span class="sxs-lookup"><span data-stu-id="f2f8a-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="f2f8a-163">Naslouchací `textListener` proces zapíše výstup trasování do souboru myListener.log.</span><span class="sxs-lookup"><span data-stu-id="f2f8a-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="f2f8a-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2f8a-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="f2f8a-165">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="f2f8a-165">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f2f8a-166">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="f2f8a-166">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
