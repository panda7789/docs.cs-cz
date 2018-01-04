---
title: "&lt;Přidat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;trasování&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
caps.latest.revision: "24"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: eb624052c3638cb49abe143ebd4173a5ee85a054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="b363f-102">&lt;Přidat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;trasování&gt;</span><span class="sxs-lookup"><span data-stu-id="b363f-102">&lt;add&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="b363f-103">Přidá naslouchací proces a **naslouchací procesy** kolekce.</span><span class="sxs-lookup"><span data-stu-id="b363f-103">Adds a listener to the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="b363f-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="b363f-104">\<configuration></span></span>  
<span data-ttu-id="b363f-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="b363f-105">\<system.diagnostics></span></span>  
<span data-ttu-id="b363f-106">\<trasování ></span><span class="sxs-lookup"><span data-stu-id="b363f-106">\<trace></span></span>  
<span data-ttu-id="b363f-107">\<moduly pro naslouchání ></span><span class="sxs-lookup"><span data-stu-id="b363f-107">\<listeners></span></span>  
<span data-ttu-id="b363f-108">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="b363f-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b363f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b363f-109">Syntax</span></span>  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b363f-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b363f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b363f-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b363f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b363f-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="b363f-112">Attributes</span></span>  
  
|<span data-ttu-id="b363f-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="b363f-113">Attribute</span></span>|<span data-ttu-id="b363f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b363f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b363f-115">**Typ**</span><span class="sxs-lookup"><span data-stu-id="b363f-115">**type**</span></span>|<span data-ttu-id="b363f-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b363f-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="b363f-117">Určuje typ naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="b363f-117">Specifies the type of the listener.</span></span> <span data-ttu-id="b363f-118">Je nutné použít řetězec, který splňuje požadavky uvedené v [určení plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="b363f-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="b363f-119">**initializeData –**</span><span class="sxs-lookup"><span data-stu-id="b363f-119">**initializeData**</span></span>|<span data-ttu-id="b363f-120">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b363f-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b363f-121">Řetězec předaný konstruktoru pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="b363f-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="b363f-122">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="b363f-122">**name**</span></span>|<span data-ttu-id="b363f-123">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b363f-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b363f-124">Určuje název naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="b363f-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b363f-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b363f-125">Child Elements</span></span>  
  
|<span data-ttu-id="b363f-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="b363f-126">Element</span></span>|<span data-ttu-id="b363f-127">Popis</span><span class="sxs-lookup"><span data-stu-id="b363f-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b363f-128">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="b363f-128">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="b363f-129">Přidá filtr do naslouchací proces ve `Listeners` kolekci pro trasování.</span><span class="sxs-lookup"><span data-stu-id="b363f-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b363f-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b363f-130">Parent Elements</span></span>  
  
|<span data-ttu-id="b363f-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="b363f-131">Element</span></span>|<span data-ttu-id="b363f-132">Popis</span><span class="sxs-lookup"><span data-stu-id="b363f-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b363f-133">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b363f-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="b363f-134">Určuje naslouchací proces, který shromažďuje, úložiště a směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="b363f-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="b363f-135">Moduly pro naslouchání přesměrujte výstup trasování do příslušné cílové.</span><span class="sxs-lookup"><span data-stu-id="b363f-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b363f-136">Určuje kořenový element pro konfigurační oddíl technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b363f-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="b363f-137">Obsahuje naslouchací procesy, které shromažďování, ukládání a směrovat trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="b363f-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b363f-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b363f-138">Remarks</span></span>  
 <span data-ttu-id="b363f-139"><xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> třídy sdílet stejný **naslouchací procesy** kolekce.</span><span class="sxs-lookup"><span data-stu-id="b363f-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="b363f-140">Pokud přidáte objekt naslouchací proces ke kolekci v jedné z těchto tříd, používá jiná třída stejný naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="b363f-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="b363f-141">Naslouchací proces třídy jsou odvozeny od <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="b363f-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="b363f-142">Pokud nezadáte `name` atribut naslouchací proces trasování, <xref:System.Diagnostics.TraceListener.Name%2A> výchozích nastavení naslouchací proces trasování na prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="b363f-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="b363f-143">Pokud vaše aplikace má pouze jeden naslouchací proces, můžete ho přidat bez určení názvu a odebrat tak, že zadáte řetězec prázdný název.</span><span class="sxs-lookup"><span data-stu-id="b363f-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="b363f-144">Ale pokud aplikace obsahuje více než jeden naslouchací proces, měli byste určit jedinečné názvy pro každý naslouchací proces trasování, které umožňuje identifikovat a spravovat jednotlivé trasování – moduly naslouchání v rámci <xref:System.Diagnostics.Debug.Listeners%2A> a <xref:System.Diagnostics.Trace.Listeners%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="b363f-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b363f-145">Přidání více než jeden naslouchací proces trasování stejného typu a se stejným názvem výsledkem pouze jeden naslouchací daného typu a název, který se přidává do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="b363f-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="b363f-146">Však můžete prostřednictvím kódu programu přidat více identické moduly pro naslouchání na `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="b363f-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="b363f-147">Hodnota **initializeData** atribut závisí na typu naslouchacího procesu vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="b363f-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="b363f-148">Ne všechny trasování – moduly naslouchání vyžadují, aby **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="b363f-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b363f-149">Při použití `initializeData` atributu, může získat kompilátoru upozornění "není deklarován atribut 'initializeData'."</span><span class="sxs-lookup"><span data-stu-id="b363f-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="b363f-150">Toto upozornění se zobrazí, protože nastavení konfigurace se ověřují vůči abstraktní základní třída <xref:System.Diagnostics.TraceListener>, který nebyl rozpoznán `initializeData` atribut.</span><span class="sxs-lookup"><span data-stu-id="b363f-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="b363f-151">Obvykle můžete toto upozornění pro implementace naslouchací proces trasování, které mají konstruktor, který přebírá parametr ignorovat.</span><span class="sxs-lookup"><span data-stu-id="b363f-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="b363f-152">Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí rozhraní .NET Framework a popisuje hodnotu jejich **initializeData** atributy.</span><span class="sxs-lookup"><span data-stu-id="b363f-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="b363f-153">Trasovací třída naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="b363f-153">Trace listener class</span></span>|<span data-ttu-id="b363f-154">Hodnota initializeData – atribut</span><span class="sxs-lookup"><span data-stu-id="b363f-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="b363f-155">`useErrorStream` Hodnota <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="b363f-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="b363f-156">Nastavte `initializeData` atribut "`true`" zápis trasování a ladění výstupu k <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" k zápisu do <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b363f-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="b363f-157">Název souboru <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje do.</span><span class="sxs-lookup"><span data-stu-id="b363f-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="b363f-158">Název název existující zdroj protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="b363f-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="b363f-159">Název souboru, který <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje do.</span><span class="sxs-lookup"><span data-stu-id="b363f-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="b363f-160">Název souboru, který <xref:System.Diagnostics.TextWriterTraceListener> zapisuje do.</span><span class="sxs-lookup"><span data-stu-id="b363f-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="b363f-161">Název souboru, který <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje do.</span><span class="sxs-lookup"><span data-stu-id="b363f-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b363f-162">Příklad</span><span class="sxs-lookup"><span data-stu-id="b363f-162">Example</span></span>  
 <span data-ttu-id="b363f-163">Následující příklad ukazuje, jak používat  **\<Přidat >** elementy přidat posluchače `MyListener` a `MyEventListener` k **naslouchací procesy** kolekce.</span><span class="sxs-lookup"><span data-stu-id="b363f-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="b363f-164">`MyListener`Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="b363f-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="b363f-165">`MyEventListener`vytvoří záznam v protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="b363f-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b363f-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="b363f-166">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 [<span data-ttu-id="b363f-167">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="b363f-167">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="b363f-168">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="b363f-168">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
