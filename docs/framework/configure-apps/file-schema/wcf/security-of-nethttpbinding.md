---
title: <security> z <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 97c52fa4f062ed0c65d5b1a8ca47a1439ab04cf5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736489"
---
# <a name="security-of-nethttpbinding"></a>\<security> z \<netHttpBinding>

Definuje možnosti zabezpečení [\<netHttpBinding>](nethttpbinding.md) .

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  

## <a name="syntax"></a>Syntaxe

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|režim|Nepovinný parametr. Určuje typ zabezpečení, který se použije. Výchozí formát je `None`. Tento atribut je typu <xref:System.ServiceModel.BasicHttpSecurityMode> .|

## <a name="mode-attribute"></a>mode – atribut

|Hodnota|Description|
|-----------|-----------------|
|Žádné|– Zprávy nejsou během přenosu zabezpečeny.|
|Přenos|Zabezpečení je zajištěno pomocí přenosu HTTPS. Zprávy SOAP jsou zabezpečeny pomocí protokolu HTTPS. Služba se ověřuje pro klienta pomocí certifikátu X. 509 služby. Klient se ověřuje pomocí dodaného ClientCredentialType.|
|Zpráva|Zabezpečení je k dispozici pomocí protokolu SOAP Message Security. Ve výchozím nastavení je text zašifrovaný a podepsaný. Pro tuto vazbu systému vyžaduje, aby byl certifikát serveru poskytnutý klientovi mimo IP síť. `ClientCredentialType`Tato vazba je platná pouze pro tuto vazbu `Certificate` .|
|TransportWithMessageCredential|Zabezpečení přenosu zajišťuje integrita, důvěrnost a ověřování serveru. Ověřování klientů je zajištěno prostřednictvím zabezpečení zpráv SOAP. Tento režim je vhodný v případě, že se uživatel ověřuje pomocí uživatelského jména a hesla a existuje stávající nasazení HTTP pro zabezpečení přenosu zpráv.|
|TransportCredentialOnly|Tento režim neposkytuje integritu a důvěrnost zpráv. Poskytuje ověřování klientů založené na protokolu HTTP. Tento režim by se měl používat opatrně. Měl by se používat v prostředích, kde je zabezpečení přenosu poskytované jiným způsobem (například IPSec) a infrastrukturou WCF poskytuje jenom ověřování klientů.|

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Description|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|Definuje nastavení zabezpečení přenosu pro základní službu HTTP. Tento prvek odpovídá <xref:System.ServiceModel.HttpTransportSecurity> .|
|[\<message>](message-of-nethttpbinding.md)|Definuje nastavení zabezpečení zpráv pro základní službu HTTP. Tento prvek odpovídá <xref:System.ServiceModel.BasicHttpMessageSecurity> .|

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Description|
|-------------|-----------------|
|vazba|Prvek vazby prvku [\<basicHttpBinding>](basichttpbinding.md) .|

## <a name="remarks"></a>Poznámky

 Ve výchozím nastavení není zpráva SOAP zabezpečená a klient není ověřen. Tento prvek umožňuje nakonfigurovat další nastavení zabezpečení pro `netHttpBinding` element.

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Výběr typu přihlašovacích údajů](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
