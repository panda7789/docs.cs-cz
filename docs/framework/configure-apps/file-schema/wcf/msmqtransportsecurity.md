---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: fece74e76f879eff51f154eab8c8edea2c27119e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180125"
---
# <a name="msmqtransportsecurity"></a>\<msmqTransportSecurity>
Určuje nastavení zabezpečení přenosu služby MSMQ pro vlastní vazbu.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<msmqIntegration>  
\<msmqTransportSecurity>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|Určuje, jak ověření zprávy dopravou služby MSMQ. Pokud je nastavené na `None`, hodnota `msmqProtectionLevel` atribut musí být také nastaven na `None`.<br /><br /> Platné hodnoty patří:<br /><br /> -Žádný: Bez ověřování.<br />– Windows: Mechanismus ověřování používá služby Active Directory k získání certifikátů X.509 pro identifikátor SID spojený se zprávou. Potom se používá ke kontrole, že seznam ACL fronty, aby uživatel má oprávnění k zápisu do fronty.<br />-Certifikátu: Kanál obdrží certifikát z úložiště certifikátů.<br /><br /> Výchozí hodnota je Windows. Tento atribut je typu <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|Určuje algoritmus se má použít pro šifrování zpráv na lince, přenos zpráv mezi správci fronty zpráv. Platné hodnoty patří:<br /><br /> -RC4Stream<br />-   AES<br /><br /> Výchozí hodnota je RC4Stream. Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|Určuje, jak je zpráva zabezpečena na úrovni přenosu služby MSMQ. Šifrování zajišťuje integrity zprávy, zatímco EncryptAndSign zajišťuje zprávu integrity a nepopiratelnosti; To znamená že zpráva pochází skutečně od odesílatele a odesílatel je, který říká, že je. Platné hodnoty patří:<br /><br /> -Žádný: Žádná ochrana.<br />– Přihlášení: Zprávy jsou podepsané.<br />-EncryptAndSign: Zprávy jsou zašifrovaná a podepsaná.<br /><br /> Výchozí hodnota je znak. Tento atribut je typu <xref:System.Net.Security.ProtectionLevel>.|  
|`msmqSecureHashAlgorithm`|Určuje algoritmus pro výpočet výběru jako součást podpisu. Platné hodnoty patří:<br /><br /> -   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> Výchozí hodnota je SHA1. Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.<br>Způsobeny problémy kolizí se MD5 a SHA1 společnost Microsoft doporučuje SHA256 nebo vyšší.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<msmqIntegration>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegration.md)|Určuje nastavení pro interakci s řízení front zpráv (MSMQ) odesílatele a příjemce.|  
|[\<msmqTransport>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransport.md)|Určuje vlastnosti komunikaci služby Řízení front služby Windows Communication Foundation (WCF), který používá nativní protokol služby MSMQ.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o zabezpečení přenosu, naleznete v tématu [zabezpečení přenosu](../../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Fronty ve WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Zabezpečení přenosu](../../../../../docs/framework/wcf/feature-details/transport-security.md)
