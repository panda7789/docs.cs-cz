---
title: <add> – element pro element <listeners> pro element <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: 31ab58d6817c6c5064182ab5ef8b9595e92bef7d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260646"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="77474-102">\<Přidat > – Element pro \<naslouchacích procesů > pro \<trasování ></span><span class="sxs-lookup"><span data-stu-id="77474-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="77474-103">Přidá naslouchací proces pro **naslouchacích procesů** kolekce.</span><span class="sxs-lookup"><span data-stu-id="77474-103">Adds a listener to the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="77474-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="77474-104">\<configuration></span></span>  
<span data-ttu-id="77474-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="77474-105">\<system.diagnostics></span></span>  
<span data-ttu-id="77474-106">\<trasování ></span><span class="sxs-lookup"><span data-stu-id="77474-106">\<trace></span></span>  
<span data-ttu-id="77474-107">\<naslouchací procesy ></span><span class="sxs-lookup"><span data-stu-id="77474-107">\<listeners></span></span>  
<span data-ttu-id="77474-108">\<add></span><span class="sxs-lookup"><span data-stu-id="77474-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77474-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77474-109">Syntax</span></span>  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77474-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="77474-110">Attributes and Elements</span></span>  
 <span data-ttu-id="77474-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="77474-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77474-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="77474-112">Attributes</span></span>  
  
|<span data-ttu-id="77474-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="77474-113">Attribute</span></span>|<span data-ttu-id="77474-114">Popis</span><span class="sxs-lookup"><span data-stu-id="77474-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77474-115">**type**</span><span class="sxs-lookup"><span data-stu-id="77474-115">**type**</span></span>|<span data-ttu-id="77474-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="77474-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="77474-117">Určuje typ naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="77474-117">Specifies the type of the listener.</span></span> <span data-ttu-id="77474-118">Je nutné použít řetězec, který splňuje požadavky uvedené v [zadání plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="77474-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="77474-119">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="77474-119">**initializeData**</span></span>|<span data-ttu-id="77474-120">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="77474-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="77474-121">Řetězec předaný konstruktoru pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="77474-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="77474-122">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="77474-122">**name**</span></span>|<span data-ttu-id="77474-123">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="77474-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="77474-124">Určuje název naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="77474-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77474-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="77474-125">Child Elements</span></span>  
  
|<span data-ttu-id="77474-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="77474-126">Element</span></span>|<span data-ttu-id="77474-127">Popis</span><span class="sxs-lookup"><span data-stu-id="77474-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77474-128">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="77474-128">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="77474-129">Přidá filtr do naslouchacího procesu v `Listeners` kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="77474-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77474-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="77474-130">Parent Elements</span></span>  
  
