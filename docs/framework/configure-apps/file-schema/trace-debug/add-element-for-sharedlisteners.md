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
ms.openlocfilehash: 116a9633d16b8dd36c82f07a8e727f6f9f98f0ee
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088971"
---
# <a name="add-element-for-sharedlisteners"></a>\<přidat > element pro \<sharedListeners >
Přidá naslouchací proces do kolekce `sharedListeners`. `sharedListeners` je kolekce posluchačů, které mohou odkazovat jakékoli [\<zdrojového >](source-element.md) nebo [\<trace >](trace-element.md) .  Ve výchozím nastavení nejsou naslouchací procesy v kolekci `sharedListeners` umístěny do kolekce `Listeners`. Musí být přidány podle názvu do [\<zdrojového >](source-element.md) nebo [\<> trasování](trace-element.md). Není možné získat naslouchací procesy v kolekci `sharedListeners` v kódu v době běhu.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sharedListeners >** ](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<přidat >**

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
|`name`|Požadovaný atribut.<br /><br /> Určuje název naslouchacího procesu, který se používá k přidání sdíleného naslouchacího procesu do kolekce `Listeners`.|  
|`type`|Požadovaný atribut.<br /><br /> Určuje typ naslouchacího procesu. Je nutné použít řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Nepovinný atribut.<br /><br /> Řetězec předaný konstruktoru pro určenou třídu.|  
|`traceOutputOptions`|Nepovinný atribut.<br/><br/>Řetězcové vyjádření jednoho nebo více <xref:System.Diagnostics.TraceOptions> členů výčtu, které označují data, která mají být zapsána do výstupu trasování. Více položek je odděleno čárkami. Výchozí hodnota je None (žádné).|

### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[filtr \<](filter-element-for-add-for-sharedlisteners.md)|Přidá filtr do naslouchacího procesu v kolekci `sharedListeners`.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`sharedListeners`|Kolekce posluchačů, na které může odkazovat jakýkoliv element source nebo Trace.|  
  
## <a name="remarks"></a>Poznámky  
 Třídy naslouchacího procesu dodávané s .NET Framework jsou odvozeny z <xref:System.Diagnostics.TraceListener> třídy. Hodnota atributu `name` slouží k přidání sdíleného naslouchacího procesu do kolekce `Listeners` pro trasování nebo zdroj trasování. Hodnota atributu `initializeData` závisí na typu naslouchacího procesu, který vytvoříte. Ne všechny naslouchací procesy trasování vyžadují, abyste zadali `initializeData`.  
  
> [!NOTE]
> Při použití atributu `initializeData` se může zobrazit upozornění kompilátoru "atribut ' initializeData ' není deklarován." K tomuto upozornění dochází, protože nastavení konfigurace je ověřeno proti abstraktní základní třídě <xref:System.Diagnostics.TraceListener>, která nerozeznává atribut `initializeData`. Obvykle můžete toto upozornění ignorovat pro implementace naslouchacího procesu trasování, které mají konstruktor, který přebírá parametr.  
  
 Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí .NET Framework a popisuje hodnotu jejich `initializeData` atributů.  
  
|Trace – třída naslouchacího procesu|hodnota atributu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|Hodnota `useErrorStream` pro konstruktor <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>  Nastavte atribut `initializeData` na "`true`" pro zápis trasování a ladění výstupu do standardního streamu chyb. nastavte ji na "`false`" pro zápis do standardního výstupního proudu.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Název souboru, do kterého <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Název existujícího zdroje protokolu událostí.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Název souboru, do kterého <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Název souboru, do kterého <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Název souboru, do kterého <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.|  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `<add>` prvky pro přidání `textListener` <xref:System.Diagnostics.TextWriterTraceListener>do kolekce `sharedListeners`.   `textListener` se přidá podle názvu do kolekce `Listeners` pro `TraceSourceApp`zdroje trasování. Naslouchací proces `textListener` zapisuje výstup trasování do souboru myListener. log.  
  
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
