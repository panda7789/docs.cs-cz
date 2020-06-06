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
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153669"
---
# <a name="add-element-for-listeners-for-trace"></a>\<add>Element pro \<listeners> pro\<trace>
Přidá naslouchací proces do kolekce **posluchačů** .  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

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
|**typ**|Požadovaný atribut.<br /><br /> Určuje typ naslouchacího procesu. Je nutné použít řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|Nepovinný atribut.<br /><br /> Řetězec předaný konstruktoru pro určenou třídu.|  
|**Jméno**|Nepovinný atribut.<br /><br /> Určuje název naslouchacího procesu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|Přidá filtr pro naslouchací proces v `Listeners` kolekci pro trasování.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`listeners`|Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy. Naslouchací procesy směrují výstup trasování do příslušného cíle.|  
|`system.diagnostics`|Určuje kořenový element konfiguračního oddílu ASP.NET.|  
|`trace`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.|  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.Diagnostics.Debug>Třídy a <xref:System.Diagnostics.Trace> sdílejí stejnou kolekci **posluchačů** . Pokud přidáte objekt naslouchacího procesu do kolekce v jedné z těchto tříd, použije druhá třída stejný naslouchací proces. Třídy naslouchacího procesu jsou odvozeny z <xref:System.Diagnostics.TraceListener> .  
  
 Pokud nezadáte `name` atribut naslouchacího procesu trasování, je <xref:System.Diagnostics.TraceListener.Name%2A> z naslouchacího procesu trasování ve výchozím nastavení prázdný řetězec (""). Pokud má vaše aplikace jenom jeden naslouchací proces, můžete ho přidat bez zadání názvu a odebrat ho zadáním prázdného řetězce pro název. Pokud však má vaše aplikace více než jeden naslouchací proces, měli byste pro každé naslouchací proces trasování zadat jedinečné názvy, které vám umožní identifikovat a spravovat jednotlivé naslouchací procesy trasování v <xref:System.Diagnostics.Debug.Listeners%2A> rámci <xref:System.Diagnostics.Trace.Listeners%2A> kolekcí a.  
  
> [!NOTE]
> Přidání více než jednoho naslouchacího procesu trasování stejného typu a se stejným názvem má za následek pouze jeden naslouchací proces pro daný typ a název přidaný do `Listeners` kolekce. Můžete však programově přidat do kolekce více identických posluchačů `Listeners` .  
  
 Hodnota atributu **initializeData** závisí na typu naslouchacího procesu, který vytvoříte. Ne všechny naslouchací procesy trasování vyžadují, abyste zadali **initializeData**.  
  
> [!NOTE]
> Při použití atributu se `initializeData` může zobrazit upozornění kompilátoru "atribut ' initializeData ' není deklarován." K tomuto upozornění dochází, protože nastavení konfigurace je ověřeno proti abstraktní základní třídě <xref:System.Diagnostics.TraceListener> , která atribut nerozpoznala `initializeData` . Obvykle můžete toto upozornění ignorovat pro implementace naslouchacího procesu trasování, které mají konstruktor, který přebírá parametr.  
  
 Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí .NET Framework a popisuje hodnotu jejich atributů **initializeData** .  
  
|Trace – třída naslouchacího procesu|hodnota atributu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream`Hodnota pro <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktor  Nastavte `initializeData` atribut na " `true` " pro zápis trasování a ladění výstupu do <xref:System.Console.Error%2A?displayProperty=nameWithType> ; " `false` " pro zápis do <xref:System.Console.Out%2A?displayProperty=nameWithType> .|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Název souboru, do kterého se <xref:System.Diagnostics.DelimitedListTraceListener> zapisují.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Název existujícího zdroje protokolu událostí.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Název souboru, do kterého se <xref:System.Diagnostics.EventSchemaTraceListener> zapisují.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Název souboru, do kterého se <xref:System.Diagnostics.TextWriterTraceListener> zapisují.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Název souboru, do kterého se <xref:System.Diagnostics.XmlWriterTraceListener> zapisují.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít **\<add>** prvky pro přidání posluchačů `MyListener` a `MyEventListener` do kolekce **posluchačů** . `MyListener`Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru. `MyEventListener`vytvoří položku v protokolu událostí.  
  
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
