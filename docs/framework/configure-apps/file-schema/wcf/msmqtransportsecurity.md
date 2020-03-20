---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5899c609b3cf52c4a275ba6fb10c5826fcf37f1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153006"
---
# <a name="msmqtransportsecurity"></a>\<msmqTransportBezpečnostní>
Určuje nastavení zabezpečení přenosu služby MSMQ pro vlastní vazbu.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<vázání>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<vlastní vazba>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<závazné>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrační>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportBezpečnostní>**  
  
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
|`msmqAuthenticationMode`|Určuje, jak musí být zpráva ověřena přenosem služby MSMQ. Pokud je tato `None`hodnota nastavena `msmqProtectionLevel` na , musí `None`být hodnota atributu také nastavena na hodnotu .<br /><br /> Platné hodnoty zahrnují následující:<br /><br /> - Žádné: Žádné ověřování.<br />- Windows: Ověřovací mechanismus používá službu Active Directory k získání certifikátu X.509 pro sid přidružené ke zprávě. To se pak používá ke kontrole ACL fronty k zajištění, že uživatel má oprávnění k zápisu do fronty.<br />- Certifikát: Kanál získá certifikát z úložiště certifikátů.<br /><br /> Výchozí hodnota je Systém Windows. Tento atribut je <xref:System.ServiceModel.MsmqAuthenticationMode>typu .|  
|`msmqEncryptionAlgorithm`|Určuje algoritmus, který má být použit pro šifrování zpráv na lince při přenosu zpráv mezi správci front zpráv. Platné hodnoty zahrnují následující:<br /><br /> - RC4Proud<br />- AES<br /><br /> Výchozí hodnota je RC4Stream. Tento atribut je <xref:System.ServiceModel.MsmqEncryptionAlgorithm>typu .|  
|`msmqProtectionLevel`|Určuje, jak je zpráva zabezpečena na úrovni přenosu služby MSMQ. Šifrování zajišťuje integritu zpráv, zatímco EncryptAndSign zajišťuje integritu zpráv i neodvolatelnost; to znamená, že zpráva skutečně pochází od odesílatele a odesílatel je, kdo říkají, že jsou. Platné hodnoty zahrnují následující:<br /><br /> - Žádná: Žádná ochrana.<br />- Znamení: Zprávy jsou podepsány.<br />- EncryptAndSign: Zprávy jsou šifrovány a podepsány.<br /><br /> Výchozí hodnota je Podepsat. Tento atribut je <xref:System.Net.Security.ProtectionLevel>typu .|  
|`msmqSecureHashAlgorithm`|Určuje algoritmus, který má být použit při výpočtu digest jako součást podpisů. Platné hodnoty zahrnují následující:<br /><br /> - MD5<br />- ŠA1<br />- SHA256<br />- SHA512<br /><br /> Výchozí hodnota je SHA1. Tento atribut je <xref:System.ServiceModel.MsmqSecureHashAlgorithm>typu .<br>Kvůli problémům s kolizí s MD5 a SHA1, Microsoft doporučuje SHA256 nebo lepší.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<msmqIntegrační>](msmqintegration.md)|Určuje nastavení potřebná pro interakci s odesílatelem nebo příjemcem služby Řízení front zpráv (MSMQ).|  
|[\<msmqTransport>](msmqtransport.md)|Určuje vlastnosti komunikace služby WCF (Queuing" pro službu WCF (Windows Communication Foundation), která používá nativní protokol služby MSMQ.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o zabezpečení dopravy naleznete v tématu [Transport Security](../../../wcf/feature-details/transport-security.md).  
  
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
- [\<vlastní vazba>](custombinding.md)
- [Zabezpečení přenosu](../../../wcf/feature-details/transport-security.md)
