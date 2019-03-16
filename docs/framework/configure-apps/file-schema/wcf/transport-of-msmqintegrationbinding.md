---
title: <transport> z <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 53b434002d81e4735688ae3821db356c4e6e0fb1
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "58040288"
---
# <a name="transport-of-msmqintegrationbinding"></a>\<přenos > z \<msmqIntegrationBinding >
Definuje nastavení zabezpečení pro přenos integrace služby Řízení front zpráv.  
  
 \<system.ServiceModel>  
\<vazby >  
msmqIntegrationBinding  
\<Vytvoření vazby >  
\<security>  
\<přenos >  
  
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
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|Určuje, jak ověření zprávy dopravou služby MSMQ. Pokud je nastavené na `None`, hodnota `msmqProtectionLevel` atribut musí být také nastaven na `None`.<br /><br /> Platné hodnoty patří:<br /><br /> -Žádný: Bez ověřování.<br />– Třída: Mechanismus ověřování používá služby Active Directory k získání certifikátů X.509 pro identifikátor SID spojený se zprávou. Potom se používá ke kontrole, že seznam ACL fronty, aby uživatel má oprávnění k zápisu do fronty.<br />-Certifikátu: Kanál obdrží certifikát z úložiště certifikátů.<br /><br /> Výchozí hodnota je třída. Tento atribut je typu <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|Určuje algoritmus se má použít pro šifrování zpráv na lince, přenos zpráv mezi správci fronty zpráv. Platné hodnoty patří:<br /><br /> -RC4Stream<br />-   AES<br /><br /> Výchozí hodnota je RC4Stream. Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|Určuje, jak je zpráva zabezpečena na úrovni přenosu služby MSMQ. Šifrování zajišťuje integrity zprávy, zatímco EncryptAndSign zajišťuje zprávu integrity a nepopiratelnosti; To znamená že zpráva pochází skutečně od odesílatele a odesílatel je, který říká, že je.<br /><br /> -Platné hodnoty patří:<br />-Žádný: Žádná ochrana.<br />– Přihlášení: Zprávy jsou podepsané.<br />-EncryptAndSign: Zprávy jsou zašifrovaná a podepsaná.<br /><br /> Výchozí hodnota je znak. Tento atribut je typu ProtectionLevel.|  
|`msmqSecureHashAlgorithm`|: Určuje algoritmus pro výpočet výběru jako součást podpisu. Platné hodnoty patří:<br />-   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> Výchozí hodnota je SHA1. Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.<br>Způsobeny problémy kolizí se MD5 a SHA1 společnost Microsoft doporučuje SHA256 nebo vyšší.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Definuje nastavení zabezpečení pro vazby služby MSMQ.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek zapouzdřuje nastavení zabezpečení pro přenos integrace služby Řízení front zpráv. Nastavení jsou stejné pro integrace služby Řízení front zpráv a přenosů zařazených do fronty. Umožňuje vám nastavit režim ověřování, algoritmu šifrování, Secure Hash Algorithm a úroveň ochrany.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
