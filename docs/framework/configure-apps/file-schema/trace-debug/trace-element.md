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
ms.openlocfilehash: 02fd794eb7b7b7f46f7f7bc4e43036cb4a4758ed
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699173"
---
# <a name="trace-element"></a>@no__t – element > 0trace
Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. diagnostics >** ](system-diagnostics-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<trace >**  
  
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
|`autoflush`|Nepovinný atribut.<br /><br /> Určuje, zda naslouchací proces trasování po každé operaci zápisu automaticky vyprázdní výstupní vyrovnávací paměť.|  
|`indentsize`|Nepovinný atribut.<br /><br /> Určuje počet mezer, které mají být odsazeny.|  
|`useGlobalLock`|Nepovinný atribut.<br /><br /> Určuje, zda má být použit globální zámek.|  
  
## <a name="autoflush-attribute"></a>AutoFlush – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Nevyprázdní výstupní vyrovnávací paměť automaticky. Toto nastavení je výchozí.|  
|`true`|Automaticky vyprázdní výstupní vyrovnávací paměť.|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock – atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Nepoužívá globální zámek, pokud naslouchací proces je bezpečný pro přístup z více vláken; v opačném případě používá globální zámek.|  
|`true`|Používá globální zámek bez ohledu na to, zda je naslouchací proces bezpečný pro přístup z více vláken. Toto nastavení je výchozí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[@no__t – 1listeners >](listeners-element-for-trace.md)|Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití prvku `<trace>` pro přidání naslouchacího procesu `MyListener` do kolekce `Listeners`. `MyListener` vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru. Atribut `useGlobalLock` je nastaven na hodnotu `false`, což způsobí, že globální zámek nebude použit, pokud je naslouchací proces trasování bezpečný pro přístup z více vláken. Atribut `autoflush` je nastaven na hodnotu `true`, což způsobí, že naslouchací proces trasování zapisuje do souboru bez ohledu na to, zda je volána metoda <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType>. Atribut `indentsize` je nastaven na hodnotu 0 (nula), což způsobí, že naslouchací proces odsadí nula mezer při volání metody <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType>.  
  
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
- [Trasování a ladění schématu nastavení](index.md)