|<span data-ttu-id="77474-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="77474-131">Element</span></span>|<span data-ttu-id="77474-132">Popis</span><span class="sxs-lookup"><span data-stu-id="77474-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="77474-133">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="77474-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="77474-134">Určuje naslouchací proces, který shromažďuje, ukládá a provádí směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="77474-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="77474-135">Posluchači přímý výstup trasování příslušný cíli.</span><span class="sxs-lookup"><span data-stu-id="77474-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="77474-136">Určuje kořenový element části o konfiguraci technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="77474-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="77474-137">Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="77474-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77474-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77474-138">Remarks</span></span>  
 <span data-ttu-id="77474-139"><xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> třídy sdílet stejný **naslouchacích procesů** kolekce.</span><span class="sxs-lookup"><span data-stu-id="77474-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="77474-140">Pokud chcete přidat objekt naslouchacího procesu do kolekce v jednom z těchto tříd, jiná třída používá stejný naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="77474-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="77474-141">Naslouchací proces třídy odvozovat z <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="77474-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="77474-142">Pokud nezadáte `name` atribut naslouchací proces trasování <xref:System.Diagnostics.TraceListener.Name%2A> výchozí naslouchací proces trasování na prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="77474-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="77474-143">Pokud vaše aplikace má pouze jeden naslouchací proces, můžete přidat bez zadání názvu a odebrat tak, že zadáte název prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="77474-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="77474-144">Nicméně pokud vaše aplikace má více než jeden naslouchací proces, měli byste určit jedinečné názvy pro každý naslouchací proces trasování, které umožňuje identifikovat a spravovat jednotlivé trasování naslouchacích procesů v rámci <xref:System.Diagnostics.Debug.Listeners%2A> a <xref:System.Diagnostics.Trace.Listeners%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="77474-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77474-145">Přidání více než jeden naslouchací proces trasování stejného typu a se stejnou pojmenujte výsledky v pouze jeden naslouchací daného typu a se přidávají do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="77474-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="77474-146">Však můžete programově přidat několik identických naslouchacích procesů k `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="77474-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="77474-147">Hodnota **initializeData** atributu závisí na typu naslouchacího procesu vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="77474-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="77474-148">Ne všechny moduly pro naslouchání trasování vyžadují, abyste určili **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="77474-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77474-149">Při použití `initializeData` atributu, může se zobrazit kompilátoru upozornění "není deklarovaný atribut"initializeData"."</span><span class="sxs-lookup"><span data-stu-id="77474-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="77474-150">K tomuto upozornění dochází, protože nastavení konfigurace se ověří proti abstraktní základní třída <xref:System.Diagnostics.TraceListener>, které nebylo rozpoznáno `initializeData` atribut.</span><span class="sxs-lookup"><span data-stu-id="77474-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="77474-151">Obvykle můžete ignorovat toto upozornění pro implementace naslouchací proces trasování, které mají konstruktor, který přijímá parametr.</span><span class="sxs-lookup"><span data-stu-id="77474-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="77474-152">Následující tabulka uvádí naslouchacích procesů trasování, které jsou součástí rozhraní .NET Framework a popisuje výhody jejich **initializeData** atributy.</span><span class="sxs-lookup"><span data-stu-id="77474-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="77474-153">Třída naslouchací proces trasování</span><span class="sxs-lookup"><span data-stu-id="77474-153">Trace listener class</span></span>|<span data-ttu-id="77474-154">Hodnota atributu initializeData</span><span class="sxs-lookup"><span data-stu-id="77474-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="77474-155">`useErrorStream` Hodnota <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="77474-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="77474-156">Nastavte `initializeData` atribut "`true`" zápis trasování a ladění výstupu do <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" k zápisu do <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="77474-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="77474-157">Název souboru <xref:System.Diagnostics.DelimitedListTraceListener> zapíše do.</span><span class="sxs-lookup"><span data-stu-id="77474-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="77474-158">Název název existující zdroj protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="77474-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="77474-159">Název souboru, který <xref:System.Diagnostics.EventSchemaTraceListener> zapíše do.</span><span class="sxs-lookup"><span data-stu-id="77474-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="77474-160">Název souboru, který <xref:System.Diagnostics.TextWriterTraceListener> zapíše do.</span><span class="sxs-lookup"><span data-stu-id="77474-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="77474-161">Název souboru, který <xref:System.Diagnostics.XmlWriterTraceListener> zapíše do.</span><span class="sxs-lookup"><span data-stu-id="77474-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="77474-162">Příklad</span><span class="sxs-lookup"><span data-stu-id="77474-162">Example</span></span>  
 <span data-ttu-id="77474-163">Následující příklad ukazuje, jak používat  **\<Přidat >** prvky pro přidání posluchače `MyListener` a `MyEventListener` k **naslouchacích procesů** kolekce.</span><span class="sxs-lookup"><span data-stu-id="77474-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="77474-164">`MyListener` Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="77474-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="77474-165">`MyEventListener` vytvoří záznam v protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="77474-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="77474-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77474-166">See also</span></span>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="77474-167">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="77474-167">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="77474-168">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="77474-168">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
