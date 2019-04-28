---
title: <add> – Element pro <listeners> pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 4d2952e29b09fcf9f81624317e30caf301a61a51
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701486"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="770dc-102">\<Přidat > – Element pro \<naslouchacích procesů > pro \<zdroje ></span><span class="sxs-lookup"><span data-stu-id="770dc-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="770dc-103">Přidá naslouchací proces pro `Listeners` kolekci pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="770dc-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="770dc-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="770dc-104">\<configuration></span></span>  
<span data-ttu-id="770dc-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="770dc-105">\<system.diagnostics></span></span>  
<span data-ttu-id="770dc-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="770dc-106">\<sources></span></span>  
<span data-ttu-id="770dc-107">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="770dc-107">\<source></span></span>  
<span data-ttu-id="770dc-108">\<naslouchací procesy ></span><span class="sxs-lookup"><span data-stu-id="770dc-108">\<listeners></span></span>  
<span data-ttu-id="770dc-109">\<add></span><span class="sxs-lookup"><span data-stu-id="770dc-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="770dc-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="770dc-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="770dc-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="770dc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="770dc-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="770dc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="770dc-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="770dc-113">Attributes</span></span>  
  
|<span data-ttu-id="770dc-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="770dc-114">Attribute</span></span>|<span data-ttu-id="770dc-115">Popis</span><span class="sxs-lookup"><span data-stu-id="770dc-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="770dc-116">Požadovaný atribut, pokud už odkazuje na naslouchací proces ve `sharedListeners` kolekce, ve kterém malá a velká je potřeba pouze na ni odkazovat podle názvu (viz [příklad](#example)).</span><span class="sxs-lookup"><span data-stu-id="770dc-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="770dc-117">Určuje typ naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="770dc-117">Specifies the type of the listener.</span></span> <span data-ttu-id="770dc-118">Je nutné použít řetězec, který splňuje požadavky uvedené v [zadání plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="770dc-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="770dc-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="770dc-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="770dc-120">Řetězec předaný konstruktoru pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="770dc-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="770dc-121">A <xref:System.Configuration.ConfigurationException> je vyvolána, pokud třída nemá konstruktor, který přijímá řetězec.</span><span class="sxs-lookup"><span data-stu-id="770dc-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="770dc-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="770dc-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="770dc-123">Určuje název naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="770dc-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="770dc-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="770dc-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="770dc-125">Určuje, <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> hodnota vlastnosti pro posluchače trasování.</span><span class="sxs-lookup"><span data-stu-id="770dc-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="770dc-126">[vlastní atributy]</span><span class="sxs-lookup"><span data-stu-id="770dc-126">[custom attributes]</span></span>|<span data-ttu-id="770dc-127">Volitelné atributy.</span><span class="sxs-lookup"><span data-stu-id="770dc-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="770dc-128">Určuje hodnotu pro atributy specifické pro naslouchací proces identifikován <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> metody pro tuto naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="770dc-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="770dc-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> je příkladem atribut navíc jedinečné pro <xref:System.Diagnostics.DelimitedListTraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="770dc-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="770dc-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="770dc-130">Child Elements</span></span>  
  
|<span data-ttu-id="770dc-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="770dc-131">Element</span></span>|<span data-ttu-id="770dc-132">Popis</span><span class="sxs-lookup"><span data-stu-id="770dc-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="770dc-133">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="770dc-133">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="770dc-134">Přidá filtr do naslouchacího procesu v `Listeners` kolekci pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="770dc-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="770dc-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="770dc-135">Parent Elements</span></span>  
  
|<span data-ttu-id="770dc-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="770dc-136">Element</span></span>|<span data-ttu-id="770dc-137">Popis</span><span class="sxs-lookup"><span data-stu-id="770dc-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="770dc-138">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="770dc-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="770dc-139">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="770dc-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="770dc-140">Obsahuje zdrojů trasování, které se zahájí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="770dc-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="770dc-141">Určuje zdroj trasování, který iniciuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="770dc-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="770dc-142">Určuje naslouchací procesy, které shromažďování, ukládání a směrovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="770dc-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="770dc-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="770dc-143">Remarks</span></span>  
 <span data-ttu-id="770dc-144">Naslouchací proces třídy součástí rozhraní .NET Framework jsou odvozeny od <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="770dc-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="770dc-145">Pokud nezadáte `name` atribut naslouchací proces trasování <xref:System.Diagnostics.TraceListener.Name%2A> vlastnost naslouchací služby stopy výchozí hodnota je prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="770dc-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="770dc-146">Pokud vaše aplikace má pouze jeden naslouchací proces, ho přidáte bez zadání názvu a můžete ho odebrat tak, že zadáte název prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="770dc-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="770dc-147">Ale, pokud aplikace obsahuje více než jeden naslouchací proces, měli byste určit jedinečný název pro každý naslouchací proces trasování, které umožňuje identifikovat a spravovat naslouchacích procesů jednotlivých trasování v <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="770dc-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="770dc-148">Přidání více než jeden naslouchací proces trasování stejného typu a se stejnou pojmenujte výsledky v pouze jeden naslouchací daného typu a se přidávají do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="770dc-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="770dc-149">Však můžete programově přidat několik identických naslouchacích procesů k `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="770dc-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="770dc-150">Hodnota `initializeData` atributu závisí na typu naslouchacího procesu vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="770dc-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="770dc-151">Ne všechny moduly pro naslouchání trasování vyžadují, abyste určili `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="770dc-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="770dc-152">Při použití `initializeData` atributu, může se zobrazit kompilátoru upozornění "není deklarovaný atribut"initializeData"."</span><span class="sxs-lookup"><span data-stu-id="770dc-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="770dc-153">K tomuto upozornění dochází, protože nastavení konfigurace se ověří proti abstraktní základní třída <xref:System.Diagnostics.TraceListener>, které nebylo rozpoznáno `initializeData` atribut.</span><span class="sxs-lookup"><span data-stu-id="770dc-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="770dc-154">Obvykle můžete ignorovat toto upozornění pro implementace naslouchací proces trasování, které mají konstruktor, který přijímá parametr.</span><span class="sxs-lookup"><span data-stu-id="770dc-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="770dc-155">Následující tabulka uvádí naslouchacích procesů trasování, které jsou součástí rozhraní .NET Framework a popisuje výhody jejich `initializeData` atributy.</span><span class="sxs-lookup"><span data-stu-id="770dc-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="770dc-156">Třída naslouchací proces trasování</span><span class="sxs-lookup"><span data-stu-id="770dc-156">Trace listener class</span></span>|<span data-ttu-id="770dc-157">Hodnota atributu initializeData</span><span class="sxs-lookup"><span data-stu-id="770dc-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="770dc-158">`useErrorStream` Hodnota <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="770dc-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="770dc-159">Nastavte `initializeData` atribut "`true`"zápis trasování a ladění výstupu na standardní chybový proud; nastavte ho na"`false`" k zápisu do standardního výstupního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="770dc-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="770dc-160">Název souboru <xref:System.Diagnostics.DelimitedListTraceListener> zapíše do.</span><span class="sxs-lookup"><span data-stu-id="770dc-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="770dc-161">Název existující zdroj protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="770dc-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="770dc-162">Název souboru, který <xref:System.Diagnostics.EventSchemaTraceListener> zapíše do.</span><span class="sxs-lookup"><span data-stu-id="770dc-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="770dc-163">Název souboru, který <xref:System.Diagnostics.TextWriterTraceListener> zapíše do.</span><span class="sxs-lookup"><span data-stu-id="770dc-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="770dc-164">Název souboru, který <xref:System.Diagnostics.XmlWriterTraceListener> zapíše do.</span><span class="sxs-lookup"><span data-stu-id="770dc-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="770dc-165">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="770dc-165">Configuration File</span></span>  
 <span data-ttu-id="770dc-166">Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="770dc-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="770dc-167">Příklad</span><span class="sxs-lookup"><span data-stu-id="770dc-167">Example</span></span>  
 <span data-ttu-id="770dc-168">Následující příklad ukazuje, jak používat `<add>` prvky pro přidání posluchače `console` a `textListener` k `Listeners` kolekce pro zdroj trasování `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="770dc-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="770dc-169">`textListener` Naslouchacího procesu zapisuje do souboru myListener.log výstupu trasování.</span><span class="sxs-lookup"><span data-stu-id="770dc-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="770dc-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="770dc-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="770dc-171">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="770dc-171">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="770dc-172">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="770dc-172">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
