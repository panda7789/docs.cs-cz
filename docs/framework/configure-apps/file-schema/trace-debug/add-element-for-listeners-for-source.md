---
title: <add>Element pro <listeners> pro<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153682"
---
# <a name="add-element-for-listeners-for-source"></a><span data-ttu-id="7f152-102">\<add>Element pro \<listeners> pro\<source></span><span class="sxs-lookup"><span data-stu-id="7f152-102">\<add> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="7f152-103">Přidá naslouchací proces do `Listeners` kolekce pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="7f152-103">Adds a listener to the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="7f152-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f152-104">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f152-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7f152-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7f152-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7f152-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f152-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="7f152-107">Attributes</span></span>  
  
|<span data-ttu-id="7f152-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="7f152-108">Attribute</span></span>|<span data-ttu-id="7f152-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7f152-109">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="7f152-110">Povinný atribut, pokud neodkazujete na naslouchací proces v `sharedListeners` kolekci, v takovém případě je nutné na něj odkazovat pouze podle názvu (viz [příklad](#example)).</span><span class="sxs-lookup"><span data-stu-id="7f152-110">Required attribute, unless you're referencing a listener in the `sharedListeners` collection, in which case you only need to refer to it by name (see the [Example](#example)).</span></span><br /><br /> <span data-ttu-id="7f152-111">Určuje typ naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="7f152-111">Specifies the type of the listener.</span></span> <span data-ttu-id="7f152-112">Je nutné použít řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="7f152-112">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="7f152-113">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f152-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="7f152-114">Řetězec předaný konstruktoru pro určenou třídu.</span><span class="sxs-lookup"><span data-stu-id="7f152-114">The string passed to the constructor for the specified class.</span></span> <span data-ttu-id="7f152-115"><xref:System.Configuration.ConfigurationException>Výjimka je vyvolána, pokud třída nemá konstruktor, který přebírá řetězec.</span><span class="sxs-lookup"><span data-stu-id="7f152-115">A <xref:System.Configuration.ConfigurationException> is thrown if the class does not have a constructor that takes a string.</span></span>|  
|`name`|<span data-ttu-id="7f152-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f152-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="7f152-117">Určuje název naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="7f152-117">Specifies the name of the listener.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="7f152-118">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="7f152-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="7f152-119">Určuje <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> hodnotu vlastnosti naslouchacího procesu trasování.</span><span class="sxs-lookup"><span data-stu-id="7f152-119">Specifies the <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> property value for the trace listener.</span></span>|  
|<span data-ttu-id="7f152-120">[vlastní atributy]</span><span class="sxs-lookup"><span data-stu-id="7f152-120">[custom attributes]</span></span>|<span data-ttu-id="7f152-121">Volitelné atributy.</span><span class="sxs-lookup"><span data-stu-id="7f152-121">Optional attributes.</span></span><br /><br /> <span data-ttu-id="7f152-122">Určuje hodnotu pro atributy specifické pro naslouchací proces identifikovaných <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> metodou pro daný naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="7f152-122">Specifies the value for listener-specific attributes identified by the <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> method for that listener.</span></span> <span data-ttu-id="7f152-123"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>je příkladem nadbytečného atributu, který je jedinečný pro <xref:System.Diagnostics.DelimitedListTraceListener> třídu.</span><span class="sxs-lookup"><span data-stu-id="7f152-123"><xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> is an example of an extra attribute unique to the <xref:System.Diagnostics.DelimitedListTraceListener> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f152-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7f152-124">Child Elements</span></span>  
  
|<span data-ttu-id="7f152-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f152-125">Element</span></span>|<span data-ttu-id="7f152-126">Description</span><span class="sxs-lookup"><span data-stu-id="7f152-126">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="7f152-127">Přidá filtr do naslouchacího procesu v `Listeners` kolekci pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="7f152-127">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f152-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7f152-128">Parent Elements</span></span>  
  
