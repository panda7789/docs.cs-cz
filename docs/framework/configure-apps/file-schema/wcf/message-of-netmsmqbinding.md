---
title: "&lt;message&gt; – &lt;netMsmqBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a7fdb8c6df84a76450aabaa983275f563d342fa
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a>&lt;message&gt; – &lt;netMsmqBinding&gt;
Definuje nastavení zabezpečení protokolu SOAP zprávy na tomto `netMsmqBinding` vazby.  
  
 \<system.ServiceModel>  
\<vazby >  
\<netMsmqBinding>  
\<Vazba >  
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
|algorithmSuite|Nastaví zprávu algoritmy šifrování a klíč wrap, které se používají k dosažení zabezpečení na základě zpráv pro zprávy odeslané přes přenos MSMQ.<br /><br /> Výchozí hodnota je `Aes256`. Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|clientCredentialType|Určuje typ pověření, který se má použít při ověřování klienta pro zprávy odeslané přes přenosu služby MSMQ. Platné hodnoty patří:<br /><br /> -None: To umožňuje službu k interakci s anonymní klienty. Služba ani klient vyžaduje přihlašovací údaje.<br />-Windows: Umožňuje výměnu SOAP pod pro ověřený kontext pověření systému Windows. Vždy provede ověřování založené na protokolu Kerberos.<br />-UserName: To povoluje službu tak, aby vyžadovala, ověření klienta pomocí pověření uživatelského jména. Přihlašovací údaje v takovém případě musí být zadán pomocí `clientCredentials` chování **upozornění:** [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] nepodporuje odesílání heslo hodnotou hash nebo odvozování klíče pomocí hesla a použití tyto klíče pro zabezpečení zpráv. Proto [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] vynutí, že exchange zabezpečené při použití pověření uživatelského jména. Tento režim vyžaduje, aby byl certifikát služby specifikován na straně klienta používá `clientCredential` chování a `serviceCertificate`. <br /><br /> -Certifikát: To povoluje službu tak, aby vyžadovala, ověření klienta pomocí certifikátu. V takovém případě musí být zadán pomocí pověření klienta `clientCredentials` chování. Přihlašovací údaje služby v takovém případě musí být zadán pomocí `clientCredentials` chování zadáním `serviceCertificate`.<br />-CardSpace: To umožňuje službě vyžadují, ověření klienta pomocí CardSpace. `serviceCertiifcate` Musí být zřízená v `clientCredential` chování.<br /><br /> Výchozí hodnota je `Windows`. Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.|  
  
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
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
