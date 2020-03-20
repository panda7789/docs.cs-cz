---
title: Element <add> pro <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: 5588892ec75a791eda1eb043936c0af95e79354e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153604"
---
# <a name="add-element-for-sharedlisteners"></a>\<přidat prvek \<> pro> sharedListeners
Přidá naslouchací proces do `sharedListeners` kolekce. `sharedListeners`je kolekce naslouchacích procesy, které všechny [ \<zdrojové>](source-element.md) nebo [ \<trasování>](trace-element.md) může odkazovat.  Ve výchozím nastavení naslouchací procesy v kolekci `sharedListeners` nejsou umístěny v kolekci. `Listeners` Musí být přidány názvem do [ \<zdrojového>](source-element.md) nebo [ \<trasování>](trace-element.md). Není možné získat naslouchací procesy v kolekci `sharedListeners` v kódu za běhu.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Požadovaný atribut.<br /><br /> Určuje název naslouchací proces, který se `Listeners` používá k přidání sdíleného naslouchací proces do kolekce.|  
|`type`|Požadovaný atribut.<br /><br /> Určuje typ naslouchacího procesu. Je nutné použít řetězec, který splňuje požadavky zadané v [poli Určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Nepovinný atribut.<br /><br /> Řetězec předán konstruktoru pro zadanou třídu.|  
|`traceOutputOptions`|Nepovinný atribut.<br/><br/>Řetězcová reprezentace jednoho <xref:System.Diagnostics.TraceOptions> nebo více členů výčtu, která označuje data, která mají být zapsána do výstupu trasování. Více položek je odděleno čárkami. Výchozí hodnota je "Žádný".|

### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>filtru](filter-element-for-add-for-sharedlisteners.md)|Přidá filtr do naslouchací proces v kolekci. `sharedListeners`|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.|  
|`sharedListeners`|Kolekce naslouchacích procesy, které může odkazovat libovolný zdroj nebo prvek trasování.|  
  
## <a name="remarks"></a>Poznámky  
 Třídy posluchače dodávané s rozhraním <xref:System.Diagnostics.TraceListener> .NET Framework jsou odvozeny z třídy. Hodnota atributu `name` se používá k přidání sdíleného naslouchací proces do `Listeners` kolekce pro trasování nebo zdroj trasování. Hodnota atributu `initializeData` závisí na typu naslouchacího procesu, který vytvoříte. Ne všechny naslouchací procesy trasování vyžadují, abyste zadali `initializeData`.  
  
> [!NOTE]
> Při použití `initializeData` atributu se může dostat upozornění kompilátoru "Atribut initializeData' není deklarován." K tomuto upozornění dochází, protože nastavení konfigurace <xref:System.Diagnostics.TraceListener>jsou ověřeny proti `initializeData` abstraktní základní třídy , která nerozpozná atribut. Obvykle můžete ignorovat toto upozornění pro implementace posluchače trasování, které mají konstruktor, který přebírá parametr.  
  
 V následující tabulce jsou uvedeny posluchače trasování, které jsou součástí `initializeData` rozhraní .NET Framework a popisuje hodnotu jejich atributů.  
  
|Třída posluchače trasování|hodnota atributu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|Hodnota `useErrorStream` pro <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktoru.  Nastavte `initializeData` atribut na`true`" " pro zápis výstupu trasování a ladění do standardního datového proudu chyb; nastavte jej`false`na " " pro zápis do standardního výstupního datového proudu.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Název souboru, <xref:System.Diagnostics.DelimitedListTraceListener> do který zapisuje.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Název existujícího zdroje protokolu událostí.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Název souboru, do <xref:System.Diagnostics.EventSchemaTraceListener> kterého zapisuje.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Název souboru, do <xref:System.Diagnostics.TextWriterTraceListener> kterého zapisuje.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Název souboru, do <xref:System.Diagnostics.XmlWriterTraceListener> kterého zapisuje.|  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento prvek lze použít v konfiguračním souboru počítače (Machine.config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, `<add>` jak použít <xref:System.Diagnostics.TextWriterTraceListener> `textListener` prvky `sharedListeners` přidat do kolekce.   `textListener`je přidán podle `Listeners` názvu do kolekce `TraceSourceApp`pro zdroj trasování . Naslouchací `textListener` proces zapíše výstup trasování do souboru myListener.log.  
  
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
