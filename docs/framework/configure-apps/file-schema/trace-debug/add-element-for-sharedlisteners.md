---
title: "&lt;Přidat&gt; Element pro &lt;sharedListeners&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 490e58d4514667c5ec781dd76644012b0c97509d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltsharedlistenersgt"></a>&lt;Přidat&gt; Element pro &lt;sharedListeners&gt;
Přidá naslouchací proces a `sharedListeners` kolekce. `sharedListeners`je to všechny kolekce naslouchacího procesu [ \<zdroje >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) nebo [ \<trasování >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) , můžete odkazovat.  Ve výchozím nastavení, moduly pro naslouchání v `sharedListeners` kolekce nejsou uloženy do `Listeners` kolekce. Je nutné je přidat název, který [ \<zdroje >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) nebo [ \<trasování >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md). Není možné získat posluchače v `sharedListeners` kolekce v kódu v době běhu.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<sharedListeners > elementu  
\<Přidat >  
  
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
|`name`|Požadovaný atribut.<br /><br /> Určuje název naslouchací proces, který se používá k přidání sdílené naslouchacího procesu `Listeners` kolekce.|  
|`type`|Požadovaný atribut.<br /><br /> Určuje typ naslouchacího procesu. Je nutné použít řetězec, který splňuje požadavky uvedené v [určení plně kvalifikované názvy typů](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Nepovinný atribut.<br /><br /> Řetězec předaný konstruktoru pro zadanou třídu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|Přidá filtr do naslouchací proces ve `sharedListeners` kolekce.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.|  
|`sharedListeners`|Kolekce naslouchací procesy, které může odkazovat všechny zdroje nebo element trasování.|  
  
## <a name="remarks"></a>Poznámky  
 Naslouchací proces třídy součástí rozhraní .NET Framework odvozena od <xref:System.Diagnostics.TraceListener> třídy. Hodnota `name` atribut se používá k přidání sdílené naslouchacího procesu `Listeners` kolekce pro trasování nebo zdroj trasování. Hodnota `initializeData` atribut závisí na typu naslouchacího procesu vytvoříte. Ne všechny trasování – moduly naslouchání vyžadují, aby `initializeData`.  
  
> [!NOTE]
>  Při použití `initializeData` atributu, může získat kompilátoru upozornění "není deklarován atribut 'initializeData'." Toto upozornění se zobrazí, protože nastavení konfigurace se ověřují vůči abstraktní základní třída <xref:System.Diagnostics.TraceListener>, který nebyl rozpoznán `initializeData` atribut. Obvykle můžete toto upozornění pro implementace naslouchací proces trasování, které mají konstruktor, který přebírá parametr ignorovat.  
  
 Následující tabulka ukazuje naslouchací procesy trasování, které jsou součástí rozhraní .NET Framework a popisuje hodnotu jejich `initializeData` atributy.  
  
|Trasovací třída naslouchací proces|Hodnota initializeData – atribut|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|`useErrorStream` Hodnota <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> konstruktor.  Nastavte `initializeData` atribut "`true`"zápis trasování a ladění výstupu na standardní chybový proud; ji nastavte na"`false`" k zápisu do standardního výstupního datového proudu.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|Název souboru <xref:System.Diagnostics.DelimitedListTraceListener> zapisuje do.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Název existující zdroj protokolu událostí.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Název souboru, který <xref:System.Diagnostics.EventSchemaTraceListener> zapisuje do.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Název souboru, který <xref:System.Diagnostics.TextWriterTraceListener> zapisuje do.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|Název souboru, který <xref:System.Diagnostics.XmlWriterTraceListener> zapisuje do.|  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `<add>` elementy přidat <xref:System.Diagnostics.TextWriterTraceListener> `textListener` k `sharedListeners` kolekce.   `textListener`název, který přidává `Listeners` kolekci pro zdroj trasování `TraceSourceApp`. `textListener` Naslouchací proces zapisuje do souboru myListener.log výstup trasování.  
  
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
