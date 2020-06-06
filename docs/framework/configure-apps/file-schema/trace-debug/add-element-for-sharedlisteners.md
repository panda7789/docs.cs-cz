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
ms.openlocfilehash: 5588892ec75a791eda1eb043936c0af95e79354e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153604"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="24d4a-102">\<add> – element pro \<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="24d4a-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="24d4a-103">Přidá naslouchací proces do `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="24d4a-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="24d4a-104">`sharedListeners`je kolekce posluchačů, na které [\<source>](source-element.md) odkazuje jakýkoli nebo [\<trace>](trace-element.md) může odkazovat.</span><span class="sxs-lookup"><span data-stu-id="24d4a-104">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="24d4a-105">Ve výchozím nastavení nejsou naslouchací procesy v `sharedListeners` kolekci umístěny do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="24d4a-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="24d4a-106">Musí být přidány podle názvu do [\<source>](source-element.md) nebo [\<trace>](trace-element.md) .</span><span class="sxs-lookup"><span data-stu-id="24d4a-106">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="24d4a-107">Není možné získat naslouchací procesy v `sharedListeners` kolekci v kódu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="24d4a-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="24d4a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24d4a-108">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24d4a-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="24d4a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="24d4a-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="24d4a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24d4a-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="24d4a-111">Attributes</span></span>  
  
|<span data-ttu-id="24d4a-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="24d4a-112">Attribute</span></span>|<span data-ttu-id="24d4a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="24d4a-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="24d4a-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="24d4a-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="24d4a-115">Určuje název naslouchacího procesu, který se používá k přidání sdíleného naslouchacího procesu do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="24d4a-115">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="24d4a-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="24d4a-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="24d4a-117">Určuje typ naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="24d4a-117">Specifies the type of the listener.</span></span> <span data-ttu-id="24d4a-118">Je nutné použít řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="24d4a-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="24d4a-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="24d4a-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="24d4a-120">Řetězec předaný konstruktoru pro určenou třídu.</span><span class="sxs-lookup"><span data-stu-id="24d4a-120">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="24d4a-121">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="24d4a-121">Optional attribute.</span></span><br/><br/><span data-ttu-id="24d4a-122">Řetězcové vyjádření jednoho nebo více <xref:System.Diagnostics.TraceOptions> členů výčtu, které označují data, která mají být zapsána do výstupu trasování.</span><span class="sxs-lookup"><span data-stu-id="24d4a-122">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="24d4a-123">Více položek je odděleno čárkami.</span><span class="sxs-lookup"><span data-stu-id="24d4a-123">Multiple items are separated by commas.</span></span> <span data-ttu-id="24d4a-124">Výchozí hodnota je None (žádné).</span><span class="sxs-lookup"><span data-stu-id="24d4a-124">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="24d4a-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="24d4a-125">Child Elements</span></span>  
  
|<span data-ttu-id="24d4a-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="24d4a-126">Element</span></span>|<span data-ttu-id="24d4a-127">Description</span><span class="sxs-lookup"><span data-stu-id="24d4a-127">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="24d4a-128">Přidá filtr do naslouchacího procesu v `sharedListeners` kolekci.</span><span class="sxs-lookup"><span data-stu-id="24d4a-128">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24d4a-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="24d4a-129">Parent Elements</span></span>  
  
|<span data-ttu-id="24d4a-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="24d4a-130">Element</span></span>|<span data-ttu-id="24d4a-131">Description</span><span class="sxs-lookup"><span data-stu-id="24d4a-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="24d4a-132">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="24d4a-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="24d4a-133">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="24d4a-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="24d4a-134">Kolekce posluchačů, na které může odkazovat jakýkoliv element source nebo Trace.</span><span class="sxs-lookup"><span data-stu-id="24d4a-134">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24d4a-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24d4a-135">Remarks</span></span>  
 <span data-ttu-id="24d4a-136">Třídy naslouchacího procesu dodávané s .NET Framework jsou odvozeny z <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="24d4a-136">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="24d4a-137">Hodnota pro `name` atribut se používá pro přidání sdíleného naslouchacího procesu do `Listeners` kolekce pro trasování nebo zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="24d4a-137">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="24d4a-138">Hodnota `initializeData` atributu závisí na typu naslouchacího procesu, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="24d4a-138">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="24d4a-139">Ne všechny naslouchací procesy trasování vyžadují, abyste určili `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="24d4a-139">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24d4a-140">Při použití atributu se `initializeData` může zobrazit upozornění kompilátoru "atribut ' initializeData ' není deklarován."</span><span class="sxs-lookup"><span data-stu-id="24d4a-140">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="24d4a-141">K tomuto upozornění dochází, protože nastavení konfigurace je ověřeno proti abstraktní základní třídě <xref:System.Diagnostics.TraceListener> , která atribut nerozpoznala `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="24d4a-141">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="24d4a-142">Obvykle můžete toto upozornění ignorovat pro implementace naslouchacího procesu trasování, které mají konstruktor, který přebírá parametr.</span><span class="sxs-lookup"><span data-stu-id="24d4a-142">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="24d4a-143">Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí .NET Framework a popisuje hodnotu jejich `initializeData` atributů.</span><span class="sxs-lookup"><span data-stu-id="24d4a-143">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="24d4a-144">Trace – třída naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="24d4a-144">Trace listener class</span></span>|<span data-ttu-id="24d4a-145">hodnota atributu initializeData</span><span class="sxs-lookup"><span data-stu-id="24d4a-145">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="24d4a-146">`useErrorStream`Hodnota pro <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktor</span><span class="sxs-lookup"><span data-stu-id="24d4a-146">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="24d4a-147">Nastavte `initializeData` atribut na " `true` " pro zápis trasování a ladění výstupu do standardního streamu chyb. nastavte ho na "", chcete-li `false` zapisovat do standardního výstupního proudu.</span><span class="sxs-lookup"><span data-stu-id="24d4a-147">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="24d4a-148">Název souboru, do kterého se <xref:System.Diagnostics.DelimitedListTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="24d4a-148">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="24d4a-149">Název existujícího zdroje protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="24d4a-149">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="24d4a-150">Název souboru, do kterého se <xref:System.Diagnostics.EventSchemaTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="24d4a-150">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="24d4a-151">Název souboru, do kterého se <xref:System.Diagnostics.TextWriterTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="24d4a-151">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="24d4a-152">Název souboru, do kterého se <xref:System.Diagnostics.XmlWriterTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="24d4a-152">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="24d4a-153">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="24d4a-153">Configuration File</span></span>  
 <span data-ttu-id="24d4a-154">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="24d4a-154">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24d4a-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="24d4a-155">Example</span></span>  
 <span data-ttu-id="24d4a-156">Následující příklad ukazuje, jak použít `<add>` prvky pro přidání do <xref:System.Diagnostics.TextWriterTraceListener> `textListener` `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="24d4a-156">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="24d4a-157">`textListener`je přidán podle názvu do `Listeners` kolekce pro zdroj trasování `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="24d4a-157">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="24d4a-158">`textListener`Naslouchací proces zapisuje výstup trasování do souboru MyListener. log.</span><span class="sxs-lookup"><span data-stu-id="24d4a-158">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="24d4a-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="24d4a-159">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="24d4a-160">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="24d4a-160">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="24d4a-161">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="24d4a-161">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
