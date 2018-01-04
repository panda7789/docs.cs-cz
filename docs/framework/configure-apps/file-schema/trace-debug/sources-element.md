---
title: "&lt;zdroje&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7abe1f4a536d9f321e0a8b300f9542255433c030
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsourcesgt-element"></a>&lt;zdroje&gt; – Element
Určuje trasování zdrojů, které zahájí trasování zpráv.  
  
 \<Konfigurace >  
\<System.Diagnostics >  
\<zdroje >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zdroj >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|Požadovaný element.<br /><br /> Určuje zdroj trasování, který iniciuje trasování zpráv.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`system.diagnostics`|Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element lze v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `<sources>` elementu, který chcete přidat zdroj trasování `mySource` a nastaví úroveň přepínač zdroje s názvem `sourceSwitch`. Naslouchací proces trasování konzoly je přidaná který informace trasování zapíše do konzoly.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="mySource" switchName="sourceSwitch"   
            switchType="System.Diagnostics.SourceSwitch"  >  
            <listeners>  
               <add name="console"   
                  type="System.Diagnostics.ConsoleTraceListener" >  
                  <filter type="System.Diagnostics.EventTypeFilter"   
                     initializeData="Error" />  
               </add>  
               <remove name="Default" />  
            </listeners>  
         </source>  
      </sources>  
      <switches>  
         <add name="sourceSwitch" value="Warning" />  
      </switches>    
   </system.diagnostics>   
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 [Trasování a ladění schématu nastavení](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [\<zdroj >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)
