---
title: <transport> z <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 1cb165fed9266307335482166116c4c1d62efe7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152954"
---
# <a name="transport-of-msmqintegrationbinding"></a>\<transportní \<> msmqIntegrationBinding>
Definuje nastavení zabezpečení pro přenos integrace služby Řízení front zpráv.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<vázání>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<závazné>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bezpečnostní>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dopravní>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|Určuje, jak musí být zpráva ověřena přenosem služby MSMQ. Pokud je tato `None`hodnota nastavena `msmqProtectionLevel` na , musí `None`být hodnota atributu také nastavena na hodnotu .<br /><br /> Platné hodnoty zahrnují následující:<br /><br /> - Žádné: Žádné ověřování.<br />- WindowsDomain: Ověřovací mechanismus používá službu Active Directory k získání certifikátu X.509 pro sid přidružené ke zprávě. To se pak používá ke kontrole ACL fronty k zajištění, že uživatel má oprávnění k zápisu do fronty.<br />- Certifikát: Kanál získá certifikát z úložiště certifikátů.<br /><br /> Výchozí hodnota je WindowsDomain. Tento atribut je <xref:System.ServiceModel.MsmqAuthenticationMode>typu .|  
|`msmqEncryptionAlgorithm`|Určuje algoritmus, který má být použit pro šifrování zpráv na lince při přenosu zpráv mezi správci front zpráv. Platné hodnoty zahrnují následující:<br /><br /> - RC4Proud<br />- AES<br /><br /> Výchozí hodnota je RC4Stream. Tento atribut je <xref:System.ServiceModel.MsmqEncryptionAlgorithm>typu .|  
|`msmqProtectionLevel`|Určuje, jak je zpráva zabezpečena na úrovni přenosu služby MSMQ. Šifrování zajišťuje integritu zpráv, zatímco EncryptAndSign zajišťuje integritu zpráv i neodvolatelnost; to znamená, že zpráva skutečně pochází od odesílatele a odesílatel je, kdo říkají, že jsou.<br /><br /> - Platné hodnoty zahrnují následující:<br />- Žádná: Žádná ochrana.<br />- Znamení: Zprávy jsou podepsány.<br />- EncryptAndSign: Zprávy jsou šifrovány a podepsány.<br /><br /> Výchozí hodnota je Podepsat. Tento atribut je typu ProtectionLevel.|  
|`msmqSecureHashAlgorithm`|- Určuje algoritmus, který má být použit při výpočtu digest jako součást podpisů. Platné hodnoty zahrnují následující:<br />- MD5<br />- ŠA1<br />- SHA256<br />- SHA512<br /><br /> Výchozí hodnota je SHA1. Tento atribut je <xref:System.ServiceModel.MsmqSecureHashAlgorithm>typu .<br>Kvůli problémům s kolizí s MD5 a SHA1, Microsoft doporučuje SHA256 nebo lepší.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádný  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<bezpečnostní>](security-of-basichttpbinding.md)|Definuje nastavení zabezpečení pro vazbu služby MSMQ.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek zapouzdřuje nastavení zabezpečení pro přenos integrace služby Řízení front zpráv. Nastavení jsou stejná pro integraci služby Řízení front zpráv i přenosy ve frontě. Umožňuje nastavit režim ověřování, šifrovací algoritmus, algoritmus zabezpečeného algoritmu hash a úroveň ochrany.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<závazné>](bindings.md)
