---
title: <transport> z <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 28c8c877a766e0d881dd04f27298fae332bf08f8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736033"
---
# <a name="transport-of-msmqintegrationbinding"></a>> \<přenosů \<msmqIntegrationBinding >
Definuje nastavení zabezpečení pro přenos Integration služby Řízení front zpráv.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<msmqIntegrationBinding >** ](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**  
  
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
|`msmqAuthenticationMode`|Určuje, jak musí být zpráva ověřena přenosem služby MSMQ. Pokud je tato hodnota nastavená na `None`, musí být hodnota atributu `msmqProtectionLevel` taky nastavená na `None`.<br /><br /> Platné hodnoty jsou následující:<br /><br /> -None: žádné ověřování.<br />-WindowsDomain: ověřovací mechanismus používá službu Active Directory k získání certifikátu X. 509 pro identifikátor SID přidružený ke zprávě. Pomocí této možnosti lze zkontrolovat seznam ACL fronty a zajistit tak, že uživatel má oprávnění k zápisu do fronty.<br />-Certificate: kanál získá certifikát z úložiště certifikátů.<br /><br /> Výchozí hodnota je WindowsDomain. Tento atribut je typu <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|Určuje algoritmus, který se má použít pro šifrování zpráv na lince při přenosu zpráv mezi správci fronty zpráv. Platné hodnoty jsou následující:<br /><br /> - RC4Stream<br />– AES<br /><br /> Výchozí hodnota je RC4Stream. Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|Určuje, jak je zpráva zabezpečena na úrovni přenosu služby MSMQ. Šifrování zajišťuje integritu zpráv i v době, kdy EncryptAndSign zajišťuje integritu zprávy i neneodvolatelnost; To znamená, že zpráva skutečně pochází od odesílatele a odesilatele se říká, že je.<br /><br /> -Platné hodnoty jsou následující:<br />-None: bez ochrany.<br />-Sign: zprávy jsou podepsané.<br />-EncryptAndSign: zprávy jsou šifrované a podepsané.<br /><br /> Výchozí hodnota je Sign (podepsat). Tento atribut je typu ProtectionLevel.|  
|`msmqSecureHashAlgorithm`|– Určuje algoritmus, který se má použít při výpočtu výtahu jako součásti signatur. Platné hodnoty jsou následující:<br />– MD5<br />– SHA1<br />– SHA256<br />– SHA512<br /><br /> Výchozí hodnota je SHA1. Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.<br>Microsoft doporučuje SHA256 nebo lepší z důvodu kolizí problémů s MD5 a SHA1.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[> zabezpečení \<](security-of-basichttpbinding.md)|Definuje nastavení zabezpečení pro vazbu služby MSMQ.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek zapouzdřuje nastavení zabezpečení pro přenos integrace služby Řízení front zpráv. Nastavení jsou stejná pro integraci služby Řízení front zpráv i pro přenos ve frontě. Umožňuje nastavit režim ověřování, šifrovací algoritmus, zabezpečený algoritmus hash a úroveň ochrany.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [vazba \<](bindings.md)
