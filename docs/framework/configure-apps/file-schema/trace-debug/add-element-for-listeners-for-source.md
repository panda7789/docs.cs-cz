---
title: '&lt;Přidat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;zdroje&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ba8ff652003a9167ec370643797ac9300b83889a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-ltsourcegt"></a>&lt;Přidat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;zdroje&gt;
Přidá naslouchací proces a `Listeners` kolekce zdroje trasování.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<zdroje >  
\<zdroj >  
\<moduly pro naslouchání >  
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
|`type`|Atribut je povinný, pokud jste odkazující na naslouchací proces ve `sharedListeners` kolekce, ve kterém případ, je potřeba pouze na ni odkazuje podle názvu (najdete v článku [příklad](#example)).<br /><br /> Určuje typ naslouchacího procesu. Je nutné použít řetězec, který splňuje požadavky uvedené v [určení plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Nepovinný atribut.<br /><br /> Řetězec předaný konstruktoru pro zadanou třídu. A <xref:System.Configuration.ConfigurationException> je vyvolána, pokud třída nemá konstruktor, který přebírá řetězec.|  
|`name`|Nepovinný atribut.<br /><br /> Určuje název naslouchacího procesu.|  
|`traceOutputOptions`|Nepovinný atribut.<br /><br /> Určuje, <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> hodnota vlastnosti pro naslouchací proces trasování.|  
|[vlastní atributy]|Volitelných atributů.<br /><br /> Určuje hodnotu atributy specifické pro naslouchací proces identifikovaný <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> metoda pro tento naslouchací proces. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> Navíc atributu je jedinečná <xref:System.Diagnostics.DelimitedListTraceListener> třídy.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Přidá filtr do naslouchací proces ve `Listeners` kolekce zdroje trasování.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.|  
|`sources`|Obsahuje trasování zdrojů, které zahájí trasování zpráv.|  
|`source`|Určuje zdroj trasování, který iniciuje trasování zpráv.|  
|`listeners`|Určuje naslouchací procesy, které shromažďování, ukládání a směrování zpráv.|  
  
## <a name="remarks"></a>Poznámky  
 Naslouchací proces třídy součástí rozhraní .NET Framework odvozena od <xref:System.Diagnostics.TraceListener> třídy.  
  
 Pokud nezadáte `name` atribut naslouchací proces trasování, <xref:System.Diagnostics.TraceListener.Name%2A> vlastnost naslouchací proces trasování výchozí nastavení je prázdný řetězec (""). Pokud vaše aplikace má pouze jeden naslouchací proces, můžete jej přidat bez určení názvu a můžete jej odebrat zadáním prázdný řetězec pro název. Ale, pokud aplikace obsahuje více než jeden naslouchací proces, měli byste určit jedinečný název pro každý naslouchací proces trasování, které umožňuje identifikovat a spravovat jednotlivé trasování – moduly naslouchání v <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> kolekce.  
  
> [!NOTE]
>  Přidání více než jeden naslouchací proces trasování stejného typu a se stejným názvem výsledkem pouze jeden naslouchací daného typu a název, který se přidává do `Listeners` kolekce. Však můžete prostřednictvím kódu programu přidat více identické moduly pro naslouchání na `Listeners` kolekce.  
  
 Hodnota `initializeData` atribut závisí na typu naslouchacího procesu vytvoříte. Ne všechny trasování – moduly naslouchání vyžadují, aby `initializeData`.  
  
> [!NOTE]
>  Při použití `initializeData` atributu, může získat kompilátoru upozornění "není deklarován atribut 'initializeData'." Toto upozornění se zobrazí, protože nastavení konfigurace se ověřují vůči abstraktní základní třída <xref:System.Diagnostics.TraceListener>, který nebyl rozpoznán `initializeData` atribut. Obvykle můžete toto upozornění pro implementace naslouchací proces trasování, které mají konstruktor, který přebírá parametr ignorovat.  
  
 Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí rozhraní .NET Framework a popisuje hodnotu jejich `initializeData` atributy.  
  
|Trasovací třída naslouchací proces|Hodnota initializeData – atribut|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|`useErrorStream` Hodnota <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktor.  Nastavte `initializeData` atribut "`true`"zápis trasování a ladění výstupu na standardní chybový proud; ji nastavte na"`false`" k zápisu do standardního výstupního datového proudu.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Název souboru <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje do.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Název existující zdroj protokolu událostí.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Název souboru, který <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje do.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Název souboru, který <xref:System.Diagnostics.TextWriterTraceListener> zapisuje do.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Název souboru, který <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje do.|  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `<add>` elementy přidat posluchače `console` a `textListener` k `Listeners` kolekci pro zdroj trasování `TraceSourceApp`. `textListener` Naslouchací proces zapisuje do souboru myListener.log výstup trasování.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [Moduly naslouchání trasování](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
