---
title: <add>Prvek <listeners> pro pro<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153669"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="034b5-102">\<přidat> \<Element pro \<naslouchací> pro trasování></span><span class="sxs-lookup"><span data-stu-id="034b5-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="034b5-103">Přidá naslouchací proces **listeners** kolekce.</span><span class="sxs-lookup"><span data-stu-id="034b5-103">Adds a listener to the **Listeners** collection.</span></span>  

<span data-ttu-id="034b5-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="034b5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="034b5-105">&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="034b5-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="034b5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trasovací>**](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="034b5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="034b5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<posluchači>**](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="034b5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="034b5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**</span><span class="sxs-lookup"><span data-stu-id="034b5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="034b5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="034b5-109">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="034b5-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="034b5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="034b5-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="034b5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="034b5-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="034b5-112">Attributes</span></span>  
  
|<span data-ttu-id="034b5-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="034b5-113">Attribute</span></span>|<span data-ttu-id="034b5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="034b5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="034b5-115">**Typ**</span><span class="sxs-lookup"><span data-stu-id="034b5-115">**type**</span></span>|<span data-ttu-id="034b5-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="034b5-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="034b5-117">Určuje typ naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="034b5-117">Specifies the type of the listener.</span></span> <span data-ttu-id="034b5-118">Je nutné použít řetězec, který splňuje požadavky zadané v [poli Určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="034b5-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="034b5-119">**inicializovatData**</span><span class="sxs-lookup"><span data-stu-id="034b5-119">**initializeData**</span></span>|<span data-ttu-id="034b5-120">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="034b5-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="034b5-121">Řetězec předán konstruktoru pro zadanou třídu.</span><span class="sxs-lookup"><span data-stu-id="034b5-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="034b5-122">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="034b5-122">**name**</span></span>|<span data-ttu-id="034b5-123">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="034b5-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="034b5-124">Určuje název naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="034b5-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="034b5-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="034b5-125">Child Elements</span></span>  
  
|<span data-ttu-id="034b5-126">Element</span><span class="sxs-lookup"><span data-stu-id="034b5-126">Element</span></span>|<span data-ttu-id="034b5-127">Popis</span><span class="sxs-lookup"><span data-stu-id="034b5-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="034b5-128">\<>filtru</span><span class="sxs-lookup"><span data-stu-id="034b5-128">\<filter></span></span>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="034b5-129">Přidá filtr naslouchací proces v kolekci `Listeners` pro trasování.</span><span class="sxs-lookup"><span data-stu-id="034b5-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="034b5-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="034b5-130">Parent Elements</span></span>  
  
|<span data-ttu-id="034b5-131">Element</span><span class="sxs-lookup"><span data-stu-id="034b5-131">Element</span></span>|<span data-ttu-id="034b5-132">Popis</span><span class="sxs-lookup"><span data-stu-id="034b5-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="034b5-133">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="034b5-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="034b5-134">Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy.</span><span class="sxs-lookup"><span data-stu-id="034b5-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="034b5-135">Naslouchací procesy nasměrují výstup trasování na příslušný cíl.</span><span class="sxs-lookup"><span data-stu-id="034b5-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="034b5-136">Určuje kořenový prvek oddílu konfigurace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="034b5-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="034b5-137">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="034b5-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="034b5-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="034b5-138">Remarks</span></span>  
 <span data-ttu-id="034b5-139">A <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> třídy sdílejí stejnou **kolekci Listeners.**</span><span class="sxs-lookup"><span data-stu-id="034b5-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="034b5-140">Pokud přidáte objekt posluchače do kolekce v jedné z těchto tříd, druhá třída používá stejný naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="034b5-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="034b5-141">Třídy posluchače <xref:System.Diagnostics.TraceListener>jsou odvozeny z .</span><span class="sxs-lookup"><span data-stu-id="034b5-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="034b5-142">Pokud nezadáte `name` atribut posluchače trasování, <xref:System.Diagnostics.TraceListener.Name%2A> naslouchací proces trasování výchozí prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="034b5-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="034b5-143">Pokud aplikace obsahuje pouze jeden naslouchací proces, můžete jej přidat bez zadání názvu a odebrat zadáním prázdného řetězce pro název.</span><span class="sxs-lookup"><span data-stu-id="034b5-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="034b5-144">Pokud však aplikace obsahuje více než jeden naslouchací proces, měli byste zadat jedinečné názvy pro každý naslouchací proces trasování, který umožňuje identifikovat a spravovat jednotlivé posluchače trasování v rámci <xref:System.Diagnostics.Debug.Listeners%2A> a <xref:System.Diagnostics.Trace.Listeners%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="034b5-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="034b5-145">Přidání více než jeden naslouchací proces trasování stejného typu a se stejným `Listeners` názvem má za následek pouze jeden posluchač trasování tohoto typu a název, který je přidán do kolekce.</span><span class="sxs-lookup"><span data-stu-id="034b5-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="034b5-146">Můžete však programově přidat více identických naslouchacích procesy do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="034b5-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="034b5-147">Hodnota atributu **initializeData** závisí na typu naslouchacího procesu, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="034b5-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="034b5-148">Ne všechny naslouchací procesy trasování vyžadují zadat **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="034b5-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="034b5-149">Při použití `initializeData` atributu se může dostat upozornění kompilátoru "Atribut initializeData' není deklarován."</span><span class="sxs-lookup"><span data-stu-id="034b5-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="034b5-150">K tomuto upozornění dochází, protože nastavení konfigurace <xref:System.Diagnostics.TraceListener>jsou ověřeny proti `initializeData` abstraktní základní třídy , která nerozpozná atribut.</span><span class="sxs-lookup"><span data-stu-id="034b5-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="034b5-151">Obvykle můžete ignorovat toto upozornění pro implementace posluchače trasování, které mají konstruktor, který přebírá parametr.</span><span class="sxs-lookup"><span data-stu-id="034b5-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="034b5-152">V následující tabulce jsou uvedeny posluchače trasování, které jsou součástí rozhraní .NET Framework a popisuje hodnotu jejich **atributů initializeData.**</span><span class="sxs-lookup"><span data-stu-id="034b5-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="034b5-153">Třída posluchače trasování</span><span class="sxs-lookup"><span data-stu-id="034b5-153">Trace listener class</span></span>|<span data-ttu-id="034b5-154">hodnota atributu initializeData</span><span class="sxs-lookup"><span data-stu-id="034b5-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="034b5-155">Hodnota `useErrorStream` pro <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="034b5-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="034b5-156">Nastavte `initializeData` atribut na`true`" " pro zápis <xref:System.Console.Error%2A?displayProperty=nameWithType>stopování a ladění výstupu ; "`false`" pro <xref:System.Console.Out%2A?displayProperty=nameWithType>zápis do .</span><span class="sxs-lookup"><span data-stu-id="034b5-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="034b5-157">Název souboru, <xref:System.Diagnostics.DelimitedListTraceListener> do který zapisuje.</span><span class="sxs-lookup"><span data-stu-id="034b5-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="034b5-158">Název názvu existujícího zdroje protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="034b5-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="034b5-159">Název souboru, do <xref:System.Diagnostics.EventSchemaTraceListener> kterého zapisuje.</span><span class="sxs-lookup"><span data-stu-id="034b5-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="034b5-160">Název souboru, do <xref:System.Diagnostics.TextWriterTraceListener> kterého zapisuje.</span><span class="sxs-lookup"><span data-stu-id="034b5-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="034b5-161">Název souboru, do <xref:System.Diagnostics.XmlWriterTraceListener> kterého zapisuje.</span><span class="sxs-lookup"><span data-stu-id="034b5-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="034b5-162">Příklad</span><span class="sxs-lookup"><span data-stu-id="034b5-162">Example</span></span>  
 <span data-ttu-id="034b5-163">Následující příklad ukazuje, \*\* \<\*\* jak použít přidat>`MyListener` prvky přidat posluchače a `MyEventListener` **listeners** kolekce.</span><span class="sxs-lookup"><span data-stu-id="034b5-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="034b5-164">`MyListener`vytvoří soubor `MyListener.log` s názvem a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="034b5-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="034b5-165">`MyEventListener`vytvoří položku v protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="034b5-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="034b5-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="034b5-166">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="034b5-167">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="034b5-167">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="034b5-168">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="034b5-168">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
