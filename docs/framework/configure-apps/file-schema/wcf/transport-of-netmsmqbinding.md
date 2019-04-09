---
title: <transport> of <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: ec726c4b39fedbf63a7ecc9e685a86367609fa43
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085000"
---
# <a name="transport-of-netmsmqbinding"></a>\<přenos > z \<netMsmqBinding >
Definuje nastavení zabezpečení přenosu.  
  
 \<system.ServiceModel>  
\<vazby >  
\<netMsmqBinding>  
\<Vytvoření vazby >  
\<security>  
\<přenos >  
  
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
|msmqAuthenticationMode|Určuje, jak ověření zprávy dopravou služby MSMQ. Platné hodnoty patří:<br /><br /> -Žádný: Bez ověřování.<br />– Třída: Mechanismus ověřování služby Active Directory používá k načtení certifikátu X.509 pro identifikátor zabezpečení spojený se zprávou. Potom se používá ke kontrole, že seznam ACL fronty, aby uživatel má oprávnění k zápisu pro danou frontu.<br />-Certifikátu: Kanál načte příslušný certifikát z úložiště certifikátů.<br /><br /> Výchozí hodnota je `WindowsDomain`.<br /><br /> Pokud tento atribut je nastaven na `None`, `msmqProtectionLevel` atribut musí být také nastaven na `None`. Tento atribut je typu <xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgorithm|Určuje algoritmus se má použít pro šifrování zpráv na lince, přenos zpráv mezi správci fronty zpráv. Platné hodnoty patří:<br /><br /> -RC4Stream<br />-   AES<br />– Výchozí hodnota je `RC4Stream`. Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|msmqProtectionLevel|Určuje že způsob, jak zprávy jsou zabezpečená na úrovni přenosu služby MSMQ. Šifrování zajišťuje, že zajišťuje zprávu integrity, při přihlašování a šifrování zpráv integrity a nepopiratelnosti. To znamená že zpráva pochází skutečně od odesílatele a odesílatel je, který říká, že je. Platné hodnoty patří:<br /><br /> -Žádný: Žádná ochrana.<br />– Přihlášení: Zprávy jsou podepsané.<br />-EncryptAndSign: Zprávy jsou zašifrovaná a podepsaná.<br />– Výchozí hodnota je `Sign`.|  
|msmqSecureHashAlgorithm|Určuje algoritmus hash, který má být použit pro výpočet výběru zprávy. Platné hodnoty patří:<br /><br /> -   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> Výchozí hodnota je `SHA1`. Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.<br>Způsobeny problémy kolizí se MD5 a SHA1 společnost Microsoft doporučuje SHA256 nebo vyšší.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Definuje nastavení zabezpečení přenosu pro přenosy tohoto zařazených do fronty.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Fronty ve WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
