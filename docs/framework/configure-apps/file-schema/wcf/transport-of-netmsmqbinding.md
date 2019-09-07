---
title: <transport> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: d6588e36a8a9420aa37837305aa904763c90781d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399351"
---
# <a name="transport-of-netmsmqbinding"></a>\<> přenosu > \<NetMsmqBinding
Definuje nastavení zabezpečení přenosu.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> přenosu**  
  
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
|msmqAuthenticationMode|Určuje, jak musí být zpráva ověřena přenosem služby MSMQ. Platné hodnoty jsou následující:<br /><br /> NTato Bez ověřování.<br />- WindowsDomain: Ověřovací mechanismus používá službu Active Directory k načtení certifikátu X. 509 pro identifikátor zabezpečení přidružený ke zprávě. Pomocí této možnosti lze zkontrolovat seznam ACL fronty a ověřit, zda má uživatel oprávnění k zápisu do fronty.<br />Certifikát Kanál načte certifikát z úložiště certifikátů.<br /><br /> Výchozí hodnota je `WindowsDomain`.<br /><br /> Pokud je tento atribut nastaven na `None`hodnotu `msmqProtectionLevel` , musí být atribut také nastaven na `None`hodnotu. Tento atribut je typu<xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgorithm|Určuje algoritmus, který se má použít pro šifrování zpráv na lince při přenosu zpráv mezi správci fronty zpráv. Platné hodnoty jsou následující:<br /><br /> - RC4Stream<br />– AES<br />– Výchozí hodnota je `RC4Stream`. Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|msmqProtectionLevel|Určuje způsob, jakým jsou zprávy zabezpečeny na úrovni přenosu služby MSMQ. Šifrování zajišťuje integritu zprávy, zatímco při podepisování a šifrování je zajištěna integrita zprávy i Neodmítnutí. To znamená, že zpráva skutečně pochází od odesílatele a odesilatele se říká, že je. Platné hodnoty jsou následující:<br /><br /> NTato Žádná ochrana.<br />Osobě Zprávy jsou podepsány.<br />EncryptAndSign Zprávy jsou zašifrovány a podepsány.<br />– Výchozí hodnota je `Sign`.|  
|msmqSecureHashAlgorithm|Určuje algoritmus hash, který se má použít k výpočtu výtahu zprávy. Platné hodnoty jsou následující:<br /><br /> -   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> Výchozí hodnota je `SHA1`. Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.<br>Microsoft doporučuje SHA256 nebo lepší z důvodu kolizí problémů s MD5 a SHA1.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> zabezpečení](security-of-netmsmqbinding.md)|Definuje nastavení zabezpečení přenosu pro přenosy ve frontě.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Fronty ve WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> vazby](../../../misc/binding.md)
