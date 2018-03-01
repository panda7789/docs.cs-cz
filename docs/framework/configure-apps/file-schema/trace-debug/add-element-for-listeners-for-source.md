---
title: "&lt;Přidat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;zdroje&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 86177010d8ed70302b51ec9c416a3295009e7394
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="e1848-102">&lt;Přidat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;zdroje&gt;</span><span class="sxs-lookup"><span data-stu-id="e1848-102">&lt;add&gt; Element for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="e1848-103">Přidá naslouchací proces a `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="e1848-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="e1848-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="e1848-104">\<configuration></span></span>  
<span data-ttu-id="e1848-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="e1848-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e1848-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="e1848-106">\<sources></span></span>  
<span data-ttu-id="e1848-107">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="e1848-107">\<source></span></span>  
<span data-ttu-id="e1848-108">\<moduly pro naslouchání ></span><span class="sxs-lookup"><span data-stu-id="e1848-108">\<listeners></span></span>  
<span data-ttu-id="e1848-109">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="e1848-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1848-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1848-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1848-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e1848-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e1848-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e1848-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1848-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="e1848-113">Attributes</span></span>  
  
|<span data-ttu-id="e1848-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="e1848-114">Attribute</span></span>|<span data-ttu-id="e1848-115">Popis</span><span class="sxs-lookup"><span data-stu-id="e1848-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e1848-116">Atribut je povinný, pokud jste odkazující na naslouchací proces ve `sharedListeners` kolekce, ve kterém případ, je potřeba pouze na ni odkazuje podle názvu (najdete v článku [příklad](#example)).</span><span class="sxs-lookup"><span data-stu-id="e1848-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="e1848-117">Určuje typ naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="e1848-117">Specifies the type of the listener.</span></span> <span data-ttu-id="e1848-118">Je nutné použít řetězec, který splňuje požadavky uvedené v [určení plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="e1848-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="e1848-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="e1848-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e1848-120">Řetězec předaný konstruktoru pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="e1848-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="e1848-121">A <xref:System.Configuration.ConfigurationException> je vyvolána, pokud třída nemá konstruktor, který přebírá řetězec.</span><span class="sxs-lookup"><span data-stu-id="e1848-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="e1848-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="e1848-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e1848-123">Určuje název naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="e1848-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="e1848-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="e1848-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e1848-125">Určuje, <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> hodnota vlastnosti pro naslouchací proces trasování.</span><span class="sxs-lookup"><span data-stu-id="e1848-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="e1848-126">[vlastní atributy]</span><span class="sxs-lookup"><span data-stu-id="e1848-126">[custom attributes]</span></span>|<span data-ttu-id="e1848-127">Volitelných atributů.</span><span class="sxs-lookup"><span data-stu-id="e1848-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="e1848-128">Určuje hodnotu atributy specifické pro naslouchací proces identifikovaný <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> metoda pro tento naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="e1848-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="e1848-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>Navíc atributu je jedinečná <xref:System.Diagnostics.DelimitedListTraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="e1848-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1848-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e1848-130">Child Elements</span></span>  
  
|<span data-ttu-id="e1848-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="e1848-131">Element</span></span>|<span data-ttu-id="e1848-132">Popis</span><span class="sxs-lookup"><span data-stu-id="e1848-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1848-133">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="e1848-133">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="e1848-134">Přidá filtr do naslouchací proces ve `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="e1848-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e1848-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e1848-135">Parent Elements</span></span>  
  
