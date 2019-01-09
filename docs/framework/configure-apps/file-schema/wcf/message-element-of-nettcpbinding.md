---
title: element &lt;message&gt; – &lt;netTcpBinding&gt;
ms.date: 03/30/2017
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
ms.openlocfilehash: 7af8cd9d36b56093eee2b53873c0fe0775a33430
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146157"
---
# <a name="ltmessagegt-element-of-ltnettcpbindinggt"></a>element &lt;message&gt; – &lt;netTcpBinding&gt;
Definuje typ požadavky zabezpečení na úrovni zpráva koncovým bodem nakonfigurovaným s [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<system.ServiceModel>  
\<vazby >  
\<netTcpBinding >  
\<Vytvoření vazby >  
\<zabezpečení >  
\<Zpráva >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<message algorithmSuite="System.Servicemodel.Security.SecurityAlgorithmsuite"
         clientCredentialType="None/Windows/UserName/Certificate/IssuedToken" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`algorithmSuite`|Nastaví zprávu algoritmy šifrování a klíč zalamování řádků. Algoritmy a velikosti klíče jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídy. Tyto algoritmy namapovat na uvedené ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).<br /><br /> V následující tabulce jsou uvedeny možné hodnoty. Výchozí hodnota je `Basic256`.<br /><br /> Pokud určuje vazby služby `algorithmSuite` hodnotu, která není rovna výchozí nastavení a generovat konfiguračního souboru pomocí Svcutil.exe, pak není správně vytvořen a musíte ručně upravit konfigurační soubor pro tento atribut nastavte na požadovanou hodnotu.|  
|`clientCredentialType`|Určuje typ přihlašovacích údajů pro použití při ověřování klientů pomocí zabezpečení na základě zpráv. V následující tabulce jsou uvedeny možné hodnoty. Výchozí hodnota je `UserName`. Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Basic128|Zabalení klíče použijte Aes128 šifrování, algoritmus pro hash Sha1 a Rsa. oaep mgf1p.|  
|Basic192|Použijte šifrování Aes192, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256|Použijte šifrování pomocí Aes256, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Rsa15|Pomocí Aes256 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|Basic192Rsa15|Použití Aes192 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|TripleDes|Použití šifrování TripleDes, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Rsa15|Použití Aes128 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|TripleDesRsa15|Použití šifrování TripleDes, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.|  
|Basic128Sha256|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic192Sha256|Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Sha256|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|TripleDesSha256|TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Sha256Rsa15|Použití Aes128 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic192Sha256Rsa15|Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic256Sha256Rsa15|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|TripleDesSha256Rsa15|TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
  
## <a name="clientcredentialtype-attribute"></a>Typ clientCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádná|To umožňuje službě komunikovat s anonymní klienty. Ve službě to znamená, že služba nevyžaduje žádné pověření klienta. Na straně klienta to znamená, že klient neposkytuje žádné pověření klienta.|  
|Windows|Umožňuje výměnu SOAP být pod správou ověřený kontext přihlašovacích údajů Windows.|  
|UserName|Umožňuje službě tak, aby vyžadovala, ověření klienta pomocí přihlašovacích údajů uživatelského jména. WCF nepodporuje odesílání hodnotou hash hesla nebo odvození klíče pomocí hesla a pomocí těchto klíčů pro zabezpečení zpráv. V důsledku toho WCF vynutí, že při použití pověření uživatelských jmen je zabezpečený přenos. Výsledkem interoperabilní exchange nebo -interoperabilní vyjednávání na základě tohoto režimu přihlašovacích údajů `negotiateServiceCredential` atribut.|  
|Certifikát|Umožňuje službě tak, aby vyžadovala, ověření klienta pomocí certifikátu. Pokud se používá režim zabezpečených zpráv a `negotiateServiceCredential` atribut je nastaven na `false`, klient musí být poskytnut certifikát služby.|  
|Třídy IssuedToken|Určuje vlastní token, obvykle vydané službou tokenu služby zabezpečení (STS).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Definuje možnosti zabezpečení pro <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.|  
  
## <a name="remarks"></a>Poznámky  
 Zprávy používá zabezpečení na úrovni zprávy pro integritu a důvěrnost zpráv SOAP a pro vzájemné ověřování partnerských uzlů komunikace. Vybrali tento režim zabezpečení u vazby kanálu zásobníku je nakonfigurována s elementy vazby zabezpečení zpráv a zabezpečené zprávy protokolu SOAP v souladu s WS-Security * standardy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.MessageSecurityOverTcp>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
