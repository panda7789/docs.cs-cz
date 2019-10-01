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
ms.openlocfilehash: 0c7665898f8c625c2d07b67ea6c7fe25113fddd8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699480"
---
# <a name="add-element-for-sharedlisteners"></a>> element \<add pro \<sharedListeners >
Přidá naslouchací proces do kolekce `sharedListeners`. `sharedListeners` je kolekce posluchačů, na které může odkazovat jakýkoli [@no__t 2source >](source-element.md) nebo [\<trace >](trace-element.md) .  Ve výchozím nastavení nejsou naslouchací procesy v kolekci `sharedListeners` umístěny do kolekce `Listeners`. Musí být přidány pomocí názvu do [\<source >](source-element.md) nebo [\<trace >](trace-element.md). Není možné získat naslouchací procesy v kolekci `sharedListeners` v kódu v době běhu.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<sharedListeners >** ](sharedlisteners-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**  
  
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
|`traceOutputOptions`|Nepovinný atribut.<br/><br/>Řetězcové vyjádření jednoho nebo více členů výčtu @no__t 0, které označují data, která mají být zapsána do výstupu trasování. Více položek je odděleno čárkami. Výchozí hodnota je None (žádné).|

### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[@no__t – 1filter >](filter-element-for-add-for-sharedlisteners.md)|Přidá filtr do naslouchacího procesu v kolekci `sharedListeners`.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`sharedListeners`|Kolekce posluchačů, na které může odkazovat jakýkoliv element source nebo Trace.|  
  
## <a name="remarks"></a>Poznámky  
 Třídy naslouchacího procesu dodávané s .NET Framework jsou odvozeny z třídy <xref:System.Diagnostics.TraceListener>. Hodnota pro atribut `name` slouží k přidání sdíleného naslouchacího procesu do kolekce `Listeners` pro trasování nebo pro zdroj trasování. Hodnota pro atribut `initializeData` závisí na typu naslouchacího procesu, který vytvoříte. Ne všechny naslouchací procesy trasování vyžadují, abyste zadali `initializeData`.  
  
> [!NOTE]
> Při použití atributu `initializeData` se může zobrazit upozornění kompilátoru "atribut ' initializeData ' není deklarován." K tomuto upozornění dochází, protože nastavení konfigurace je ověřeno proti abstraktní základní třídě <xref:System.Diagnostics.TraceListener>, což nerozeznává atribut `initializeData`. Obvykle můžete toto upozornění ignorovat pro implementace naslouchacího procesu trasování, které mají konstruktor, který přebírá parametr.  
  
 Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí .NET Framework a popisuje hodnotu jejich atributů `initializeData`.  
  
|Trace – třída naslouchacího procesu|hodnota atributu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|Hodnota `useErrorStream` pro konstruktor <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.  Nastavte atribut `initializeData` na hodnotu "`true`" pro zápis trasování a ladění výstupu do standardního streamu chyb. nastavte ji na "`false`", chcete-li zapisovat do standardního výstupního proudu.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Název souboru, do kterého <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Název existujícího zdroje protokolu událostí.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Název souboru, do kterého <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Název souboru, do kterého <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Název souboru, do kterého <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.|  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít prvky `<add>` k přidání <xref:System.Diagnostics.TextWriterTraceListener> @ no__t-2 do kolekce `sharedListeners`.   `textListener` se přidá podle názvu do kolekce `Listeners` pro zdroj trasování `TraceSourceApp`. Naslouchací proces `textListener` zapisuje výstup trasování do souboru myListener. log.  
  
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
