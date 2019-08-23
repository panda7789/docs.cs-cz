---
title: <add> – element pro <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: c4b83834fb7aaf64a696b85bd2c8da47cfba2397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927216"
---
# <a name="add-element-for-sharedlisteners"></a>\<Přidat > element pro \<sharedListeners >
Přidá naslouchací proces do `sharedListeners` kolekce. `sharedListeners`je kolekce posluchačů, které mohou odkazovat všechny [ \<zdrojové >](source-element.md) nebo [ \<> trasování](trace-element.md) .  Ve výchozím nastavení nejsou naslouchací procesy `sharedListeners` v kolekci umístěny `Listeners` do kolekce. Musí být přidány podle názvu do [ \<zdrojového >](source-element.md) nebo [ \<> trasování](trace-element.md). Není možné získat naslouchací procesy v `sharedListeners` kolekci v kódu v době běhu.  
  
 \<> Konfigurace  
&nbsp;&nbsp;\<> System. Diagnostics  
&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners – > element  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<Přidat >  
  
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
|`name`|Požadovaný atribut.<br /><br /> Určuje název naslouchacího procesu, který se používá k přidání sdíleného naslouchacího procesu do `Listeners` kolekce.|  
|`type`|Požadovaný atribut.<br /><br /> Určuje typ naslouchacího procesu. Je nutné použít řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Nepovinný atribut.<br /><br /> Řetězec předaný konstruktoru pro určenou třídu.|  
|`traceOutputOptions`|Nepovinný atribut.<br/><br/>Řetězcové vyjádření jednoho nebo více <xref:System.Diagnostics.TraceOptions> členů výčtu, které označují data, která mají být zapsána do výstupu trasování. Více položek je odděleno čárkami. Výchozí hodnota je None (žádné).|

### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Filtrovat >](filter-element-for-add-for-sharedlisteners.md)|Přidá filtr do naslouchacího procesu v `sharedListeners` kolekci.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`sharedListeners`|Kolekce posluchačů, na které může odkazovat jakýkoliv element source nebo Trace.|  
  
## <a name="remarks"></a>Poznámky  
 Třídy naslouchacího procesu dodávané s .NET Framework jsou odvozeny z <xref:System.Diagnostics.TraceListener> třídy. Hodnota pro `name` atribut se používá pro přidání sdíleného naslouchacího procesu `Listeners` do kolekce pro trasování nebo zdroj trasování. Hodnota `initializeData` atributu závisí na typu naslouchacího procesu, který vytvoříte. Ne všechny naslouchací procesy trasování vyžadují, abyste `initializeData`určili.  
  
> [!NOTE]
> Při použití `initializeData` atributu se může zobrazit upozornění kompilátoru "atribut ' initializeData ' není deklarován." K tomuto upozornění dochází, protože nastavení konfigurace je ověřeno proti abstraktní základní <xref:System.Diagnostics.TraceListener>třídě, která `initializeData` atribut nerozpoznala. Obvykle můžete toto upozornění ignorovat pro implementace naslouchacího procesu trasování, které mají konstruktor, který přebírá parametr.  
  
 Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí .NET Framework a popisuje hodnotu jejich `initializeData` atributů.  
  
|Trace – třída naslouchacího procesu|hodnota atributu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|`useErrorStream` Hodnota<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> pro konstruktor  Nastavte atribut na "" pro zápis trasování a ladění výstupu do standardního streamu chyb. nastavte ho na "`false`", chcete-li zapisovat do standardního výstupního proudu.`true` `initializeData`|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Název souboru, do kterého se <xref:System.Diagnostics.DelimitedListTraceListener> zapisují.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Název existujícího zdroje protokolu událostí.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Název souboru, do kterého se <xref:System.Diagnostics.EventSchemaTraceListener> zapisují.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Název souboru, do kterého se <xref:System.Diagnostics.TextWriterTraceListener> zapisují.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Název souboru, do kterého se <xref:System.Diagnostics.XmlWriterTraceListener> zapisují.|  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `<add>` , jak použít prvky pro <xref:System.Diagnostics.TextWriterTraceListener> `textListener` přidání `sharedListeners` do kolekce.   `textListener`je přidán podle názvu do `Listeners` kolekce pro zdroj `TraceSourceApp`trasování. `textListener` Naslouchací proces zapisuje výstup trasování do souboru MyListener. log.  
  
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
- [Trasování a ladění schématu nastavení](index.md)
- [Moduly naslouchání trasování](../../../debug-trace-profile/trace-listeners.md)
