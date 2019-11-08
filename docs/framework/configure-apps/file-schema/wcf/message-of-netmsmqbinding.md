---
title: <message> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736755"
---
# <a name="message-of-netmsmqbinding"></a>\<> zprávy \<netMsmqBinding >

Definuje nastavení zabezpečení zprávy protokolu SOAP u této `netMsmqBinding` vazby.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zpráva >**  

## <a name="syntax"></a>Syntaxe

```xml
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|algorithmSuite|Nastaví šifrování zprávy a algoritmy pro zabalení klíčů, které se používají k zajištění zabezpečení založeného na zprávách pro zprávy odesílané prostřednictvím přenosu služby MSMQ.<br /><br /> Výchozí hodnota je `Aes256`. Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|
|clientCredentialType|Určuje typ přihlašovacích údajů, které se mají použít při ověřování klienta pro zprávy odesílané prostřednictvím přenosu služby MSMQ. Platné hodnoty jsou následující:<br /><br /> -None: umožňuje službě interakci s anonymními klienty. Služba ani klient nevyžaduje pověření.<br />-Windows: umožňuje, aby Exchange SOAP byly pod ověřeným kontextem pověření systému Windows. Tato vždy provádí ověřování pomocí protokolu Kerberos.<br />-UserName: umožňuje službě vyžadovat, aby byl klient ověřený pomocí přihlašovacích údajů uživatele. Přihlašovací údaje v tomto případě je potřeba zadat pomocí `clientCredentials` chování při **:** Windows Communication Foundation (WCF) nepodporuje odeslání Digest hesla ani odvození klíčů pomocí hesla a použití takových klíčů pro zabezpečení zpráv. Proto WCF vynutilo, aby při použití přihlašovacích údajů uživatelského jména byla výměna zabezpečená. Tento režim vyžaduje, aby se certifikát služby zadal na straně klienta pomocí `clientCredential` chování a `serviceCertificate`. <br /><br /> -Certificate: umožňuje službě vyžadovat, aby byl klient ověřený pomocí certifikátu. Přihlašovací údaje klienta v tomto případě je potřeba zadat pomocí chování `clientCredentials`. Pověření služby v tomto případě je nutné zadat pomocí `clientCredentials` chování zadáním `serviceCertificate`.<br />-Služba CardSpace: umožňuje službě, aby vyžadovala ověření klienta pomocí služby CardSpace. `serviceCertificate` musí být zřízené v chování `clientCredential`.<br /><br /> Výchozí hodnota je `Windows`. Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|[> zabezpečení \<](security-of-netmsmqbinding.md)|Definuje nastavení zabezpečení pro vazbu.|

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [Fronty ve WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [vazba \<](bindings.md)
