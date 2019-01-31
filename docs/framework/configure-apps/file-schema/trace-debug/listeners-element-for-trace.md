---
title: <listeners> – element pro element <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: cc6ba06127703fbda5d9edf8211b4b206127cbda
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271668"
---
# <a name="listeners-element-for-trace"></a>\<naslouchací procesy > – Element pro \<trasování >
Určuje naslouchací proces, který shromažďuje, ukládá a provádí směrování zpráv. Posluchači přímý výstup trasování příslušný cíli.  
  
 \<Konfigurace > – Element  
\<System.Diagnostics > – Element  
\<trasování > – Element  
\<naslouchací procesy > – Element pro \<trasování >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Přidá naslouchací proces pro `Listeners` kolekce.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|Vymaže `Listeners` kolekce pro trasování.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|Odebere z naslouchacího procesu `Listeners` kolekce.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje kořenový element části o konfiguraci technologie ASP.NET.|  
|`trace`|Obsahuje moduly pro naslouchání, které shromažďování, ukládání a směrovat trasovací zprávy.|  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.Diagnostics.Debug> a <xref:System.Diagnostics.Trace> třídy sdílet stejný **naslouchacích procesů** kolekce. Pokud chcete přidat objekt naslouchacího procesu do kolekce v jednom z těchto tříd, jiná třída používá stejný naslouchací proces. Naslouchací proces třídy součástí rozhraní .NET Framework jsou odvozeny od <xref:System.Diagnostics.TraceListener> třídy.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití  **\<naslouchacích procesů >** prvku pro přidání posluchače `MyListener` a `MyEventListener` k **naslouchacích procesů** kolekce. `MyListener` Vytvoří soubor s názvem `MyListener.log` a zapíše výstup do souboru. `MyEventListener` vytvoří záznam v protokolu událostí.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Diagnostics.TraceListener>
- [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
