---
title: "&lt;Přidat&gt; Element pro &lt;sharedListeners&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 490e58d4514667c5ec781dd76644012b0c97509d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltsharedlistenersgt"></a><span data-ttu-id="a3012-102">&lt;Přidat&gt; Element pro &lt;sharedListeners&gt;</span><span class="sxs-lookup"><span data-stu-id="a3012-102">&lt;add&gt; Element for &lt;sharedListeners&gt;</span></span>
<span data-ttu-id="a3012-103">Přidá naslouchací proces a `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="a3012-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="a3012-104">`sharedListeners`je to všechny kolekce naslouchacího procesu [ \<zdroje >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) nebo [ \<trasování >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) , můžete odkazovat.</span><span class="sxs-lookup"><span data-stu-id="a3012-104">`sharedListeners` is a collection of listeners that any [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) can reference.</span></span>  <span data-ttu-id="a3012-105">Ve výchozím nastavení, moduly pro naslouchání v `sharedListeners` kolekce nejsou uloženy do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="a3012-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="a3012-106">Je nutné je přidat název, který [ \<zdroje >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) nebo [ \<trasování >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span><span class="sxs-lookup"><span data-stu-id="a3012-106">They must be added by name to the [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span></span> <span data-ttu-id="a3012-107">Není možné získat posluchače v `sharedListeners` kolekce v kódu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a3012-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
 <span data-ttu-id="a3012-108">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="a3012-108">\<configuration></span></span>  
<span data-ttu-id="a3012-109">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="a3012-109">\<system.diagnostics></span></span>  
<span data-ttu-id="a3012-110">\<sharedListeners > elementu</span><span class="sxs-lookup"><span data-stu-id="a3012-110">\<sharedListeners> Element</span></span>  
<span data-ttu-id="a3012-111">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="a3012-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3012-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3012-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3012-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a3012-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a3012-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a3012-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3012-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="a3012-115">Attributes</span></span>  
  
|<span data-ttu-id="a3012-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="a3012-116">Attribute</span></span>|<span data-ttu-id="a3012-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a3012-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="a3012-118">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a3012-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="a3012-119">Určuje název naslouchací proces, který se používá k přidání sdílené naslouchacího procesu `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="a3012-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="a3012-120">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a3012-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="a3012-121">Určuje typ naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="a3012-121">Specifies the type of the listener.</span></span> <span data-ttu-id="a3012-122">Je nutné použít řetězec, který splňuje požadavky uvedené v [určení plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="a3012-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="a3012-123">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="a3012-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a3012-124">Řetězec předaný konstruktoru pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="a3012-124">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3012-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a3012-125">Child Elements</span></span>  
  
|<span data-ttu-id="a3012-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="a3012-126">Element</span></span>|<span data-ttu-id="a3012-127">Popis</span><span class="sxs-lookup"><span data-stu-id="a3012-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3012-128">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="a3012-128">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="a3012-129">Přidá filtr do naslouchací proces ve `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="a3012-129">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3012-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a3012-130">Parent Elements</span></span>  
  
|<span data-ttu-id="a3012-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="a3012-131">Element</span></span>|<span data-ttu-id="a3012-132">Popis</span><span class="sxs-lookup"><span data-stu-id="a3012-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a3012-133">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a3012-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a3012-134">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="a3012-134">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="a3012-135">Kolekce naslouchací procesy, které může odkazovat všechny zdroje nebo element trasování.</span><span class="sxs-lookup"><span data-stu-id="a3012-135">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3012-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3012-136">Remarks</span></span>  
 <span data-ttu-id="a3012-137">Naslouchací proces třídy součástí rozhraní .NET Framework odvozena od <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="a3012-137">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="a3012-138">Hodnota `name` atribut se používá k přidání sdílené naslouchacího procesu `Listeners` kolekce pro trasování nebo zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="a3012-138">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="a3012-139">Hodnota `initializeData` atribut závisí na typu naslouchacího procesu vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="a3012-139">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="a3012-140">Ne všechny trasování – moduly naslouchání vyžadují, aby `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="a3012-140">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3012-141">Při použití `initializeData` atributu, může získat kompilátoru upozornění "není deklarován atribut 'initializeData'."</span><span class="sxs-lookup"><span data-stu-id="a3012-141">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="a3012-142">Toto upozornění se zobrazí, protože nastavení konfigurace se ověřují vůči abstraktní základní třída <xref:System.Diagnostics.TraceListener>, který nebyl rozpoznán `initializeData` atribut.</span><span class="sxs-lookup"><span data-stu-id="a3012-142">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="a3012-143">Obvykle můžete toto upozornění pro implementace naslouchací proces trasování, které mají konstruktor, který přebírá parametr ignorovat.</span><span class="sxs-lookup"><span data-stu-id="a3012-143">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="a3012-144">Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí rozhraní .NET Framework a popisuje hodnotu jejich `initializeData` atributy.</span><span class="sxs-lookup"><span data-stu-id="a3012-144">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="a3012-145">Trasovací třída naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="a3012-145">Trace listener class</span></span>|<span data-ttu-id="a3012-146">Hodnota initializeData – atribut</span><span class="sxs-lookup"><span data-stu-id="a3012-146">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="a3012-147">`useErrorStream` Hodnota <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="a3012-147">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="a3012-148">Nastavte `initializeData` atribut "`true`"zápis trasování a ladění výstupu na standardní chybový proud; ji nastavte na"`false`" k zápisu do standardního výstupního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="a3012-148">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="a3012-149">Název souboru <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje do.</span><span class="sxs-lookup"><span data-stu-id="a3012-149">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a3012-150">Název existující zdroj protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="a3012-150">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a3012-151">Název souboru, který <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje do.</span><span class="sxs-lookup"><span data-stu-id="a3012-151">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="a3012-152">Název souboru, který <xref:System.Diagnostics.TextWriterTraceListener> zapisuje do.</span><span class="sxs-lookup"><span data-stu-id="a3012-152">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="a3012-153">Název souboru, který <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje do.</span><span class="sxs-lookup"><span data-stu-id="a3012-153">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="a3012-154">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="a3012-154">Configuration File</span></span>  
 <span data-ttu-id="a3012-155">Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="a3012-155">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3012-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3012-156">Example</span></span>  
 <span data-ttu-id="a3012-157">Následující příklad ukazuje, jak používat `<add>` elementy přidat <xref:System.Diagnostics.TextWriterTraceListener> `textListener` k `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="a3012-157">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="a3012-158">`textListener`název, který přidává `Listeners` kolekci pro zdroj trasování `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="a3012-158">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="a3012-159">`textListener` Naslouchací proces zapisuje do souboru myListener.log výstup trasování.</span><span class="sxs-lookup"><span data-stu-id="a3012-159">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3012-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3012-160">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="a3012-161">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="a3012-161">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="a3012-162">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="a3012-162">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
