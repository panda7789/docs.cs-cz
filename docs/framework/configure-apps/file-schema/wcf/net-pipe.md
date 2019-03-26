---
title: < net.pipe >
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: 90d081c1287362669286aaa1185ed3b0bbe09b07
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412107"
---
# <a name="netpipe"></a>\<NET.pipe >
Určuje nastavení konfigurace služby Aktivace pojmenovaných kanálů, která spravuje životnost připojení pojmenovaného kanálu a zpracovává požadavky na aktivaci přicházející přes pojmenované kanály.  
  
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
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
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
|`maxPendingAccepts`|Celé číslo, které určuje maximální počet souběžně otevřených přijímacích vláken na koncový bod naslouchací služby pro sdílení. Výchozí hodnota je 2.|  
|`maxPendingConnections`|Celé číslo určující maximální počet připojení, které mohou čekat na odeslání. Výchozí hodnota je 100.|  
|`receiveTimeout`|A <xref:System.TimeSpan> , který určuje časový limit pro vytváření datových rámců a jejich odesílání z přidružených připojení. Výchozí hodnota je "00: 00:10"|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<allowAccounts>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Kolekce elementů konfigurace, které obsahují `securityIdentifier` atributy uživatelské účty pro procesy, které hostují služby WCF a jemuž je udělen přístup ke službě sdílení.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Obsahuje nastavení konfigurace pro naslouchací proces SMSvcHost.exe.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
