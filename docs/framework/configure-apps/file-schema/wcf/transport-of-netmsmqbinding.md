---
title: <transport> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: cc47c01cccc931e81ba57ab37ad9e3accfaa693b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152928"
---
# <a name="transport-of-netmsmqbinding"></a>\<dopravní> \<> netMsmqBinding
Definuje nastavení zabezpečení přenosu.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<vázání>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<závazné>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bezpečnostní>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dopravní>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim ověřování msmq|Určuje, jak musí být zpráva ověřena přenosem služby MSMQ. Platné hodnoty zahrnují následující:<br /><br /> - Žádné: Žádné ověřování.<br />- WindowsDomain: Ověřovací mechanismus používá službu Active Directory k načtení certifikátu X.509 pro identifikátor zabezpečení přidružený ke zprávě. To se pak používá ke kontrole ACL fronty k zajištění, že uživatel má oprávnění k zápisu pro frontu.<br />- Certifikát: Kanál načte certifikát z úložiště certifikátů.<br /><br /> Výchozí formát je `WindowsDomain`.<br /><br /> Pokud je tento `None`atribut `msmqProtectionLevel` nastaven na , `None`musí být atribut také nastaven na . Tento atribut je typu<xref:System.ServiceModel.MsmqAuthenticationMode>|  
|MsmqEncryptionAlgorithm|Určuje algoritmus, který má být použit pro šifrování zpráv na lince při přenosu zpráv mezi správci front zpráv. Platné hodnoty zahrnují následující:<br /><br /> - RC4Proud<br />- AES<br />- Výchozí hodnota `RC4Stream`je . Tento atribut je <xref:System.ServiceModel.MsmqEncryptionAlgorithm>typu .|  
|Úroveň ochrany msmq|Určuje způsob zabezpečení zpráv na úrovni přenosu msmq. Šifrování zajišťuje integritu zpráv, zatímco znaménko a šifrování zajišťuje integritu zpráv i neodvolatelnost. To znamená, že zpráva skutečně přišla od odesílatele a odesílatel je, kdo říkají, že jsou. Platné hodnoty zahrnují následující:<br /><br /> - Žádná: Žádná ochrana.<br />- Znamení: Zprávy jsou podepsány.<br />- EncryptAndSign: Zprávy jsou šifrovány a podepsány.<br />- Výchozí `Sign`hodnota je .|  
|msmqSecureHashAlgorithm|Určuje algoritmus hash, který má být použit pro výpočet digest zpráv. Platné hodnoty zahrnují následující:<br /><br /> - MD5<br />- ŠA1<br />- SHA256<br />- SHA512<br /><br /> Výchozí formát je `SHA1`. Tento atribut je <xref:System.ServiceModel.MsmqSecureHashAlgorithm>typu .<br>Kvůli problémům s kolizí s MD5 a SHA1, Microsoft doporučuje SHA256 nebo lepší.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádný  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<bezpečnostní>](security-of-netmsmqbinding.md)|Definuje nastavení zabezpečení přenosu pro přenosy ve frontě.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Fronty ve WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<závazné>](bindings.md)
