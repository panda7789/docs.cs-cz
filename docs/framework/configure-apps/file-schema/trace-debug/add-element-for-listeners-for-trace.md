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
# <a name="add-element-for-listeners-for-trace"></a>\<přidat> \<Element pro \<naslouchací> pro trasování>
Přidá naslouchací proces **listeners** kolekce.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trasovací>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<posluchači>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**Typ**|Požadovaný atribut.<br /><br /> Určuje typ naslouchacího procesu. Je nutné použít řetězec, který splňuje požadavky zadané v [poli Určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**inicializovatData**|Nepovinný atribut.<br /><br /> Řetězec předán konstruktoru pro zadanou třídu.|  
|**Jméno**|Nepovinný atribut.<br /><br /> Určuje název naslouchací proces.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>filtru](filter-element-for-add-for-listeners-for-trace.md)|Přidá filtr naslouchací proces v kolekci `Listeners` pro trasování.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`listeners`|Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy. Naslouchací procesy nasměrují výstup trasování na příslušný cíl.|  
|`system.diagnostics`|Určuje kořenový prvek oddílu konfigurace ASP.NET.|  
|`trace`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasování zpráv.|  
  
## <a name="remarks"></a>Poznámky  
 A <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> třídy sdílejí stejnou **kolekci Listeners.** Pokud přidáte objekt posluchače do kolekce v jedné z těchto tříd, druhá třída používá stejný naslouchací proces. Třídy posluchače <xref:System.Diagnostics.TraceListener>jsou odvozeny z .  
  
 Pokud nezadáte `name` atribut posluchače trasování, <xref:System.Diagnostics.TraceListener.Name%2A> naslouchací proces trasování výchozí prázdný řetězec (""). Pokud aplikace obsahuje pouze jeden naslouchací proces, můžete jej přidat bez zadání názvu a odebrat zadáním prázdného řetězce pro název. Pokud však aplikace obsahuje více než jeden naslouchací proces, měli byste zadat jedinečné názvy pro každý naslouchací proces trasování, který umožňuje identifikovat a spravovat jednotlivé posluchače trasování v rámci <xref:System.Diagnostics.Debug.Listeners%2A> a <xref:System.Diagnostics.Trace.Listeners%2A> kolekce.  
  
> [!NOTE]
> Přidání více než jeden naslouchací proces trasování stejného typu a se stejným `Listeners` názvem má za následek pouze jeden posluchač trasování tohoto typu a název, který je přidán do kolekce. Můžete však programově přidat více identických naslouchacích procesy do `Listeners` kolekce.  
  
 Hodnota atributu **initializeData** závisí na typu naslouchacího procesu, který vytvoříte. Ne všechny naslouchací procesy trasování vyžadují zadat **initializeData**.  
  
> [!NOTE]
> Při použití `initializeData` atributu se může dostat upozornění kompilátoru "Atribut initializeData' není deklarován." K tomuto upozornění dochází, protože nastavení konfigurace <xref:System.Diagnostics.TraceListener>jsou ověřeny proti `initializeData` abstraktní základní třídy , která nerozpozná atribut. Obvykle můžete ignorovat toto upozornění pro implementace posluchače trasování, které mají konstruktor, který přebírá parametr.  
  
 V následující tabulce jsou uvedeny posluchače trasování, které jsou součástí rozhraní .NET Framework a popisuje hodnotu jejich **atributů initializeData.**  
  
|Třída posluchače trasování|hodnota atributu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|Hodnota `useErrorStream` pro <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktoru.  Nastavte `initializeData` atribut na`true`" " pro zápis <xref:System.Console.Error%2A?displayProperty=nameWithType>stopování a ladění výstupu ; "`false`" pro <xref:System.Console.Out%2A?displayProperty=nameWithType>zápis do .|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Název souboru, <xref:System.Diagnostics.DelimitedListTraceListener> do který zapisuje.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Název názvu existujícího zdroje protokolu událostí.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Název souboru, do <xref:System.Diagnostics.EventSchemaTraceListener> kterého zapisuje.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Název souboru, do <xref:System.Diagnostics.TextWriterTraceListener> kterého zapisuje.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Název souboru, do <xref:System.Diagnostics.XmlWriterTraceListener> kterého zapisuje.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, ** \<** jak použít přidat>`MyListener` prvky přidat posluchače a `MyEventListener` **listeners** kolekce. `MyListener`vytvoří soubor `MyListener.log` s názvem a zapíše výstup do souboru. `MyEventListener`vytvoří položku v protokolu událostí.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [Trasování a ladění schématu nastavení](index.md)
- [Moduly naslouchání trasování](../../../debug-trace-profile/trace-listeners.md)
