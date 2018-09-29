---
title: '&lt;Přidat&gt; – Element pro &lt;naslouchacích procesů&gt; pro &lt;trasování&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
author: mcleblanc
ms.author: markl
ms.openlocfilehash: fd8ddf5daec4ab7e4de636a2f14cf413aedaa99a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/29/2018
ms.locfileid: "47455759"
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;Přidat&gt; – Element pro &lt;naslouchacích procesů&gt; pro &lt;trasování&gt;
Přidá naslouchací proces pro **naslouchacích procesů** kolekce.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<trasování >  
\<naslouchací procesy >  
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
|**Typ**|Požadovaný atribut.<br /><br /> Určuje typ naslouchací proces. Je nutné použít řetězec, který splňuje požadavky uvedené v [zadání plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|Nepovinný atribut.<br /><br /> Řetězec předaný konstruktoru pro zadanou třídu.|  
|**Jméno**|Nepovinný atribut.<br /><br /> Určuje název naslouchacího procesu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|Přidá filtr do naslouchacího procesu v `Listeners` kolekce pro trasování.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`listeners`|Určuje naslouchací proces, který shromažďuje, ukládá a provádí směrování zpráv. Posluchači přímý výstup trasování příslušný cíli.|  
|`system.diagnostics`|Určuje kořenový element části o konfiguraci technologie ASP.NET.|  
|`trace`|Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat trasovací zprávy.|  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> třídy sdílet stejný **naslouchacích procesů** kolekce. Pokud chcete přidat objekt naslouchacího procesu do kolekce v jednom z těchto tříd, jiná třída používá stejný naslouchací proces. Naslouchací proces třídy odvozovat z <xref:System.Diagnostics.TraceListener>.  
  
 Pokud nezadáte `name` atribut naslouchací proces trasování <xref:System.Diagnostics.TraceListener.Name%2A> výchozí naslouchací proces trasování na prázdný řetězec (""). Pokud vaše aplikace má pouze jeden naslouchací proces, můžete přidat bez zadání názvu a odebrat tak, že zadáte název prázdný řetězec. Nicméně pokud vaše aplikace má více než jeden naslouchací proces, měli byste určit jedinečné názvy pro každý naslouchací proces trasování, které umožňuje identifikovat a spravovat jednotlivé trasování naslouchacích procesů v rámci <xref:System.Diagnostics.Debug.Listeners%2A> a <xref:System.Diagnostics.Trace.Listeners%2A> kolekce.  
  
> [!NOTE]
>  Přidání více než jeden naslouchací proces trasování stejného typu a se stejnou pojmenujte výsledky v pouze jeden naslouchací daného typu a se přidávají do `Listeners` kolekce. Však můžete programově přidat několik identických naslouchacích procesů k `Listeners` kolekce.  
  
 Hodnota **initializeData** atributu závisí na typu naslouchacího procesu vytvoříte. Ne všechny moduly pro naslouchání trasování vyžadují, abyste určili **initializeData**.  
  
> [!NOTE]
>  Při použití `initializeData` atributu, může se zobrazit kompilátoru upozornění "není deklarovaný atribut"initializeData"." K tomuto upozornění dochází, protože nastavení konfigurace se ověří proti abstraktní základní třída <xref:System.Diagnostics.TraceListener>, které nebylo rozpoznáno `initializeData` atribut. Obvykle můžete ignorovat toto upozornění pro implementace naslouchací proces trasování, které mají konstruktor, který přijímá parametr.  
  
 Následující tabulka uvádí naslouchacích procesů trasování, které jsou součástí rozhraní .NET Framework a popisuje výhody jejich **initializeData** atributy.  
  
|Třída naslouchací proces trasování|Hodnota atributu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Hodnota <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktoru.  Nastavte `initializeData` atribut "`true`" zápis trasování a ladění výstupu do <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" k zápisu do <xref:System.Console.Out%2A?displayProperty=nameWithType>.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Název souboru <xref:System.Diagnostics.DelimitedListTraceListener> zapíše do.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Název název existující zdroj protokolu událostí.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Název souboru, který <xref:System.Diagnostics.EventSchemaTraceListener> zapíše do.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Název souboru, který <xref:System.Diagnostics.TextWriterTraceListener> zapíše do.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Název souboru, který <xref:System.Diagnostics.XmlWriterTraceListener> zapíše do.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat  **\<Přidat >** prvky pro přidání posluchače `MyListener` a `MyEventListener` k **naslouchacích procesů** kolekce. `MyListener` Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru. `MyEventListener` vytvoří záznam v protokolu událostí.  
  
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
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [Moduly naslouchání trasování](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
