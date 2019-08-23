---
title: <remove>Element pro <listeners> pro<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 0c5c9efb8a22d26ea5d4467f9628af5935d6dbad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920473"
---
# <a name="remove-element-for-listeners-for-trace"></a>\<Odebrat element > pro \<naslouchací procesy > \<pro > trasování
Odebere naslouchací proces z kolekce **posluchačů** .  
  
 \<> Konfigurace  
\<system.diagnostics>  
\<> trasování  
\<> naslouchací proces  
\<odebrat >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**name**|Požadovaný atribut.<br /><br /> Název naslouchacího procesu, který se má odebrat z kolekce posluchačů.|  
  
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
> <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>Odebrání zkolekcezmění<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>chování metod,, a .<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> <xref:System.Diagnostics.DefaultTraceListener> `Listeners` Volání metody `Fail` <xref:System.Diagnostics.DefaultTraceListener> nebo obvykle vede k zobrazení okna se zprávou, avšak okno se zprávou není zobrazeno, pokud není v `Listeners` kolekci. `Assert`  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak odebrat výchozí naslouchací proces trasování z kolekce posluchačů trasování.  
  
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