|<span data-ttu-id="7f152-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f152-129">Element</span></span>|<span data-ttu-id="7f152-130">Description</span><span class="sxs-lookup"><span data-stu-id="7f152-130">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7f152-131">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7f152-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="7f152-132">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="7f152-132">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="7f152-133">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="7f152-133">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="7f152-134">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="7f152-134">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="7f152-135">Určuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="7f152-135">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f152-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f152-136">Remarks</span></span>  
 <span data-ttu-id="7f152-137">Třídy naslouchacího procesu dodávané s .NET Framework jsou odvozeny z <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="7f152-137">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="7f152-138">Pokud nezadáte `name` atribut naslouchacího procesu trasování, <xref:System.Diagnostics.TraceListener.Name%2A> vlastnost naslouchacího procesu trasování je ve výchozím nastavení prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="7f152-138">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> property of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="7f152-139">Pokud má aplikace pouze jeden naslouchací proces, můžete ji přidat bez zadání názvu a můžete ji odebrat zadáním prázdného řetězce pro název.</span><span class="sxs-lookup"><span data-stu-id="7f152-139">If your application has only one listener, you can add it without specifying a name, and you can remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="7f152-140">Pokud však má vaše aplikace více než jeden naslouchací proces, měli byste pro každé naslouchací proces trasování zadat jedinečný název, který umožňuje identifikovat a spravovat jednotlivé naslouchací procesy trasování v <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> kolekci.</span><span class="sxs-lookup"><span data-stu-id="7f152-140">However, if your application has more than one listener, you should specify a unique name for each trace listener, which allows you to identify and manage individual trace listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f152-141">Přidání více než jednoho naslouchacího procesu trasování stejného typu a se stejným názvem má za následek pouze jeden naslouchací proces pro daný typ a název přidaný do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="7f152-141">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="7f152-142">Můžete však programově přidat do kolekce více identických posluchačů `Listeners` .</span><span class="sxs-lookup"><span data-stu-id="7f152-142">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="7f152-143">Hodnota `initializeData` atributu závisí na typu naslouchacího procesu, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="7f152-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="7f152-144">Ne všechny naslouchací procesy trasování vyžadují, abyste určili `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="7f152-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f152-145">Při použití atributu se `initializeData` může zobrazit upozornění kompilátoru "atribut ' initializeData ' není deklarován."</span><span class="sxs-lookup"><span data-stu-id="7f152-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="7f152-146">K tomuto upozornění dochází, protože nastavení konfigurace je ověřeno proti abstraktní základní třídě <xref:System.Diagnostics.TraceListener> , která atribut nerozpoznala `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="7f152-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="7f152-147">Obvykle můžete toto upozornění ignorovat pro implementace naslouchacího procesu trasování, které mají konstruktor, který přebírá parametr.</span><span class="sxs-lookup"><span data-stu-id="7f152-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="7f152-148">Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí .NET Framework a popisuje hodnotu jejich `initializeData` atributů.</span><span class="sxs-lookup"><span data-stu-id="7f152-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="7f152-149">Trace – třída naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="7f152-149">Trace listener class</span></span>|<span data-ttu-id="7f152-150">hodnota atributu initializeData</span><span class="sxs-lookup"><span data-stu-id="7f152-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="7f152-151">`useErrorStream`Hodnota pro <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktor</span><span class="sxs-lookup"><span data-stu-id="7f152-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="7f152-152">Nastavte `initializeData` atribut na " `true` " pro zápis trasování a ladění výstupu do standardního streamu chyb. nastavte ho na "", chcete-li `false` zapisovat do standardního výstupního proudu.</span><span class="sxs-lookup"><span data-stu-id="7f152-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="7f152-153">Název souboru, do kterého se <xref:System.Diagnostics.DelimitedListTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="7f152-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="7f152-154">Název existujícího zdroje protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="7f152-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="7f152-155">Název souboru, do kterého se <xref:System.Diagnostics.EventSchemaTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="7f152-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="7f152-156">Název souboru, do kterého se <xref:System.Diagnostics.TextWriterTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="7f152-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="7f152-157">Název souboru, do kterého se <xref:System.Diagnostics.XmlWriterTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="7f152-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="7f152-158">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="7f152-158">Configuration File</span></span>  
 <span data-ttu-id="7f152-159">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="7f152-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f152-160">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f152-160">Example</span></span>  
 <span data-ttu-id="7f152-161">Následující příklad ukazuje, jak použít `<add>` prvky pro přidání posluchačů `console` a `textListener` do `Listeners` kolekce pro zdroj trasování `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="7f152-161">The following example shows how to use `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="7f152-162">`textListener`Naslouchací proces zapisuje výstup trasování do souboru MyListener. log.</span><span class="sxs-lookup"><span data-stu-id="7f152-162">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f152-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f152-163">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="7f152-164">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="7f152-164">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7f152-165">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="7f152-165">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
