---
title: <add>Prvek <listeners> pro pro<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153682"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="28e3e-102">\<přidat prvek \<> pro \<naslouchací procesy> pro zdrojový></span><span class="sxs-lookup"><span data-stu-id="28e3e-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="28e3e-103">Přidá naslouchací proces do `Listeners` kolekce pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="28e3e-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="28e3e-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="28e3e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="28e3e-105">&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="28e3e-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="28e3e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdroje>**](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="28e3e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="28e3e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdrojové>**](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="28e3e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="28e3e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<posluchači>**](listeners-element-for-source.md)</span><span class="sxs-lookup"><span data-stu-id="28e3e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="28e3e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**</span><span class="sxs-lookup"><span data-stu-id="28e3e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="28e3e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28e3e-110">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28e3e-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="28e3e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="28e3e-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="28e3e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28e3e-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="28e3e-113">Attributes</span></span>  
  
|<span data-ttu-id="28e3e-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="28e3e-114">Attribute</span></span>|<span data-ttu-id="28e3e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="28e3e-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="28e3e-116">Povinný atribut, pokud odkazujete na naslouchací proces v `sharedListeners` kolekci, v takovém případě stačí odkazovat na něj podle názvu (viz [příklad).](#example)</span><span class="sxs-lookup"><span data-stu-id="28e3e-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="28e3e-117">Určuje typ naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="28e3e-117">Specifies the type of the listener.</span></span> <span data-ttu-id="28e3e-118">Je nutné použít řetězec, který splňuje požadavky zadané v [poli Určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="28e3e-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="28e3e-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="28e3e-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="28e3e-120">Řetězec předán konstruktoru pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="28e3e-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="28e3e-121">A <xref:System.Configuration.ConfigurationException> je vyvolána, pokud třída nemá konstruktor, který trvá řetězec.</span><span class="sxs-lookup"><span data-stu-id="28e3e-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="28e3e-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="28e3e-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="28e3e-123">Určuje název naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="28e3e-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="28e3e-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="28e3e-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="28e3e-125">Určuje hodnotu vlastnosti <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> posluchače trasování.</span><span class="sxs-lookup"><span data-stu-id="28e3e-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="28e3e-126">[vlastní atributy]</span><span class="sxs-lookup"><span data-stu-id="28e3e-126">[custom attributes]</span></span>|<span data-ttu-id="28e3e-127">Volitelné atributy.</span><span class="sxs-lookup"><span data-stu-id="28e3e-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="28e3e-128">Určuje hodnotu atributů specifických pro <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> posluchače identifikovaných metodou pro daný naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="28e3e-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="28e3e-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>je příkladem extra atribut jedinečný <xref:System.Diagnostics.DelimitedListTraceListener> pro třídu.</span><span class="sxs-lookup"><span data-stu-id="28e3e-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28e3e-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="28e3e-130">Child Elements</span></span>  
  
|<span data-ttu-id="28e3e-131">Element</span><span class="sxs-lookup"><span data-stu-id="28e3e-131">Element</span></span>|<span data-ttu-id="28e3e-132">Popis</span><span class="sxs-lookup"><span data-stu-id="28e3e-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28e3e-133">\<>filtru</span><span class="sxs-lookup"><span data-stu-id="28e3e-133">\<filter></span></span>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="28e3e-134">Přidá filtr do naslouchací proces v kolekci `Listeners` pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="28e3e-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28e3e-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="28e3e-135">Parent Elements</span></span>  
  
|<span data-ttu-id="28e3e-136">Element</span><span class="sxs-lookup"><span data-stu-id="28e3e-136">Element</span></span>|<span data-ttu-id="28e3e-137">Popis</span><span class="sxs-lookup"><span data-stu-id="28e3e-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="28e3e-138">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="28e3e-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="28e3e-139">Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="28e3e-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="28e3e-140">Obsahuje zdroje trasování, které iniciují tracing zprávy.</span><span class="sxs-lookup"><span data-stu-id="28e3e-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="28e3e-141">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="28e3e-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="28e3e-142">Určuje posluchače, kteří shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="28e3e-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28e3e-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28e3e-143">Remarks</span></span>  
 <span data-ttu-id="28e3e-144">Třídy posluchače dodávané s rozhraním <xref:System.Diagnostics.TraceListener> .NET Framework jsou odvozeny z třídy.</span><span class="sxs-lookup"><span data-stu-id="28e3e-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="28e3e-145">Pokud nezadáte `name` atribut posluchače trasování, <xref:System.Diagnostics.TraceListener.Name%2A> vlastnost posluchače trasování výchozí prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="28e3e-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="28e3e-146">Pokud aplikace obsahuje pouze jeden naslouchací proces, můžete jej přidat bez zadání názvu a můžete jej odebrat zadáním prázdného řetězce pro název.</span><span class="sxs-lookup"><span data-stu-id="28e3e-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="28e3e-147">Pokud však aplikace obsahuje více než jeden naslouchací proces, měli byste zadat jedinečný název <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> pro každý naslouchací proces trasování, který umožňuje identifikovat a spravovat jednotlivé posluchače trasování v kolekci.</span><span class="sxs-lookup"><span data-stu-id="28e3e-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28e3e-148">Přidání více než jeden naslouchací proces trasování stejného typu a se stejným `Listeners` názvem má za následek pouze jeden posluchač trasování tohoto typu a název, který je přidán do kolekce.</span><span class="sxs-lookup"><span data-stu-id="28e3e-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="28e3e-149">Můžete však programově přidat více identických naslouchacích procesy do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="28e3e-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="28e3e-150">Hodnota atributu `initializeData` závisí na typu naslouchacího procesu, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="28e3e-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="28e3e-151">Ne všechny naslouchací procesy trasování vyžadují, abyste zadali `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="28e3e-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28e3e-152">Při použití `initializeData` atributu se může dostat upozornění kompilátoru "Atribut initializeData' není deklarován."</span><span class="sxs-lookup"><span data-stu-id="28e3e-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="28e3e-153">K tomuto upozornění dochází, protože nastavení konfigurace <xref:System.Diagnostics.TraceListener>jsou ověřeny proti `initializeData` abstraktní základní třídy , která nerozpozná atribut.</span><span class="sxs-lookup"><span data-stu-id="28e3e-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="28e3e-154">Obvykle můžete ignorovat toto upozornění pro implementace posluchače trasování, které mají konstruktor, který přebírá parametr.</span><span class="sxs-lookup"><span data-stu-id="28e3e-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="28e3e-155">V následující tabulce jsou uvedeny posluchače trasování, které jsou součástí `initializeData` rozhraní .NET Framework a popisuje hodnotu jejich atributů.</span><span class="sxs-lookup"><span data-stu-id="28e3e-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="28e3e-156">Třída posluchače trasování</span><span class="sxs-lookup"><span data-stu-id="28e3e-156">Trace listener class</span></span>|<span data-ttu-id="28e3e-157">hodnota atributu initializeData</span><span class="sxs-lookup"><span data-stu-id="28e3e-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="28e3e-158">Hodnota `useErrorStream` pro <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="28e3e-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="28e3e-159">Nastavte `initializeData` atribut na`true`" " pro zápis výstupu trasování a ladění do standardního datového proudu chyb; nastavte jej`false`na " " pro zápis do standardního výstupního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="28e3e-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="28e3e-160">Název souboru, <xref:System.Diagnostics.DelimitedListTraceListener> do který zapisuje.</span><span class="sxs-lookup"><span data-stu-id="28e3e-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="28e3e-161">Název existujícího zdroje protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="28e3e-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="28e3e-162">Název souboru, do <xref:System.Diagnostics.EventSchemaTraceListener> kterého zapisuje.</span><span class="sxs-lookup"><span data-stu-id="28e3e-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="28e3e-163">Název souboru, do <xref:System.Diagnostics.TextWriterTraceListener> kterého zapisuje.</span><span class="sxs-lookup"><span data-stu-id="28e3e-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="28e3e-164">Název souboru, do <xref:System.Diagnostics.XmlWriterTraceListener> kterého zapisuje.</span><span class="sxs-lookup"><span data-stu-id="28e3e-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="28e3e-165">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="28e3e-165">Configuration File</span></span>  
 <span data-ttu-id="28e3e-166">Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="28e3e-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28e3e-167">Příklad</span><span class="sxs-lookup"><span data-stu-id="28e3e-167">Example</span></span>  
 <span data-ttu-id="28e3e-168">Následující příklad ukazuje, `<add>` jak použít prvky `console` `textListener` přidat `Listeners` posluchače a `TraceSourceApp`do kolekce pro zdroj trasování .</span><span class="sxs-lookup"><span data-stu-id="28e3e-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="28e3e-169">Naslouchací `textListener` proces zapíše výstup trasování do souboru myListener.log.</span><span class="sxs-lookup"><span data-stu-id="28e3e-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="28e3e-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="28e3e-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="28e3e-171">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="28e3e-171">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="28e3e-172">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="28e3e-172">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
