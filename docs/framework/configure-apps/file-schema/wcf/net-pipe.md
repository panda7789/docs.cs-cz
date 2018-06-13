---
title: '&lt;NET.pipe&gt;'
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: 71291b1163ffb4e5fe13ff18d88d47f7d2193497
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359361"
---
# <a name="ltnetpipegt"></a>&lt;NET.pipe&gt;
Určuje nastavení konfigurace s názvem kanálu aktivace služby, která spravuje životnost připojení pojmenovaný kanál a zpracovává požadavky na aktivaci, které přicházejí pomocí pojmenovaných kanálů.  
  
 \<system.serviceModel.activation>  
\<NET.pipe >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.pipe maxPendingAccepts="Integer"  
                    maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan">  
          <allowAccounts>  
             // LocalSystem account  
             <add securityIdentifier="S-1-5-18"/>  
             // LocalService account  
             <add securityIdentifier="S-1-5-19"/>  
             // Administrators account  
             <add securityIdentifier="S-1-5-20"/>  
             // Network Service account  
             <add securityIdentifier="S-1-5-32-544" />  
             // IIS_IUSRS account (Vista only)  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.pipe>  
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
|`maxPendingAccepts`|Celé číslo, které určuje maximální počet nezpracovaných souběžných přijímá vláken pro naslouchání koncový bod pro službu sdílení. Výchozí hodnota je 2.|  
|`maxPendingConnections`|Celé číslo, které určuje maximální počet připojení, která může čekat pro odesílání. Výchozí hodnota je 100.|  
|`receiveTimeout`|A `TimeSpan` který určuje časový limit pro čtení dat rámcovacích a provádění připojení odeslání od připojení podtržení. Výchozí hodnota je "00: 00:10"|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<allowAccounts >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Kolekci elementů konfigurace, které obsahují `securityIdentifier` atribut zadejte uživatelské účty pro procesy, které hostování služby WCF a je uděleno oprávnění k připojení ke službě sdílení.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Obsahuje nastavení konfigurace pro proces naslouchání SMSvcHost.exe.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
