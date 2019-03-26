---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 692c4cf6688bfc2f9b99f065f4b16711f7f08063
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412042"
---
# <a name="nettcp"></a>\<net.tcp>
Určuje nastavení konfigurace sítě. TCP služba Sdílení portů, která umožňuje sdílet stejný port TCP mezi více procesy.  
  
 \<system.serviceModel.activation>  
\<net.tcp>  
  
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
  
## <a name="type"></a>Type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`listenBacklog`|Celé číslo určující maximální počet nevyřízených připojení, které jsou přijaty od sdíleného připojení, ale ještě nebyly odeslány do služby Windows Communication Foundation (WCF). Výchozí hodnota je 10.|  
|`maxPendingAccepts`|Celé číslo, které určuje maximální počet souběžně otevřených přijímacích vláken na koncový bod naslouchací služby pro sdílení. Výchozí hodnota je 2.|  
|`MaxPendingConnections`|Maximální počet připojení, která mohou v naslouchacím čekat na přijetí aplikací. Při překročení této kvóty hodnoty nové příchozí připojení jsou vynechány místo čekat na přijetí. Připojení funkce, jako je zabezpečení zpráv můžete donutit klienta k otevření více než jedno připojení. Správci služeb by měl účet pro tyto další připojení při nastavování této hodnoty kvóty. Výchozí hodnota je 10.|  
|`receiveTimeout`|A <xref:System.TimeSpan> , který určuje časový limit pro vytváření datových rámců a jejich odesílání z přidružených připojení. Výchozí hodnota je "00: 00:10".|  
|`teredoEnabled`|Logická hodnota, která označuje, zda služba Sdílení portů používá službu Microsoft Teredo pro naslouchání na portech TCP, jménem služby WCF. Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<allowAccounts>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Kolekce elementů konfigurace, které obsahují `securityIdentifier` atributy uživatelské účty pro procesy, které hostují služby WCF a jemuž je udělen přístup ke službě sdílení.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Obsahuje nastavení konfigurace pro naslouchací proces SMSvcHost.exe.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o sdílení portů najdete v tématu [sdílení portů Net.TCP](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md). Postup konfigurace služby Sdílení portů najdete v tématu [konfigurace služby Sdílení portů Net.TCP](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [Sdílení portů Net.TCP](../../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Konfigurace služby sdílení portů Net.TCP](../../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
