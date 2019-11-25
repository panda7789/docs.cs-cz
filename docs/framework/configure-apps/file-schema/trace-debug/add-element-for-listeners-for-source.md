---
title: <add> element pro <listeners> pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: c32205310f9fc451a5a55a943f925ee52f65c8a8
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088992"
---
# <a name="add-element-for-listeners-for-source"></a>\<přidat > element pro \<naslouchací proces > pro \<zdrojového >
Přidá naslouchací proces do kolekce `Listeners` pro zdroj trasování.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zdrojů >** ](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zdroj >** ](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Listeners**](listeners-element-for-source.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<přidat >**

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
|`type`|Povinný atribut, pokud neodkazujete na naslouchací proces v kolekci `sharedListeners`, v takovém případě je nutné na něj odkazovat pouze podle názvu (viz [příklad](#example)).<br /><br /> Určuje typ naslouchacího procesu. Je nutné použít řetězec, který splňuje požadavky zadané v části [určení plně kvalifikovaných názvů typů](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Nepovinný atribut.<br /><br /> Řetězec předaný konstruktoru pro určenou třídu. Pokud třída nemá konstruktor, který přebírá řetězec, je vyvolána <xref:System.Configuration.ConfigurationException>.|  
|`name`|Nepovinný atribut.<br /><br /> Určuje název naslouchacího procesu.|  
|`traceOutputOptions`|Nepovinný atribut.<br /><br /> Určuje hodnotu vlastnosti <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> pro naslouchací proces trasování.|  
|[vlastní atributy]|Volitelné atributy.<br /><br /> Určuje hodnotu pro atributy specifické pro naslouchací proces identifikovaných metodou <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> pro daný naslouchací proces. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> je příkladem nadbytečného atributu, který je jedinečný pro <xref:System.Diagnostics.DelimitedListTraceListener> třídu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[filtr \<](filter-element-for-add-for-listeners-for-source.md)|Přidá filtr do naslouchacího procesu v kolekci `Listeners` pro zdroj trasování.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`sources`|Obsahuje zdroje trasování, které spouštějí trasovací zprávy.|  
|`source`|Určuje zdroj trasování, který inicializuje trasovací zprávy.|  
|`listeners`|Určuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.|  
  
## <a name="remarks"></a>Poznámky  
 Třídy naslouchacího procesu dodávané s .NET Framework jsou odvozeny z <xref:System.Diagnostics.TraceListener> třídy.  
  
 Pokud nezadáte atribut `name` naslouchacího procesu trasování, vlastnost <xref:System.Diagnostics.TraceListener.Name%2A> naslouchacího procesu trasování je ve výchozím nastavení prázdný řetězec (""). Pokud má aplikace pouze jeden naslouchací proces, můžete ji přidat bez zadání názvu a můžete ji odebrat zadáním prázdného řetězce pro název. Pokud však má vaše aplikace více než jeden naslouchací proces, měli byste pro každé naslouchací proces trasování zadat jedinečný název, který umožňuje identifikovat a spravovat jednotlivé naslouchací procesy trasování v kolekci <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
> Přidání více než jednoho naslouchacího procesu trasování stejného typu a se stejným názvem má za následek pouze jeden naslouchací proces sledování tohoto typu a název přidaný do kolekce `Listeners`. Můžete však programově přidat do kolekce `Listeners` více stejných posluchačů.  
  
 Hodnota atributu `initializeData` závisí na typu naslouchacího procesu, který vytvoříte. Ne všechny naslouchací procesy trasování vyžadují, abyste zadali `initializeData`.  
  
> [!NOTE]
> Při použití atributu `initializeData` se může zobrazit upozornění kompilátoru "atribut ' initializeData ' není deklarován." K tomuto upozornění dochází, protože nastavení konfigurace je ověřeno proti abstraktní základní třídě <xref:System.Diagnostics.TraceListener>, která nerozeznává atribut `initializeData`. Obvykle můžete toto upozornění ignorovat pro implementace naslouchacího procesu trasování, které mají konstruktor, který přebírá parametr.  
  
 Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí .NET Framework a popisuje hodnotu jejich `initializeData` atributů.  
  
|Trace – třída naslouchacího procesu|hodnota atributu initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|Hodnota `useErrorStream` pro konstruktor <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>  Nastavte atribut `initializeData` na "`true`" pro zápis trasování a ladění výstupu do standardního streamu chyb. nastavte ji na "`false`" pro zápis do standardního výstupního proudu.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Název souboru, do kterého <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Název existujícího zdroje protokolu událostí.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Název souboru, do kterého <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Název souboru, do kterého <xref:System.Diagnostics.TextWriterTraceListener> zapisuje.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Název souboru, do kterého <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje.|  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `<add>` prvky pro přidání `console` a `textListener` do kolekce `Listeners` pro `TraceSourceApp`zdroje trasování. Naslouchací proces `textListener` zapisuje výstup trasování do souboru myListener. log.  
  
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