|<span data-ttu-id="e1848-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="e1848-136">Element</span></span>|<span data-ttu-id="e1848-137">Popis</span><span class="sxs-lookup"><span data-stu-id="e1848-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e1848-138">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e1848-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e1848-139">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="e1848-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="e1848-140">Obsahuje trasování zdrojů, které zahájí trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="e1848-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="e1848-141">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="e1848-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="e1848-142">Určuje naslouchací procesy, které shromažďování, ukládání a směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="e1848-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1848-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1848-143">Remarks</span></span>  
 <span data-ttu-id="e1848-144">Naslouchací proces třídy součástí rozhraní .NET Framework odvozena od <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="e1848-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="e1848-145">Pokud nezadáte `name` atribut naslouchací proces trasování, <xref:System.Diagnostics.TraceListener.Name%2A> vlastnost naslouchací proces trasování výchozí nastavení je prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="e1848-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="e1848-146">Pokud vaše aplikace má pouze jeden naslouchací proces, můžete jej přidat bez určení názvu a můžete jej odebrat zadáním prázdný řetězec pro název.</span><span class="sxs-lookup"><span data-stu-id="e1848-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="e1848-147">Ale, pokud aplikace obsahuje více než jeden naslouchací proces, měli byste určit jedinečný název pro každý naslouchací proces trasování, které umožňuje identifikovat a spravovat jednotlivé trasování – moduly naslouchání v <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="e1848-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1848-148">Přidání více než jeden naslouchací proces trasování stejného typu a se stejným názvem výsledkem pouze jeden naslouchací daného typu a název, který se přidává do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="e1848-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="e1848-149">Však můžete prostřednictvím kódu programu přidat více identické moduly pro naslouchání na `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="e1848-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="e1848-150">Hodnota `initializeData` atribut závisí na typu naslouchacího procesu vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="e1848-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="e1848-151">Ne všechny trasování – moduly naslouchání vyžadují, aby `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="e1848-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1848-152">Při použití `initializeData` atributu, může získat kompilátoru upozornění "není deklarován atribut 'initializeData'."</span><span class="sxs-lookup"><span data-stu-id="e1848-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="e1848-153">Toto upozornění se zobrazí, protože nastavení konfigurace se ověřují vůči abstraktní základní třída <xref:System.Diagnostics.TraceListener>, který nebyl rozpoznán `initializeData` atribut.</span><span class="sxs-lookup"><span data-stu-id="e1848-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="e1848-154">Obvykle můžete toto upozornění pro implementace naslouchací proces trasování, které mají konstruktor, který přebírá parametr ignorovat.</span><span class="sxs-lookup"><span data-stu-id="e1848-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="e1848-155">Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí rozhraní .NET Framework a popisuje hodnotu jejich `initializeData` atributy.</span><span class="sxs-lookup"><span data-stu-id="e1848-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="e1848-156">Trasovací třída naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="e1848-156">Trace listener class</span></span>|<span data-ttu-id="e1848-157">Hodnota initializeData – atribut</span><span class="sxs-lookup"><span data-stu-id="e1848-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="e1848-158">`useErrorStream` Hodnota <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="e1848-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="e1848-159">Nastavte `initializeData` atribut "`true`"zápis trasování a ladění výstupu na standardní chybový proud; ji nastavte na"`false`" k zápisu do standardního výstupního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="e1848-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="e1848-160">Název souboru <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje do.</span><span class="sxs-lookup"><span data-stu-id="e1848-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="e1848-161">Název existující zdroj protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="e1848-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="e1848-162">Název souboru, který <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje do.</span><span class="sxs-lookup"><span data-stu-id="e1848-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="e1848-163">Název souboru, který <xref:System.Diagnostics.TextWriterTraceListener> zapisuje do.</span><span class="sxs-lookup"><span data-stu-id="e1848-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="e1848-164">Název souboru, který <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje do.</span><span class="sxs-lookup"><span data-stu-id="e1848-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="e1848-165">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="e1848-165">Configuration File</span></span>  
 <span data-ttu-id="e1848-166">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="e1848-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1848-167">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1848-167">Example</span></span>  
 <span data-ttu-id="e1848-168">Následující příklad ukazuje, jak používat `<add>` elementy přidat posluchače `console` a `textListener` k `Listeners` kolekci pro zdroj trasování `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="e1848-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="e1848-169">`textListener` Naslouchací proces zapisuje do souboru myListener.log výstup trasování.</span><span class="sxs-lookup"><span data-stu-id="e1848-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e1848-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1848-170">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="e1848-171">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="e1848-171">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="e1848-172">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="e1848-172">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
