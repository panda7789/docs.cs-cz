---
title: Element <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 5faf352dce2a459a999b3cf54209f6bd9793bde0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673794"
---
# <a name="trace-element"></a>\<trasování > – Element
Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat trasovací zprávy.  
  
 \<Konfigurace >  
\<system.diagnostics>  
\<trasování >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`autoflush`|Nepovinný atribut.<br /><br /> Určuje, zda naslouchacími procesy trasování automaticky vyprázdní výstupní vyrovnávací paměť po každé operaci zápisu.|  
|`indentsize`|Nepovinný atribut.<br /><br /> Určuje počet mezer pro odsazení.|  
|`useGlobalLock`|Nepovinný atribut.<br /><br /> Označuje, zda má být použita globální zámku.|  
  
## <a name="autoflush-attribute"></a>autoflush atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|`false`|Není vyprázdnění automaticky výstupní vyrovnávací paměť. Toto nastavení je výchozí.|  
|`true`|Automaticky vyprázdní vyrovnávací paměť pro výstup.|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Nepoužívá globální uzamčení, pokud je bezpečná; pro naslouchací proces v opačném případě používá globální zámku.|  
|`true`|Používá globální zámek bez ohledu na to, jestli je bezpečná pro naslouchací proces. Toto nastavení je výchozí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<listeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|Určuje naslouchací proces, který shromažďuje, ukládá a provádí směrování zpráv.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `<trace>` prvek a přidat naslouchací proces `MyListener` k `Listeners` kolekce. `MyListener` Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru. `useGlobalLock` Atribut je nastaven na `false`, což způsobí, že globální zámek nechcete použít, pokud je bezpečná pro posluchače trasování. `autoflush` Atribut je nastaven na `true`, což způsobí, že naslouchací proces trasování pro zápis do souboru bez ohledu na to, zda <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> metoda je volána. `indentsize` Atribut je nastaven na hodnotu 0 (nula), což způsobí, že naslouchací proces odsazení nulové prostory při <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> metoda je volána.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
