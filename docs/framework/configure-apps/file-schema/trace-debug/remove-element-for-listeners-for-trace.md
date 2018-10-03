---
title: '&lt;Odebrat&gt; – Element pro &lt;naslouchacích procesů&gt; pro &lt;trasování&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 54fd529c571c8e8cf43c5dabe2398ae4a6cf4f11
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030532"
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;Odebrat&gt; – Element pro &lt;naslouchacích procesů&gt; pro &lt;trasování&gt;
Odebere z naslouchacího procesu **naslouchacích procesů** kolekce.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<trasování >  
\<naslouchací procesy >  
\<Odebrat >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|**Jméno**|Požadovaný atribut.<br /><br /> Název naslouchacího procesu odebrání **naslouchacích procesů** kolekce.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`listeners`|Určuje naslouchací proces, který shromažďuje, ukládá a provádí směrování zpráv. Posluchači přímý výstup trasování příslušný cíli.|  
|`system.diagnostics`|Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.|  
|`trace`|Nakonfiguruje službu sledování technologie ASP.NET.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Odebírá <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekce mění chování <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metody. Volání `Assert` nebo `Fail` metoda normálně ve výsledku zobrazení okna se zprávou, ale okno se zprávou se nezobrazí, pokud <xref:System.Diagnostics.DefaultTraceListener> není v `Listeners` kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k odebrání naslouchacího procesu trasování výchozí trasování **naslouchacích procesů** kolekce.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
