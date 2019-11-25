---
title: <add> element pro <listeners> pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: c32205310f9fc451a5a55a943f925ee52f65c8a8
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088992"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="3daf2-102">\<přidat > element pro \<naslouchací proces > pro \<zdrojového ></span><span class="sxs-lookup"><span data-stu-id="3daf2-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="3daf2-103">Přidá naslouchací proces do kolekce `Listeners` pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="3daf2-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

<span data-ttu-id="3daf2-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3daf2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3daf2-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="3daf2-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="3daf2-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zdrojů >** ](sources-element.md)</span><span class="sxs-lookup"><span data-stu-id="3daf2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)</span></span>\
<span data-ttu-id="3daf2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zdroj >** ](source-element.md)</span><span class="sxs-lookup"><span data-stu-id="3daf2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)</span></span>\
<span data-ttu-id="3daf2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Listeners**](listeners-element-for-source.md) ></span><span class="sxs-lookup"><span data-stu-id="3daf2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)</span></span>\
<span data-ttu-id="3daf2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<přidat >**</span><span class="sxs-lookup"><span data-stu-id="3daf2-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3daf2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3daf2-110">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3daf2-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3daf2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3daf2-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3daf2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3daf2-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="3daf2-113">Attributes</span></span>  
  
|<span data-ttu-id="3daf2-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="3daf2-114">Attribute</span></span>|<span data-ttu-id="3daf2-115">Popis</span><span class="sxs-lookup"><span data-stu-id="3daf2-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="3daf2-116">Povinný atribut, pokud neodkazujete na naslouchací proces v kolekci `sharedListeners`, v takovém případě je nutné na něj odkazovat pouze podle názvu (viz [příklad](#example)).</span><span class="sxs-lookup"><span data-stu-id="3daf2-116">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="3daf2-117">Určuje typ naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="3daf2-117">Specifies the type of the listener.</span></span> <span data-ttu-id="3daf2-118">Je nutné použít řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="3daf2-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="3daf2-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3daf2-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3daf2-120">Řetězec předaný konstruktoru pro určenou třídu.</span><span class="sxs-lookup"><span data-stu-id="3daf2-120">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="3daf2-121">Pokud třída nemá konstruktor, který přebírá řetězec, je vyvolána <xref:System.Configuration.ConfigurationException>.</span><span class="sxs-lookup"><span data-stu-id="3daf2-121">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="3daf2-122">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3daf2-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3daf2-123">Určuje název naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="3daf2-123">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="3daf2-124">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="3daf2-124">Optional attribute.</span></span><br /><br /> <span data-ttu-id="3daf2-125">Určuje hodnotu vlastnosti <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> pro naslouchací proces trasování.</span><span class="sxs-lookup"><span data-stu-id="3daf2-125">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="3daf2-126">[vlastní atributy]</span><span class="sxs-lookup"><span data-stu-id="3daf2-126">[custom attributes]</span></span>|<span data-ttu-id="3daf2-127">Volitelné atributy.</span><span class="sxs-lookup"><span data-stu-id="3daf2-127">Optional attributes.</span></span><br /><br /> <span data-ttu-id="3daf2-128">Určuje hodnotu pro atributy specifické pro naslouchací proces identifikovaných metodou <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> pro daný naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="3daf2-128">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="3daf2-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> je příkladem nadbytečného atributu, který je jedinečný pro <xref:System.Diagnostics.DelimitedListTraceListener> třídu.</span><span class="sxs-lookup"><span data-stu-id="3daf2-129"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3daf2-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3daf2-130">Child Elements</span></span>  
  
|<span data-ttu-id="3daf2-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="3daf2-131">Element</span></span>|<span data-ttu-id="3daf2-132">Popis</span><span class="sxs-lookup"><span data-stu-id="3daf2-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3daf2-133">filtr \<</span><span class="sxs-lookup"><span data-stu-id="3daf2-133">\<filter></span></span>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="3daf2-134">Přidá filtr do naslouchacího procesu v kolekci `Listeners` pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="3daf2-134">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3daf2-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3daf2-135">Parent Elements</span></span>  
  
|<span data-ttu-id="3daf2-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="3daf2-136">Element</span></span>|<span data-ttu-id="3daf2-137">Popis</span><span class="sxs-lookup"><span data-stu-id="3daf2-137">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3daf2-138">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3daf2-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="3daf2-139">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="3daf2-139">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="3daf2-140">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="3daf2-140">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="3daf2-141">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="3daf2-141">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="3daf2-142">Určuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="3daf2-142">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3daf2-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3daf2-143">Remarks</span></span>  
 <span data-ttu-id="3daf2-144">Třídy naslouchacího procesu dodávané s .NET Framework jsou odvozeny z <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="3daf2-144">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="3daf2-145">Pokud nezadáte atribut `name` naslouchacího procesu trasování, vlastnost <xref:System.Diagnostics.TraceListener.Name%2A> naslouchacího procesu trasování je ve výchozím nastavení prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="3daf2-145">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="3daf2-146">Pokud má aplikace pouze jeden naslouchací proces, můžete ji přidat bez zadání názvu a můžete ji odebrat zadáním prázdného řetězce pro název.</span><span class="sxs-lookup"><span data-stu-id="3daf2-146">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="3daf2-147">Pokud však má vaše aplikace více než jeden naslouchací proces, měli byste pro každé naslouchací proces trasování zadat jedinečný název, který umožňuje identifikovat a spravovat jednotlivé naslouchací procesy trasování v kolekci <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3daf2-147">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3daf2-148">Přidání více než jednoho naslouchacího procesu trasování stejného typu a se stejným názvem má za následek pouze jeden naslouchací proces sledování tohoto typu a název přidaný do kolekce `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="3daf2-148">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="3daf2-149">Můžete však programově přidat do kolekce `Listeners` více stejných posluchačů.</span><span class="sxs-lookup"><span data-stu-id="3daf2-149">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="3daf2-150">Hodnota atributu `initializeData` závisí na typu naslouchacího procesu, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="3daf2-150">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="3daf2-151">Ne všechny naslouchací procesy trasování vyžadují, abyste zadali `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="3daf2-151">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3daf2-152">Při použití atributu `initializeData` se může zobrazit upozornění kompilátoru "atribut ' initializeData ' není deklarován."</span><span class="sxs-lookup"><span data-stu-id="3daf2-152">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="3daf2-153">K tomuto upozornění dochází, protože nastavení konfigurace je ověřeno proti abstraktní základní třídě <xref:System.Diagnostics.TraceListener>, která nerozeznává atribut `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="3daf2-153">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="3daf2-154">Obvykle můžete toto upozornění ignorovat pro implementace naslouchacího procesu trasování, které mají konstruktor, který přebírá parametr.</span><span class="sxs-lookup"><span data-stu-id="3daf2-154">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="3daf2-155">Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí .NET Framework a popisuje hodnotu jejich `initializeData` atributů.</span><span class="sxs-lookup"><span data-stu-id="3daf2-155">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="3daf2-156">Trace – třída naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="3daf2-156">Trace listener class</span></span>|<span data-ttu-id="3daf2-157">hodnota atributu initializeData</span><span class="sxs-lookup"><span data-stu-id="3daf2-157">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3daf2-158">Hodnota `useErrorStream` pro konstruktor <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="3daf2-158">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="3daf2-159">Nastavte atribut `initializeData` na "`true`" pro zápis trasování a ladění výstupu do standardního streamu chyb. nastavte ji na "`false`" pro zápis do standardního výstupního proudu.</span><span class="sxs-lookup"><span data-stu-id="3daf2-159">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3daf2-160">Název souboru, do kterého <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="3daf2-160">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3daf2-161">Název existujícího zdroje protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="3daf2-161">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3daf2-162">Název souboru, do kterého <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="3daf2-162">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3daf2-163">Název souboru, do kterého <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="3daf2-163">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="3daf2-164">Název souboru, do kterého <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.</span><span class="sxs-lookup"><span data-stu-id="3daf2-164">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="3daf2-165">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="3daf2-165">Configuration File</span></span>  
 <span data-ttu-id="3daf2-166">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="3daf2-166">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3daf2-167">Příklad</span><span class="sxs-lookup"><span data-stu-id="3daf2-167">Example</span></span>  
 <span data-ttu-id="3daf2-168">Následující příklad ukazuje, jak použít `<add>` prvky pro přidání `console` a `textListener` do kolekce `Listeners` pro `TraceSourceApp`zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="3daf2-168">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="3daf2-169">Naslouchací proces `textListener` zapisuje výstup trasování do souboru myListener. log.</span><span class="sxs-lookup"><span data-stu-id="3daf2-169">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3daf2-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3daf2-170">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="3daf2-171">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="3daf2-171">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3daf2-172">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="3daf2-172">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
