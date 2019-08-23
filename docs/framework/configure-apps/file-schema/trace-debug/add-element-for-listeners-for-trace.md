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
# <a name="add-element-for-listeners-for-trace"></a>\<Přidat > element pro \<naslouchací procesy > \<pro > trasování
Přidá naslouchací proces do kolekce **posluchačů** .  
  
 \<> Konfigurace  
\<system.diagnostics>  
\<> trasování  
\<> naslouchací proces  
\<add>  
  
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
|**type**|Požadovaný atribut.<br /><br /> Určuje typ naslouchacího procesu. Je nutné použít řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|Nepovinný atribut.<br /><br /> Řetězec předaný konstruktoru pro určenou třídu.|  
|**name**|Nepovinný atribut.<br /><br /> Určuje název naslouchacího procesu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Filtrovat >](filter-element-for-add-for-listeners-for-trace.md)|Přidá filtr pro naslouchací proces v `Listeners` kolekci pro trasování.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`listeners`|Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy. Naslouchací procesy směrují výstup trasování do příslušného cíle.|  
|`system.diagnostics`|Určuje kořenový element konfiguračního oddílu ASP.NET.|  
|`trace`|Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.|  
  
## <a name="remarks"></a>Poznámky  
 Třídy <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> sdílejí stejnou kolekci **posluchačů** . Pokud přidáte objekt naslouchacího procesu do kolekce v jedné z těchto tříd, použije druhá třída stejný naslouchací proces. Třídy naslouchacího procesu jsou odvozeny <xref:System.Diagnostics.TraceListener>z.  
  
 Pokud nezadáte `name` atribut naslouchacího procesu trasování, je <xref:System.Diagnostics.TraceListener.Name%2A> z naslouchacího procesu trasování ve výchozím nastavení prázdný řetězec (""). Pokud má vaše aplikace jenom jeden naslouchací proces, můžete ho přidat bez zadání názvu a odebrat ho zadáním prázdného řetězce pro název. Pokud však má vaše aplikace více než jeden naslouchací proces, měli byste pro každé naslouchací proces trasování zadat jedinečné názvy, které vám umožní identifikovat a spravovat jednotlivé naslouchací procesy trasování v <xref:System.Diagnostics.Debug.Listeners%2A> rámci <xref:System.Diagnostics.Trace.Listeners%2A> kolekcí a.  
  
> [!NOTE]
> Přidání více než jednoho naslouchacího procesu trasování stejného typu a se stejným názvem má za následek pouze jeden naslouchací proces pro daný typ a název přidaný do `Listeners` kolekce. Můžete však programově přidat do `Listeners` kolekce více identických posluchačů.  
  
 Hodnota atributu **initializeData** závisí na typu naslouchacího procesu, který vytvoříte. Ne všechny naslouchací procesy trasování vyžadují, abyste zadali **initializeData**.  
  
> [!NOTE]
> Při použití `initializeData` atributu se může zobrazit upozornění kompilátoru "atribut ' initializeData ' není deklarován." K tomuto upozornění dochází, protože nastavení konfigurace je ověřeno proti abstraktní základní <xref:System.Diagnostics.TraceListener>třídě, která `initializeData` atribut nerozpoznala. Obvykle můžete toto upozornění ignorovat pro implementace naslouchacího procesu trasování, které mají konstruktor, který přebírá parametr.  
  
 Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí .NET Framework a popisuje hodnotu jejich atributů **initializeData** .  
  
|Trace – třída naslouchacího procesu|hodnota atributu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Hodnota<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> pro konstruktor  Nastavte atribut na "" pro zápis trasování a ladění výstupu do <xref:System.Console.Error%2A?displayProperty=nameWithType>;`true` `initializeData` "`false`" pro zápis do <xref:System.Console.Out%2A?displayProperty=nameWithType>.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Název souboru, do kterého se <xref:System.Diagnostics.DelimitedListTraceListener> zapisují.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Název existujícího zdroje protokolu událostí.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Název souboru, do kterého se <xref:System.Diagnostics.EventSchemaTraceListener> zapisují.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Název souboru, do kterého se <xref:System.Diagnostics.TextWriterTraceListener> zapisují.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Název souboru, do kterého se <xref:System.Diagnostics.XmlWriterTraceListener> zapisují.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `MyListener` `MyEventListener`  **\<prvky Add >** pro přidání posluchačů a do kolekce **posluchačů** . `MyListener`Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru. `MyEventListener`vytvoří položku v protokolu událostí.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [Trasování a ladění schématu nastavení](index.md)
- [Moduly naslouchání trasování](../../../debug-trace-profile/trace-listeners.md)
