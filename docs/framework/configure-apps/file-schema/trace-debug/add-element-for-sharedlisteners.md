---
title: <add> – element pro <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: c4b83834fb7aaf64a696b85bd2c8da47cfba2397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927216"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="eff78-102">\<Přidat > element pro \<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="eff78-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="eff78-103">Přidá naslouchací proces do `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="eff78-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="eff78-104">`sharedListeners`je kolekce posluchačů, které mohou odkazovat všechny [ \<zdrojové >](source-element.md) nebo [ \<> trasování](trace-element.md) .</span><span class="sxs-lookup"><span data-stu-id="eff78-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="eff78-105">Ve výchozím nastavení nejsou naslouchací procesy `sharedListeners` v kolekci umístěny `Listeners` do kolekce.</span><span class="sxs-lookup"><span data-stu-id="eff78-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="eff78-106">Musí být přidány podle názvu do [ \<zdrojového >](source-element.md) nebo [ \<> trasování](trace-element.md).</span><span class="sxs-lookup"><span data-stu-id="eff78-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="eff78-107">Není možné získat naslouchací procesy v `sharedListeners` kolekci v kódu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="eff78-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
 <span data-ttu-id="eff78-108">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="eff78-108">\<configuration></span></span>  
<span data-ttu-id="eff78-109">&nbsp;&nbsp;\<> System. Diagnostics</span><span class="sxs-lookup"><span data-stu-id="eff78-109">&nbsp;&nbsp;\<system.diagnostics></span></span>  
<span data-ttu-id="eff78-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners – > element</span><span class="sxs-lookup"><span data-stu-id="eff78-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners> Element</span></span>  
<span data-ttu-id="eff78-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="eff78-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eff78-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eff78-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eff78-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eff78-113">Attributes and Elements</span></span>  
 <span data-ttu-id="eff78-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eff78-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eff78-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="eff78-115">Attributes</span></span>  
  
|<span data-ttu-id="eff78-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="eff78-116">Attribute</span></span>|<span data-ttu-id="eff78-117">Popis</span><span class="sxs-lookup"><span data-stu-id="eff78-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="eff78-118">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="eff78-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="eff78-119">Určuje název naslouchacího procesu, který se používá k přidání sdíleného naslouchacího procesu do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="eff78-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="eff78-120">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="eff78-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="eff78-121">Určuje typ naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="eff78-121">Specifies the type of the listener.</span></span> <span data-ttu-id="eff78-122">Je nutné použít řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="eff78-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="eff78-123">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="eff78-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="eff78-124">Řetězec předaný konstruktoru pro určenou třídu.</span><span class="sxs-lookup"><span data-stu-id="eff78-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="eff78-125">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="eff78-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="eff78-126">Řetězcové vyjádření jednoho nebo více <xref:System.Diagnostics.TraceOptions> členů výčtu, které označují data, která mají být zapsána do výstupu trasování.</span><span class="sxs-lookup"><span data-stu-id="eff78-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="eff78-127">Více položek je odděleno čárkami.</span><span class="sxs-lookup"><span data-stu-id="eff78-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="eff78-128">Výchozí hodnota je None (žádné).</span><span class="sxs-lookup"><span data-stu-id="eff78-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="eff78-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="eff78-129">Child Elements</span></span>  
  
|<span data-ttu-id="eff78-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="eff78-130">Element</span></span>|<span data-ttu-id="eff78-131">Popis</span><span class="sxs-lookup"><span data-stu-id="eff78-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eff78-132">\<Filtrovat ></span><span class="sxs-lookup"><span data-stu-id="eff78-132">\<filter></span></span>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="eff78-133">Přidá filtr do naslouchacího procesu v `sharedListeners` kolekci.</span><span class="sxs-lookup"><span data-stu-id="eff78-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eff78-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="eff78-134">Parent Elements</span></span>  
  
|<span data-ttu-id="eff78-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="eff78-135">Element</span></span>|<span data-ttu-id="eff78-136">Popis</span><span class="sxs-lookup"><span data-stu-id="eff78-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="eff78-137">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eff78-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="eff78-138">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="eff78-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="eff78-139">Kolekce posluchačů, na které může odkazovat jakýkoliv element source nebo Trace.</span><span class="sxs-lookup"><span data-stu-id="eff78-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eff78-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eff78-140">Remarks</span></span>  
 <span data-ttu-id="eff78-141">Třídy naslouchacího procesu dodávané s .NET Framework jsou odvozeny z <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="eff78-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="eff78-142">Hodnota pro `name` atribut se používá pro přidání sdíleného naslouchacího procesu `Listeners` do kolekce pro trasování nebo zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="eff78-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="eff78-143">Hodnota `initializeData` atributu závisí na typu naslouchacího procesu, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="eff78-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="eff78-144">Ne všechny naslouchací procesy trasování vyžadují, abyste `initializeData`určili.</span><span class="sxs-lookup"><span data-stu-id="eff78-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eff78-145">Při použití `initializeData` atributu se může zobrazit upozornění kompilátoru "atribut ' initializeData ' není deklarován."</span><span class="sxs-lookup"><span data-stu-id="eff78-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="eff78-146">K tomuto upozornění dochází, protože nastavení konfigurace je ověřeno proti abstraktní základní <xref:System.Diagnostics.TraceListener>třídě, která `initializeData` atribut nerozpoznala.</span><span class="sxs-lookup"><span data-stu-id="eff78-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="eff78-147">Obvykle můžete toto upozornění ignorovat pro implementace naslouchacího procesu trasování, které mají konstruktor, který přebírá parametr.</span><span class="sxs-lookup"><span data-stu-id="eff78-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="eff78-148">Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí .NET Framework a popisuje hodnotu jejich `initializeData` atributů.</span><span class="sxs-lookup"><span data-stu-id="eff78-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="eff78-149">Trace – třída naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="eff78-149">Trace listener class</span></span>|<span data-ttu-id="eff78-150">hodnota atributu initializeData</span><span class="sxs-lookup"><span data-stu-id="eff78-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="eff78-151">`useErrorStream` Hodnota<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> pro konstruktor</span><span class="sxs-lookup"><span data-stu-id="eff78-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="eff78-152">Nastavte atribut na "" pro zápis trasování a ladění výstupu do standardního streamu chyb. nastavte ho na "`false`", chcete-li zapisovat do standardního výstupního proudu.`true` `initializeData`</span><span class="sxs-lookup"><span data-stu-id="eff78-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="eff78-153">Název souboru, do kterého se <xref:System.Diagnostics.DelimitedListTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="eff78-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="eff78-154">Název existujícího zdroje protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="eff78-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="eff78-155">Název souboru, do kterého se <xref:System.Diagnostics.EventSchemaTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="eff78-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="eff78-156">Název souboru, do kterého se <xref:System.Diagnostics.TextWriterTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="eff78-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="eff78-157">Název souboru, do kterého se <xref:System.Diagnostics.XmlWriterTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="eff78-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="eff78-158">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="eff78-158">Configuration File</span></span>  
 <span data-ttu-id="eff78-159">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="eff78-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eff78-160">Příklad</span><span class="sxs-lookup"><span data-stu-id="eff78-160">Example</span></span>  
 <span data-ttu-id="eff78-161">Následující příklad ukazuje `<add>` , jak použít prvky pro <xref:System.Diagnostics.TextWriterTraceListener> `textListener` přidání `sharedListeners` do kolekce.</span><span class="sxs-lookup"><span data-stu-id="eff78-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="eff78-162">`textListener`je přidán podle názvu do `Listeners` kolekce pro zdroj `TraceSourceApp`trasování.</span><span class="sxs-lookup"><span data-stu-id="eff78-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="eff78-163">`textListener` Naslouchací proces zapisuje výstup trasování do souboru MyListener. log.</span><span class="sxs-lookup"><span data-stu-id="eff78-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eff78-164">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eff78-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="eff78-165">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="eff78-165">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="eff78-166">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="eff78-166">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
