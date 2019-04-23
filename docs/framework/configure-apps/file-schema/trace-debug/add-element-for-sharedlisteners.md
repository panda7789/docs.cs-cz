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
ms.openlocfilehash: e7934ed5e71005cfd28271298ff6ce1eb8829a0d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095630"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="faf1d-102">\<Přidat > – Element pro \<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="faf1d-102">\<add> Element for \<sharedListeners></span></span>
<span data-ttu-id="faf1d-103">Přidá naslouchací proces pro `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="faf1d-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="faf1d-104">`sharedListeners` je kolekce naslouchacích procesů, aby každá [ \<zdroj >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) nebo [ \<trasování >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) můžete odkazovat.</span><span class="sxs-lookup"><span data-stu-id="faf1d-104">`sharedListeners` is a collection of listeners that any [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) can reference.</span></span>  <span data-ttu-id="faf1d-105">Ve výchozím nastavení, moduly pro naslouchání v `sharedListeners` kolekce nejsou umístěny v `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="faf1d-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="faf1d-106">Musí se přidat název, který [ \<zdroj >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) nebo [ \<trasování >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span><span class="sxs-lookup"><span data-stu-id="faf1d-106">They must be added by name to the [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span></span> <span data-ttu-id="faf1d-107">Není možné získat naslouchacím procesům `sharedListeners` kolekce v kódu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="faf1d-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
 <span data-ttu-id="faf1d-108">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="faf1d-108">\<configuration></span></span>  
<span data-ttu-id="faf1d-109">&nbsp;&nbsp;\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="faf1d-109">&nbsp;&nbsp;\<system.diagnostics></span></span>  
<span data-ttu-id="faf1d-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners > – Element</span><span class="sxs-lookup"><span data-stu-id="faf1d-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners> Element</span></span>  
<span data-ttu-id="faf1d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add></span><span class="sxs-lookup"><span data-stu-id="faf1d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faf1d-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="faf1d-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="faf1d-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="faf1d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="faf1d-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="faf1d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="faf1d-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="faf1d-115">Attributes</span></span>  
  
|<span data-ttu-id="faf1d-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="faf1d-116">Attribute</span></span>|<span data-ttu-id="faf1d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="faf1d-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="faf1d-118">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="faf1d-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="faf1d-119">Určuje název, který se používá k přidání sdílené naslouchací proces pro naslouchací proces `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="faf1d-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="faf1d-120">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="faf1d-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="faf1d-121">Určuje typ naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="faf1d-121">Specifies the type of the listener.</span></span> <span data-ttu-id="faf1d-122">Je nutné použít řetězec, který splňuje požadavky uvedené v [zadání plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="faf1d-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="faf1d-123">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="faf1d-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="faf1d-124">Řetězec předaný konstruktoru pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="faf1d-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="faf1d-125">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="faf1d-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="faf1d-126">Řetězcové vyjádření jednoho nebo víc <xref:System.Diagnostics.TraceOptions> členy výčtu, které určuje dat zapisovaných do výstupu trasování.</span><span class="sxs-lookup"><span data-stu-id="faf1d-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="faf1d-127">Více položek jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="faf1d-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="faf1d-128">Výchozí hodnota je "None".</span><span class="sxs-lookup"><span data-stu-id="faf1d-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="faf1d-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="faf1d-129">Child Elements</span></span>  
  
|<span data-ttu-id="faf1d-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="faf1d-130">Element</span></span>|<span data-ttu-id="faf1d-131">Popis</span><span class="sxs-lookup"><span data-stu-id="faf1d-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="faf1d-132">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="faf1d-132">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="faf1d-133">Přidá filtr do naslouchacího procesu v `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="faf1d-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="faf1d-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="faf1d-134">Parent Elements</span></span>  
  
