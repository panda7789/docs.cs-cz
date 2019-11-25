---
title: <remove> element pro <listeners> pro <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: f06973ec30d5061e4a200d6bf7e68adcf6302018
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088834"
---
# <a name="remove-element-for-listeners-for-trace"></a>\<odebrat > elementu pro \<naslouchací proces > pro \<trace >
Odebere naslouchací proces z kolekce **posluchačů** .  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trace >** ](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<naslouchacího procesu >** ](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**Jméno**|Požadovaný atribut.<br /><br /> Název naslouchacího procesu, který se má odebrat z kolekce **posluchačů** .|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`listeners`|Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy. Naslouchací procesy směrují výstup trasování do příslušného cíle.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`trace`|Konfiguruje službu trasování ASP.NET.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Odebráním <xref:System.Diagnostics.DefaultTraceListener> z kolekce `Listeners` se změní chování metod <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>. Volání metody `Assert` nebo `Fail` obvykle vede k zobrazení okna se zprávou, ale okno se zprávou není zobrazeno, pokud <xref:System.Diagnostics.DefaultTraceListener> není v `Listeners` Collection.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak odebrat výchozí naslouchací proces trasování z kolekce **posluchačů** trasování.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
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
