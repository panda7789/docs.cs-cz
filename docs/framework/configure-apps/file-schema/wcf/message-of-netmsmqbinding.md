---
title: '&lt;message&gt; – &lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 65a8b0fa120d23931ad218ac67846c066b050af8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515811"
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a>&lt;message&gt; – &lt;netMsmqBinding&gt;
Definuje nastavení založená na protokolu SOAP zprávy zabezpečení v tomto `netMsmqBinding` vazby.  
  
 \<system.ServiceModel>  
\<vazby >  
\<netMsmqBinding >  
\<Vytvoření vazby >  
\<zabezpečení >  
\<Zpráva >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|algorithmSuite|Nastaví zprávu, šifrování a key-wrap algoritmy, které se používají k zajištění zabezpečení na základě zpráv pro zprávy odeslané přes přenosu služby MSMQ.<br /><br /> Výchozí hodnota je `Aes256`. Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|Typ clientCredentialType|Určuje typ přihlašovacích údajů pro použití při ověřování klientů pro zprávy odeslané přes přenosu služby MSMQ. Platné hodnoty patří:<br /><br /> -Žádný: To umožňuje službě komunikovat s anonymní klienty. Služby ani klienta vyžaduje přihlašovací údaje.<br />-Windows: Umožňuje výměnu SOAP být pod správou ověřený kontext přihlašovacích údajů pro Windows. To provádí ověřování pomocí protokolu Kerberos.<br />-UserName: To umožňuje službě tak, aby vyžadovala, ověření klienta pomocí přihlašovacích údajů uživatelského jména. Přihlašovací údaje, které v tomto případě musí být zadaná pomocí `clientCredentials` chování **upozornění:** Windows Communication Foundation (WCF) nepodporuje odesílání hodnotou hash nebo odvození klíče pomocí hesla a pomocí těchto klíčů pro heslo zabezpečení zpráv. Proto WCF vynutí, že při použití pověření uživatelských jmen zabezpečené výměny. Tento režim vyžaduje, aby byl specifikován certifikát služby na straně klienta pomocí `clientCredential` chování a `serviceCertificate`. <br /><br /> -Certificate: To umožňuje službě tak, aby vyžadovala, ověření klienta pomocí certifikátu. Pověření klienta nejsou v tomto případě musí být zadaná pomocí `clientCredentials` chování. Přihlašovací údaje služby v tomto případě musí být zadaná pomocí `clientCredentials` chování tak, že zadáte `serviceCertificate`.<br />-Služba CardSpace: To umožňuje službě tak, aby vyžadovala, ověření klienta pomocí CardSpace. `serviceCertiifcate` Musí být zřízený v `clientCredential` chování.<br /><br /> Výchozí hodnota je `Windows`. Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Definuje nastavení zabezpečení pro vazbu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [Fronty ve WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
