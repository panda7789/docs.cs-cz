---
title: '&lt;Přidat&gt; – Element pro &lt;naslouchacích procesů&gt; pro &lt;zdroje&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 9e1bc2629b613b278ad38bbe9aab4cdfaa3f2a5e
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55084026"
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-ltsourcegt"></a>&lt;Přidat&gt; – Element pro &lt;naslouchacích procesů&gt; pro &lt;zdroje&gt;
Přidá naslouchací proces pro `Listeners` kolekci pro zdroj trasování.  
  
 \<Konfigurace >  
\<system.diagnostics>  
\<zdroje >  
\<zdroj >  
\<naslouchací procesy >  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`type`|Požadovaný atribut, pokud už odkazuje na naslouchací proces ve `sharedListeners` kolekce, ve kterém malá a velká je potřeba pouze na ni odkazovat podle názvu (viz [příklad](#example)).<br /><br /> Určuje typ naslouchací proces. Je nutné použít řetězec, který splňuje požadavky uvedené v [zadání plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Nepovinný atribut.<br /><br /> Řetězec předaný konstruktoru pro zadanou třídu. A <xref:System.Configuration.ConfigurationException> je vyvolána, pokud třída nemá konstruktor, který přijímá řetězec.|  
|`name`|Nepovinný atribut.<br /><br /> Určuje název naslouchacího procesu.|  
|`traceOutputOptions`|Nepovinný atribut.<br /><br /> Určuje, <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> hodnota vlastnosti pro posluchače trasování.|  
|[vlastní atributy]|Volitelné atributy.<br /><br /> Určuje hodnotu pro atributy specifické pro naslouchací proces identifikován <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> metody pro tuto naslouchací proces. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> je příkladem atribut navíc jedinečné pro <xref:System.Diagnostics.DelimitedListTraceListener> třídy.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Přidá filtr do naslouchacího procesu v `Listeners` kolekci pro zdroj trasování.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`sources`|Obsahuje zdrojů trasování, které se zahájí trasovací zprávy.|  
|`source`|Určuje zdroj trasování, který iniciuje trasovací zprávy.|  
|`listeners`|Určuje naslouchací procesy, které shromažďování, ukládání a směrovat zprávy.|  
  
## <a name="remarks"></a>Poznámky  
 Naslouchací proces třídy součástí rozhraní .NET Framework jsou odvozeny od <xref:System.Diagnostics.TraceListener> třídy.  
  
 Pokud nezadáte `name` atribut naslouchací proces trasování <xref:System.Diagnostics.TraceListener.Name%2A> vlastnost naslouchací služby stopy výchozí hodnota je prázdný řetězec (""). Pokud vaše aplikace má pouze jeden naslouchací proces, ho přidáte bez zadání názvu a můžete ho odebrat tak, že zadáte název prázdný řetězec. Ale, pokud aplikace obsahuje více než jeden naslouchací proces, měli byste určit jedinečný název pro každý naslouchací proces trasování, které umožňuje identifikovat a spravovat naslouchacích procesů jednotlivých trasování v <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> kolekce.  
  
> [!NOTE]
>  Přidání více než jeden naslouchací proces trasování stejného typu a se stejnou pojmenujte výsledky v pouze jeden naslouchací daného typu a se přidávají do `Listeners` kolekce. Však můžete programově přidat několik identických naslouchacích procesů k `Listeners` kolekce.  
  
 Hodnota `initializeData` atributu závisí na typu naslouchacího procesu vytvoříte. Ne všechny moduly pro naslouchání trasování vyžadují, abyste určili `initializeData`.  
  
> [!NOTE]
>  Při použití `initializeData` atributu, může se zobrazit kompilátoru upozornění "není deklarovaný atribut"initializeData"." K tomuto upozornění dochází, protože nastavení konfigurace se ověří proti abstraktní základní třída <xref:System.Diagnostics.TraceListener>, které nebylo rozpoznáno `initializeData` atribut. Obvykle můžete ignorovat toto upozornění pro implementace naslouchací proces trasování, které mají konstruktor, který přijímá parametr.  
  
 Následující tabulka uvádí naslouchacích procesů trasování, které jsou součástí rozhraní .NET Framework a popisuje výhody jejich `initializeData` atributy.  
  
|Třída naslouchací proces trasování|Hodnota atributu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Hodnota <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktoru.  Nastavte `initializeData` atribut "`true`"zápis trasování a ladění výstupu na standardní chybový proud; nastavte ho na"`false`" k zápisu do standardního výstupního datového proudu.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Název souboru <xref:System.Diagnostics.DelimitedListTraceListener> zapíše do.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Název existující zdroj protokolu událostí.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Název souboru, který <xref:System.Diagnostics.EventSchemaTraceListener> zapíše do.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Název souboru, který <xref:System.Diagnostics.TextWriterTraceListener> zapíše do.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Název souboru, který <xref:System.Diagnostics.XmlWriterTraceListener> zapíše do.|  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `<add>` prvky pro přidání posluchače `console` a `textListener` k `Listeners` kolekce pro zdroj trasování `TraceSourceApp`. `textListener` Naslouchacího procesu zapisuje do souboru myListener.log výstupu trasování.  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [Moduly naslouchání trasování](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
