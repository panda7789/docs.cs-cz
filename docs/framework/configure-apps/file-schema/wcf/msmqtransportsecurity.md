---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5899c609b3cf52c4a275ba6fb10c5826fcf37f1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153006"
---
# \<msmqTransportSecurity>
Určuje nastavení zabezpečení přenosu služby MSMQ pro vlastní vazbu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
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
|`msmqAuthenticationMode`|Určuje, jak musí být zpráva ověřena přenosem služby MSMQ. Pokud je tento atribut nastaven na `None` hodnotu, `msmqProtectionLevel` musí být hodnota atributu také nastavena na `None` .<br /><br /> Platné hodnoty jsou následující:<br /><br /> -None: žádné ověřování.<br />-Windows: ověřovací mechanismus používá službu Active Directory k získání certifikátu X. 509 pro identifikátor SID přidružený ke zprávě. Pomocí této možnosti lze zkontrolovat seznam ACL fronty a zajistit tak, že uživatel má oprávnění k zápisu do fronty.<br />-Certificate: kanál získá certifikát z úložiště certifikátů.<br /><br /> Výchozí hodnota je Windows. Tento atribut je typu <xref:System.ServiceModel.MsmqAuthenticationMode> .|  
|`msmqEncryptionAlgorithm`|Určuje algoritmus, který se má použít pro šifrování zpráv na lince při přenosu zpráv mezi správci fronty zpráv. Platné hodnoty jsou následující:<br /><br /> - RC4Stream<br />– AES<br /><br /> Výchozí hodnota je RC4Stream. Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .|  
|`msmqProtectionLevel`|Určuje, jak je zpráva zabezpečena na úrovni přenosu služby MSMQ. Šifrování zajišťuje integritu zpráv i v době, kdy EncryptAndSign zajišťuje integritu zprávy i neneodvolatelnost; To znamená, že zpráva skutečně pochází od odesílatele a odesilatelem je, že k nim říká. Platné hodnoty jsou následující:<br /><br /> -None: bez ochrany.<br />-Sign: zprávy jsou podepsané.<br />-EncryptAndSign: zprávy jsou šifrované a podepsané.<br /><br /> Výchozí hodnota je Sign (podepsat). Tento atribut je typu <xref:System.Net.Security.ProtectionLevel> .|  
|`msmqSecureHashAlgorithm`|Určuje algoritmus, který se má použít při výpočtu výtahu jako součásti signatur. Platné hodnoty jsou následující:<br /><br /> – MD5<br />– SHA1<br />– SHA256<br />– SHA512<br /><br /> Výchozí hodnota je SHA1. Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .<br>Microsoft doporučuje SHA256 nebo lepší z důvodu kolizí problémů s MD5 a SHA1.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<msmqIntegration>](msmqintegration.md)|Určuje nastavení vyžadované pro interakci s odesílatelem nebo příjemcem služby Řízení front zpráv (MSMQ).|  
|[\<msmqTransport>](msmqtransport.md)|Určuje vlastnosti komunikace služby Řízení front pro službu Windows Communication Foundation (WCF), která používá nativní protokol MSMQ.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o zabezpečení přenosu najdete v tématu [zabezpečení přenosu](../../../wcf/feature-details/transport-security.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Fronty ve WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Přenosy](../../../wcf/feature-details/transports.md)
- [Volba přenosu](../../../wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Zabezpečení přenosu](../../../wcf/feature-details/transport-security.md)
