---
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: 4a3a17655f5469fe84c0b684ebdac9848bbfba84
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397696"
---
# \<net.tcp>
Určuje nastavení konfigurace pro NET. Služba sdílení portů TCP, která umožňuje více procesů sdílet stejný port TCP.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**  
  
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
|`listenBacklog`|Celé číslo určující maximální počet nevyřízených připojení, které jsou přijímány ze sdíleného připojení, ale ještě nebyly odeslány do služeb Windows Communication Foundation (WCF). Výchozí hodnota je 10.|  
|`maxPendingAccepts`|Celé číslo, které určuje maximální počet nedokončených souběžných přijímajících vláken na koncovém bodu naslouchání pro službu sdílení. Výchozí hodnota je 2.|  
|`MaxPendingConnections`|Maximální počet připojení, která naslouchací proces mohl čekat na přijetí aplikací. Pokud je tato hodnota kvóty překročena, jsou nová příchozí připojení vynechána, ale čekají na přijetí. Funkce připojení, jako je například zabezpečení zprávy, mohou způsobit, že klient může otevřít více než jedno připojení. Správci služeb by měli při nastavení této kvóty brát v úvahu tato další připojení. Výchozí hodnota je 10.|  
|`receiveTimeout`|A <xref:System.TimeSpan> Určuje časový limit pro čtení dat rámců a provádění odesílání připojení z připojení s podtržením. Výchozí hodnota je "00:00:10".|  
|`teredoEnabled`|Logická hodnota, která označuje, zda služba sdílení portů používá službu Microsoft Teredo pro naslouchání na portech TCP jménem služeb WCF. Výchozí formát je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|Kolekce elementů konfigurace, které obsahují `securityIdentifier` atribut pro určení uživatelských účtů pro procesy, které hostují služby WCF, a kterým je udělen přístup k připojení ke službě sdílení.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|Obsahuje nastavení konfigurace procesu naslouchacího procesu SMSvcHost. exe.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o sdílení portů najdete v tématu [Sdílení portů Net. TCP](../../../wcf/feature-details/net-tcp-port-sharing.md). Informace o tom, jak nakonfigurovat službu sdílení portů, najdete v tématu [Konfigurace služby sdílení portů Net. TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [Sdílení portů Net.TCP](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [Konfigurace služby sdílení portů Net.TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
