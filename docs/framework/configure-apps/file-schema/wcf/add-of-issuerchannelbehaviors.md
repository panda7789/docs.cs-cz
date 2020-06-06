---
title: <add> z <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398332"
---
# <a name="add-of-issuerchannelbehaviors"></a>\<add> z \<issuerChannelBehaviors>

Přidá chování koncového bodu, které se použije při komunikaci se službou STS.

> [!NOTE]
> Pokud jakékoli chování koncového bodu obsahuje [\<clientCredentials>](clientcredentials.md) element, vyvolá se výjimka.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a>Syntaxe

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|issuerAddress|Identifikátor URI vystavitele tokenu zabezpečení, se kterým se má komunikovat.|
|behaviorConfiguration|Název chování koncového bodu, které je definováno ve stejném konfiguračním souboru.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Description|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|Obsahuje kolekci chování koncového bodu klienta služby Windows Communication Foundation (WCF), která se má použít při komunikaci se zadanými službami tokenů služeb.|

## <a name="remarks"></a>Poznámky

`issuerAddress`obsahuje identifikátor URI služby tokenu zabezpečení, se kterou chce klient komunikovat. `behaviorConfiguration`odkazuje na chování koncového bodu, které aplikace používá v kanálech vytvořených pomocí Windows Communication Foundation (WCF) k získání vydaných tokenů ze služeb tokenů zabezpečení.

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Zabezpečení klientů](../../../wcf/securing-clients.md)
- [Postupy: Vytvoření federovaného klienta](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Postupy: Konfigurace místního vystavitele](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
