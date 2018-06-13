---
title: element &lt;message&gt; – &lt;netTcpBinding&gt;
ms.date: 03/30/2017
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
ms.openlocfilehash: 4a487d695cab259fc6b82fdf44b4c1bfdf5d04e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364123"
---
# <a name="ltmessagegt-element-of-ltnettcpbindinggt"></a>element &lt;message&gt; – &lt;netTcpBinding&gt;
Definuje typ požadavků na zabezpečení na úrovni zpráv pro koncový bod nakonfigurované [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<system.ServiceModel>  
\<vazby >  
\<netTcpBinding >  
\<Vazba >  
\<zabezpečení >  
\<Zpráva >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<message   
      algorithmSuite=System.Servicemodel.Security.SecurityAlgorithmsuite  
    clientCredentialType="None/Windows/UserName/Certificate/IssuedToken"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`algorithmSuite`|Nastaví zprávu algoritmy šifrování a klíč wrap. Algoritmy a velikosti klíče jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídy. Tyto algoritmy mapovat platformám zadaným v specifikace jazyka zásady zabezpečení (WS-SecurityPolicy).<br /><br /> V následující tabulce jsou uvedeny možné hodnoty. Výchozí hodnota je `Basic256`.<br /><br /> Pokud určuje vazby služby `algorithmSuite` hodnotu, která není roven výchozí a generovat konfiguračního souboru pomocí Svcutil.exe, pak není správně vytvořen a je nutné ručně upravit konfigurační soubor, aby tento atribut požadovanou hodnotu.|  
|`clientCredentialType`|Určuje typ pověření, který se má použít při ověřování klienta pomocí zabezpečení na základě zpráv. V následující tabulce jsou uvedeny možné hodnoty. Výchozí hodnota je `UserName`. Tento atribut je typu <xref:System.ServiceModel.MessageCredentialType>.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Basic128|Použijte šifrování pomocí algoritmu aes128 za pomoci, Sha1 pro hodnota hash a šifrování Rsa. oaep mgf1p pro zabalení klíče.|  
|Basic192|Použijte šifrování pomocí Aes192, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256|Použijte šifrování pomocí Aes256, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Rsa15|Pomocí Aes256 pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|Basic192Rsa15|Použijte Aes192 pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|TripleDes|Použití šifrování TripleDes, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Rsa15|Pomocí algoritmu aes128 za pomoci pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|TripleDesRsa15|Použití šifrování TripleDes, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.|  
|Basic128Sha256|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic192Sha256|Použijte Aes192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic256Sha256|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|TripleDesSha256|Použití šifrování TripleDes pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.|  
|Basic128Sha256Rsa15|Pomocí algoritmu aes128 za pomoci pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic192Sha256Rsa15|Použijte Aes192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|Basic256Sha256Rsa15|Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
|TripleDesSha256Rsa15|Použití šifrování TripleDes pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|To umožňuje službu k interakci s anonymní klienty. Ve službě to znamená, že služba nevyžaduje žádné pověření klienta. Na klientovi to znamená, že klient nenabízí žádné pověření klienta.|  
|Windows|Umožňuje výměnu SOAP pod pro ověřený kontext pověření systému Windows.|  
|UserName|Umožňuje službě vyžadují, ověření klienta pomocí pověření uživatelského jména. WCF nepodporuje odesílání hodnotu hash hesla nebo odvozování klíče pomocí hesla a použití tyto klíče pro zabezpečení zpráv. Jako takový WCF vynutí, že při použití uživatelské jméno pověření zabezpečené přenosu. Tento režim pověření výsledkem umožňuje vzájemnou spolupráci exchange nebo jiný umožňuje vzájemnou spolupráci vyjednávání na základě `negotiateServiceCredential` atribut.|  
|certifikát|Umožňuje službě vyžadují, ověření klienta pomocí certifikátu. Pokud se používá režim zabezpečení zprávy a `negotiateServiceCredential` je atribut nastaven na `false`, klient musí být zřízená s certifikát služby.|  
|IssuedToken|Určuje vlastní token, obvykle vystavené pomocí zabezpečení tokenu služby (STS).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Definuje možnosti zabezpečení pro <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.|  
  
## <a name="remarks"></a>Poznámky  
 Zpráva používá zabezpečení na úrovni zpráv pro integrity a důvěrnosti zpráv protokolu SOAP a pro vzájemné ověřování partnerské uzly komunikace. Pokud je tento režim zabezpečení na vazbu, zásobník kanál je nakonfigurován s prvky vazby zabezpečení zpráv, která jsou zabezpečená protokolu SOAP zprávy v souladu s WS-standardy zabezpečení *.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.MessageSecurityOverTcp>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
