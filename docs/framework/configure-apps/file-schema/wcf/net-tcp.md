---
title: '&lt;NET.TCP&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a3d22b6feef80dbff8c7f20b130ce2b0f9702c9e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltnettcpgt"></a>&lt;NET.TCP&gt;
Určuje nastavení konfigurace sítě. TCP Port sdílení služby, která umožňuje více procesů sdílet stejný port TCP.  
  
 \<system.serviceModel.activation >  
\<NET.TCP >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="Integer"  
          maxPendingAccepts="Integer"  
          maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan"  
          teredoEnabled="Boolean">  
          <allowAccounts>  
             <!-- LocalSystem account -->   
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->   
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->   
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->   
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only)-->   
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`listenBacklog`|Celé číslo, které určuje maximální počet nezpracovaných připojení, které přijímají sdíleného připojení, ale ještě nejsou odeslaných [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby. Výchozí hodnota je 10.|  
|`maxPendingAccepts`|Celé číslo, které určuje maximální počet nezpracovaných souběžných přijímá vláken pro naslouchání koncový bod pro službu sdílení. Výchozí hodnota je 2.|  
|`MaxPendingConnections`|Maximální počet připojení, která naslouchací proces může mít čeká se na aplikace akceptovat. Při překročení této hodnoty kvóty na nový příchozí připojení zahozených místo čekání na přijmout. Funkce připojení jako zabezpečení zpráv může způsobit klienta otevřít víc než jedno připojení. Správci služeb by měl účet pro tyto další připojení při nastavování této hodnoty kvóty. Výchozí hodnota je 10.|  
|`receiveTimeout`|A `TimeSpan` který určuje časový limit pro čtení dat rámcovacích a provádění připojení odeslání od připojení podtržení. Výchozí hodnota je "00: 00:10".|  
|`teredoEnabled`|Logická hodnota, která označuje, zda služby Sdílení portů používá službu Microsoft Teredo pro naslouchání TCP porty jménem [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby. Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<allowAccounts >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Kolekci elementů konfigurace, které obsahují `securityIdentifier` atribut k určení uživatelských účtů pro procesy, které hostují [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služby a je uděleno oprávnění k připojení ke službě sdílení.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.serviceModel.activation >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Obsahuje nastavení konfigurace pro proces naslouchání SMSvcHost.exe.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o sdílení portů najdete v tématu [sdílení portů Net.TCP](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded). Chcete-li pochopit, jak nakonfigurovat služby Sdílení portů, přečtěte si téma [konfigurace služby Sdílení portů Net.TCP](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [Sdílení portů Net.TCP](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded)  
 [Konfigurace služby sdílení portů Net.TCP](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)
