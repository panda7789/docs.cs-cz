---
title: <add>Prvek <listeners> pro pro<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153682"
---
# <a name="add-element-for-listeners-for-source"></a>\<přidat prvek \<> pro \<naslouchací procesy> pro zdrojový>
Přidá naslouchací proces do `Listeners` kolekce pro zdroj trasování.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdroje>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<zdrojové>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<posluchači>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**

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
|`type`|Povinný atribut, pokud odkazujete na naslouchací proces v `sharedListeners` kolekci, v takovém případě stačí odkazovat na něj podle názvu (viz [příklad).](#example)<br /><br /> Určuje typ naslouchacího procesu. Je nutné použít řetězec, který splňuje požadavky zadané v [poli Určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Nepovinný atribut.<br /><br /> Řetězec předán konstruktoru pro zadanou třídu. A <xref:System.Configuration.ConfigurationException> je vyvolána, pokud třída nemá konstruktor, který trvá řetězec.|  
|`name`|Nepovinný atribut.<br /><br /> Určuje název naslouchací proces.|  
|`traceOutputOptions`|Nepovinný atribut.<br /><br /> Určuje hodnotu vlastnosti <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> posluchače trasování.|  
|[vlastní atributy]|Volitelné atributy.<br /><br /> Určuje hodnotu atributů specifických pro <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> posluchače identifikovaných metodou pro daný naslouchací proces. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>je příkladem extra atribut jedinečný <xref:System.Diagnostics.DelimitedListTraceListener> pro třídu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>filtru](filter-element-for-add-for-listeners-for-source.md)|Přidá filtr do naslouchací proces v kolekci `Listeners` pro zdroj trasování.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.|  
|`sources`|Obsahuje zdroje trasování, které iniciují tracing zprávy.|  
|`source`|Určuje zdroj trasování, který iniciuje trasování zpráv.|  
|`listeners`|Určuje posluchače, kteří shromažďují, ukládají a směrují zprávy.|  
  
## <a name="remarks"></a>Poznámky  
 Třídy posluchače dodávané s rozhraním <xref:System.Diagnostics.TraceListener> .NET Framework jsou odvozeny z třídy.  
  
 Pokud nezadáte `name` atribut posluchače trasování, <xref:System.Diagnostics.TraceListener.Name%2A> vlastnost posluchače trasování výchozí prázdný řetězec (""). Pokud aplikace obsahuje pouze jeden naslouchací proces, můžete jej přidat bez zadání názvu a můžete jej odebrat zadáním prázdného řetězce pro název. Pokud však aplikace obsahuje více než jeden naslouchací proces, měli byste zadat jedinečný název <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> pro každý naslouchací proces trasování, který umožňuje identifikovat a spravovat jednotlivé posluchače trasování v kolekci.  
  
> [!NOTE]
> Přidání více než jeden naslouchací proces trasování stejného typu a se stejným `Listeners` názvem má za následek pouze jeden posluchač trasování tohoto typu a název, který je přidán do kolekce. Můžete však programově přidat více identických naslouchacích procesy do `Listeners` kolekce.  
  
 Hodnota atributu `initializeData` závisí na typu naslouchacího procesu, který vytvoříte. Ne všechny naslouchací procesy trasování vyžadují, abyste zadali `initializeData`.  
  
> [!NOTE]
> Při použití `initializeData` atributu se může dostat upozornění kompilátoru "Atribut initializeData' není deklarován." K tomuto upozornění dochází, protože nastavení konfigurace <xref:System.Diagnostics.TraceListener>jsou ověřeny proti `initializeData` abstraktní základní třídy , která nerozpozná atribut. Obvykle můžete ignorovat toto upozornění pro implementace posluchače trasování, které mají konstruktor, který přebírá parametr.  
  
 V následující tabulce jsou uvedeny posluchače trasování, které jsou součástí `initializeData` rozhraní .NET Framework a popisuje hodnotu jejich atributů.  
  
|Třída posluchače trasování|hodnota atributu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|Hodnota `useErrorStream` pro <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktoru.  Nastavte `initializeData` atribut na`true`" " pro zápis výstupu trasování a ladění do standardního datového proudu chyb; nastavte jej`false`na " " pro zápis do standardního výstupního datového proudu.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Název souboru, <xref:System.Diagnostics.DelimitedListTraceListener> do který zapisuje.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Název existujícího zdroje protokolu událostí.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Název souboru, do <xref:System.Diagnostics.EventSchemaTraceListener> kterého zapisuje.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Název souboru, do <xref:System.Diagnostics.TextWriterTraceListener> kterého zapisuje.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Název souboru, do <xref:System.Diagnostics.XmlWriterTraceListener> kterého zapisuje.|  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, `<add>` jak použít prvky `console` `textListener` přidat `Listeners` posluchače a `TraceSourceApp`do kolekce pro zdroj trasování . Naslouchací `textListener` proces zapíše výstup trasování do souboru myListener.log.  
  
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

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [Trasování a ladění schématu nastavení](index.md)
- [Moduly naslouchání trasování](../../../debug-trace-profile/trace-listeners.md)