|<span data-ttu-id="faf1d-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="faf1d-135">Element</span></span>|<span data-ttu-id="faf1d-136">Popis</span><span class="sxs-lookup"><span data-stu-id="faf1d-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="faf1d-137">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="faf1d-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="faf1d-138">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="faf1d-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="faf1d-139">Kolekce naslouchacích procesů, které všechny zdroje nebo trasování – element může odkazovat.</span><span class="sxs-lookup"><span data-stu-id="faf1d-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faf1d-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="faf1d-140">Remarks</span></span>  
 <span data-ttu-id="faf1d-141">Naslouchací proces třídy součástí rozhraní .NET Framework jsou odvozeny od <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="faf1d-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="faf1d-142">Hodnota `name` atribut se používá k přidání sdílené naslouchací proces pro `Listeners` kolekce pro trasování nebo zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="faf1d-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="faf1d-143">Hodnota `initializeData` atributu závisí na typu naslouchacího procesu vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="faf1d-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="faf1d-144">Ne všechny moduly pro naslouchání trasování vyžadují, abyste určili `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="faf1d-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="faf1d-145">Při použití `initializeData` atributu, může se zobrazit kompilátoru upozornění "není deklarovaný atribut"initializeData"."</span><span class="sxs-lookup"><span data-stu-id="faf1d-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="faf1d-146">K tomuto upozornění dochází, protože nastavení konfigurace se ověří proti abstraktní základní třída <xref:System.Diagnostics.TraceListener>, které nebylo rozpoznáno `initializeData` atribut.</span><span class="sxs-lookup"><span data-stu-id="faf1d-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="faf1d-147">Obvykle můžete ignorovat toto upozornění pro implementace naslouchací proces trasování, které mají konstruktor, který přijímá parametr.</span><span class="sxs-lookup"><span data-stu-id="faf1d-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="faf1d-148">Následující tabulka uvádí naslouchacích procesů trasování, které jsou součástí rozhraní .NET Framework a popisuje výhody jejich `initializeData` atributy.</span><span class="sxs-lookup"><span data-stu-id="faf1d-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="faf1d-149">Třída naslouchací proces trasování</span><span class="sxs-lookup"><span data-stu-id="faf1d-149">Trace listener class</span></span>|<span data-ttu-id="faf1d-150">Hodnota atributu initializeData</span><span class="sxs-lookup"><span data-stu-id="faf1d-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="faf1d-151">`useErrorStream` Hodnota <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="faf1d-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="faf1d-152">Nastavte `initializeData` atribut "`true`"zápis trasování a ladění výstupu na standardní chybový proud; nastavte ho na"`false`" k zápisu do standardního výstupního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="faf1d-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="faf1d-153">Název souboru <xref:System.Diagnostics.DelimitedListTraceListener> zapíše do.</span><span class="sxs-lookup"><span data-stu-id="faf1d-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="faf1d-154">Název existující zdroj protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="faf1d-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="faf1d-155">Název souboru, který <xref:System.Diagnostics.EventSchemaTraceListener> zapíše do.</span><span class="sxs-lookup"><span data-stu-id="faf1d-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="faf1d-156">Název souboru, který <xref:System.Diagnostics.TextWriterTraceListener> zapíše do.</span><span class="sxs-lookup"><span data-stu-id="faf1d-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="faf1d-157">Název souboru, který <xref:System.Diagnostics.XmlWriterTraceListener> zapíše do.</span><span class="sxs-lookup"><span data-stu-id="faf1d-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="faf1d-158">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="faf1d-158">Configuration File</span></span>  
 <span data-ttu-id="faf1d-159">Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="faf1d-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="faf1d-160">Příklad</span><span class="sxs-lookup"><span data-stu-id="faf1d-160">Example</span></span>  
 <span data-ttu-id="faf1d-161">Následující příklad ukazuje, jak používat `<add>` prvky pro přidání <xref:System.Diagnostics.TextWriterTraceListener> `textListener` k `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="faf1d-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="faf1d-162">`textListener` název, který přidává `Listeners` kolekce pro zdroj trasování `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="faf1d-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="faf1d-163">`textListener` Naslouchacího procesu zapisuje do souboru myListener.log výstupu trasování.</span><span class="sxs-lookup"><span data-stu-id="faf1d-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="faf1d-164">Viz také:</span><span class="sxs-lookup"><span data-stu-id="faf1d-164">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="faf1d-165">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="faf1d-165">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="faf1d-166">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="faf1d-166">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
