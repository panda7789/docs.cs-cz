---
title: <security> z <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: f2750036aa4d3fbe41062ad041e50ff3a4be32b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283960"
---
# <a name="security-of-nethttpbinding"></a>\<zabezpečení > z \<netHttpBinding >

Definuje možnosti zabezpečení [ \<basicHttpBinding >](basichttpbinding.md).

\<system.ServiceModel>\
\<vazby > \
\<netHttpBinding>\
\<binding>\
\<security>

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
|režim|Volitelné. Určuje typ zabezpečení, který se používá. Výchozí hodnota je `None`. Tento atribut je typu <xref:System.ServiceModel.BasicHttpSecurityMode>.|

## <a name="mode-attribute"></a>atribut režimu

|Hodnota|Popis|
|-----------|-----------------|
|Žádná|-Zprávy nejsou zabezpečená při přenosu.|
|Přenos|Zabezpečení je prováděno pomocí přenos protokolu HTTPS. Zprávy protokolu SOAP jsou zabezpečené pomocí protokolu HTTPS. Služba je ověřen u klienta pomocí certifikátu X.509 služby. Klient je ověřený pomocí nebyl typ ClientCredentialType zadán.|
|Zpráva|Poskytuje zabezpečení pomocí zabezpečení zprávy protokolu SOAP. Ve výchozím nastavení je tělo zašifrovaný a podepsaný. Pro tuto vazbu systému vyžaduje, aby certifikát serveru poskytnuta klientovi mimo pásmo. Jediné platné `ClientCredentialType` pro tuto vazbu `Certificate`.|
|TransportWithMessageCredential|Zabezpečení přenosu zajišťují integritu a důvěrnost serveru ověřování. Ověření klienta je k dispozici prostřednictvím zabezpečení zprávy protokolu SOAP. Tento režim je důležité, když se uživatel ověřuje pomocí uživatelského jména a hesla a nějaké existující nasazení HTTP pro přenos zpráv zabezpečení.|
|TransportCredentialOnly|Tento režim neposkytuje integrity a důvěrnosti zpráv. Poskytuje ověření klienta založené na protokolu http. Tento režim je třeba používat opatrně. Byste měli použít ve prostředích, kde zabezpečení přenosu se neposkytujeme jiným způsobem (jako je protokol IPSec) a infrastruktura WCF se poskytuje pouze ověření klienta.|

### <a name="child-elements"></a>Podřízené prvky

|Prvek|Popis|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|Definuje nastavení zabezpečení přenosu pro základní služba HTTP. Tento element odpovídá <xref:System.ServiceModel.HttpTransportSecurity>.|
|[\<message>](message-of-nethttpbinding.md)|Definuje nastavení zabezpečení zpráv pro základní služba HTTP. Tento element odpovídá <xref:System.ServiceModel.BasicHttpMessageSecurity>.|

### <a name="parent-elements"></a>Nadřazené prvky

|Prvek|Popis|
|-------------|-----------------|
|vazba|Prvek vazby [ \<basicHttpBinding >](basichttpbinding.md).|

## <a name="remarks"></a>Poznámky

 Ve výchozím nastavení není zabezpečen zprávu protokolu SOAP a klient není ověřený. Tento prvek umožňuje konfigurovat nastavení dalšího ověření zabezpečení pro `netHttpBinding` elementu.

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Výběr typu přihlašovacích údajů](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Vytvoření vazby >](../../../misc/binding.md)
