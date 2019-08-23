---
title: <add>Element pro <listeners> pro<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: d4ff919991ab1505b2845a225706d32cc1e57d0a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920572"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="425f1-102">\<Přidat > element pro \<naslouchací procesy > \<pro > trasování</span><span class="sxs-lookup"><span data-stu-id="425f1-102">\<add> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="425f1-103">Přidá naslouchací proces do kolekce **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="425f1-103">Adds a listener to the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="425f1-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="425f1-104">\<configuration></span></span>  
<span data-ttu-id="425f1-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="425f1-105">\<system.diagnostics></span></span>  
<span data-ttu-id="425f1-106">\<> trasování</span><span class="sxs-lookup"><span data-stu-id="425f1-106">\<trace></span></span>  
<span data-ttu-id="425f1-107">\<> naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="425f1-107">\<listeners></span></span>  
<span data-ttu-id="425f1-108">\<add></span><span class="sxs-lookup"><span data-stu-id="425f1-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="425f1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="425f1-109">Syntax</span></span>  
  
```xml  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="425f1-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="425f1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="425f1-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="425f1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="425f1-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="425f1-112">Attributes</span></span>  
  
|<span data-ttu-id="425f1-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="425f1-113">Attribute</span></span>|<span data-ttu-id="425f1-114">Popis</span><span class="sxs-lookup"><span data-stu-id="425f1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="425f1-115">**type**</span><span class="sxs-lookup"><span data-stu-id="425f1-115">**type**</span></span>|<span data-ttu-id="425f1-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="425f1-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="425f1-117">Určuje typ naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="425f1-117">Specifies the type of the listener.</span></span> <span data-ttu-id="425f1-118">Je nutné použít řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="425f1-118">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="425f1-119">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="425f1-119">**initializeData**</span></span>|<span data-ttu-id="425f1-120">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="425f1-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="425f1-121">Řetězec předaný konstruktoru pro určenou třídu.</span><span class="sxs-lookup"><span data-stu-id="425f1-121">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="425f1-122">**name**</span><span class="sxs-lookup"><span data-stu-id="425f1-122">**name**</span></span>|<span data-ttu-id="425f1-123">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="425f1-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="425f1-124">Určuje název naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="425f1-124">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="425f1-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="425f1-125">Child Elements</span></span>  
  
|<span data-ttu-id="425f1-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="425f1-126">Element</span></span>|<span data-ttu-id="425f1-127">Popis</span><span class="sxs-lookup"><span data-stu-id="425f1-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="425f1-128">\<Filtrovat ></span><span class="sxs-lookup"><span data-stu-id="425f1-128">\<filter></span></span>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="425f1-129">Přidá filtr pro naslouchací proces v `Listeners` kolekci pro trasování.</span><span class="sxs-lookup"><span data-stu-id="425f1-129">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="425f1-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="425f1-130">Parent Elements</span></span>  
  
|<span data-ttu-id="425f1-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="425f1-131">Element</span></span>|<span data-ttu-id="425f1-132">Popis</span><span class="sxs-lookup"><span data-stu-id="425f1-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="425f1-133">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="425f1-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="425f1-134">Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy.</span><span class="sxs-lookup"><span data-stu-id="425f1-134">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="425f1-135">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="425f1-135">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="425f1-136">Určuje kořenový element konfiguračního oddílu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="425f1-136">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="425f1-137">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="425f1-137">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="425f1-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="425f1-138">Remarks</span></span>  
 <span data-ttu-id="425f1-139">Třídy <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> sdílejí stejnou kolekci **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="425f1-139">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="425f1-140">Pokud přidáte objekt naslouchacího procesu do kolekce v jedné z těchto tříd, použije druhá třída stejný naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="425f1-140">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="425f1-141">Třídy naslouchacího procesu jsou odvozeny <xref:System.Diagnostics.TraceListener>z.</span><span class="sxs-lookup"><span data-stu-id="425f1-141">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="425f1-142">Pokud nezadáte `name` atribut naslouchacího procesu trasování, je <xref:System.Diagnostics.TraceListener.Name%2A> z naslouchacího procesu trasování ve výchozím nastavení prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="425f1-142">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="425f1-143">Pokud má vaše aplikace jenom jeden naslouchací proces, můžete ho přidat bez zadání názvu a odebrat ho zadáním prázdného řetězce pro název.</span><span class="sxs-lookup"><span data-stu-id="425f1-143">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="425f1-144">Pokud však má vaše aplikace více než jeden naslouchací proces, měli byste pro každé naslouchací proces trasování zadat jedinečné názvy, které vám umožní identifikovat a spravovat jednotlivé naslouchací procesy trasování v <xref:System.Diagnostics.Debug.Listeners%2A> rámci <xref:System.Diagnostics.Trace.Listeners%2A> kolekcí a.</span><span class="sxs-lookup"><span data-stu-id="425f1-144">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="425f1-145">Přidání více než jednoho naslouchacího procesu trasování stejného typu a se stejným názvem má za následek pouze jeden naslouchací proces pro daný typ a název přidaný do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="425f1-145">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="425f1-146">Můžete však programově přidat do `Listeners` kolekce více identických posluchačů.</span><span class="sxs-lookup"><span data-stu-id="425f1-146">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="425f1-147">Hodnota atributu **initializeData** závisí na typu naslouchacího procesu, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="425f1-147">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="425f1-148">Ne všechny naslouchací procesy trasování vyžadují, abyste zadali **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="425f1-148">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="425f1-149">Při použití `initializeData` atributu se může zobrazit upozornění kompilátoru "atribut ' initializeData ' není deklarován."</span><span class="sxs-lookup"><span data-stu-id="425f1-149">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="425f1-150">K tomuto upozornění dochází, protože nastavení konfigurace je ověřeno proti abstraktní základní <xref:System.Diagnostics.TraceListener>třídě, která `initializeData` atribut nerozpoznala.</span><span class="sxs-lookup"><span data-stu-id="425f1-150">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="425f1-151">Obvykle můžete toto upozornění ignorovat pro implementace naslouchacího procesu trasování, které mají konstruktor, který přebírá parametr.</span><span class="sxs-lookup"><span data-stu-id="425f1-151">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="425f1-152">Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí .NET Framework a popisuje hodnotu jejich atributů **initializeData** .</span><span class="sxs-lookup"><span data-stu-id="425f1-152">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="425f1-153">Trace – třída naslouchacího procesu</span><span class="sxs-lookup"><span data-stu-id="425f1-153">Trace listener class</span></span>|<span data-ttu-id="425f1-154">hodnota atributu initializeData</span><span class="sxs-lookup"><span data-stu-id="425f1-154">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="425f1-155">`useErrorStream` Hodnota<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> pro konstruktor</span><span class="sxs-lookup"><span data-stu-id="425f1-155">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="425f1-156">Nastavte atribut na "" pro zápis trasování a ladění výstupu do <xref:System.Console.Error%2A?displayProperty=nameWithType>;`true` `initializeData` "`false`" pro zápis do <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="425f1-156">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="425f1-157">Název souboru, do kterého se <xref:System.Diagnostics.DelimitedListTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="425f1-157">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="425f1-158">Název existujícího zdroje protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="425f1-158">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="425f1-159">Název souboru, do kterého se <xref:System.Diagnostics.EventSchemaTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="425f1-159">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="425f1-160">Název souboru, do kterého se <xref:System.Diagnostics.TextWriterTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="425f1-160">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="425f1-161">Název souboru, do kterého se <xref:System.Diagnostics.XmlWriterTraceListener> zapisují.</span><span class="sxs-lookup"><span data-stu-id="425f1-161">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="425f1-162">Příklad</span><span class="sxs-lookup"><span data-stu-id="425f1-162">Example</span></span>  
 <span data-ttu-id="425f1-163">Následující příklad ukazuje, jak použít `MyListener` `MyEventListener`  **\<prvky Add >** pro přidání posluchačů a do kolekce **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="425f1-163">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="425f1-164">`MyListener`Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru.</span><span class="sxs-lookup"><span data-stu-id="425f1-164">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="425f1-165">`MyEventListener`vytvoří položku v protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="425f1-165">`MyEventListener` creates an entry in the event log.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="425f1-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="425f1-166">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="425f1-167">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="425f1-167">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="425f1-168">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="425f1-168">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
