---
title: <remove>Element pro <listeners> pro<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: edd27dd262004aead7db4d81db8ecab0e831dac1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926996"
---
# <a name="remove-element-for-listeners-for-source"></a>\<Odebrat element > pro \<naslouchací procesy > \<pro > zdrojového kódu
Odebere naslouchací proces z `Listeners` kolekce pro zdroj trasování.  
  
 \<> Konfigurace  
\<system.diagnostics>  
\<> zdrojů  
\<> zdroje  
\<> naslouchací proces  
\<odebrat >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Požadovaný atribut.<br /><br /> Název naslouchacího procesu, který se má odebrat z `Listeners` kolekce.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`sources`|Obsahuje zdroje trasování, které spouštějí trasovací zprávy.|  
|`source`|Určuje zdroj trasování, který inicializuje trasovací zprávy.|  
|`listeners`|Určuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.|  
  
## <a name="remarks"></a>Poznámky  
 Element Odebere zadaný naslouchací proces `Listeners` z kolekce pro zdroj trasování. `<remove>`  
  
 Můžete `Listeners` odebrat prvek z kolekce pro zdroj trasování programově <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> voláním metody <xref:System.Diagnostics.TraceSource> u <xref:System.Diagnostics.TraceSource.Listeners%2A> vlastnosti instance.  
  
 Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad `<remove>` ukazuje, jak použít element před `<add>` použitím elementu pro `Listeners` přidání naslouchacího procesu `console` do kolekce pro zdroj `TraceSourceApp`trasování.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [Trasování a ladění schématu nastavení](index.md)
- [\<clear>](clear-element-for-listeners-for-source.md)
- [Moduly naslouchání trasování](../../../debug-trace-profile/trace-listeners.md)
