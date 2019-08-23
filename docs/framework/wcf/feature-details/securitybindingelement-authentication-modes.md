---
title: Režimy ověřování SecurityBindingElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
ms.openlocfilehash: d55bc0e1ccd45409c09ddeba820ed74d00ae86f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949338"
---
# <a name="securitybindingelement-authentication-modes"></a>Režimy ověřování SecurityBindingElement
Windows Communication Foundation (WCF) poskytuje několik režimů, podle kterých se klienti a služby ověřují mezi sebou. Prvky vazby zabezpečení pro tyto režimy ověřování lze vytvořit pomocí statických metod <xref:System.ServiceModel.Channels.SecurityBindingElement> pro třídu nebo prostřednictvím konfigurace. Toto téma stručně popisuje režimy ověřování 18.  
  
 Příklad použití prvku pro jeden z režimů ověřování naleznete v tématu [How to: Vytvoří SecurityBindingElement pro zadaný režim](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)ověřování.  
  
## <a name="basic-configuration-programming"></a>Základní programování konfigurace  
 Následující postup popisuje, jak nastavit režim ověřování v konfiguračním souboru.  
  
#### <a name="to-set-the-authentication-mode-in-configuration"></a>Nastavení režimu ověřování v konfiguraci  
  
1. Do prvku > [ vazbypřidejte>CustomBinding.\<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
2. Jako podřízený element přidejte [ \<vazbu >](../../../../docs/framework/misc/binding.md) elementu do `<customBinding>` elementu.  
  
3. `<security>` Přidejte element`<binding>` do elementu.  
  
4. `authenticationMode` Nastavte atribut na jednu z hodnot popsaných níže. Například následující kód nastaví režim na `AnonymousForCertificate`.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SecureCustomBinding">  
         <security authenticationMode ="AnonymousForCertificate" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
#### <a name="to-set-the-mode-programmatically"></a>Postup při nastavování režimu prostřednictvím kódu programu  
  
1. Určete návratový typ, který může být jeden z následujících <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>:, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>nebo <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2. Zavolejte příslušnou statickou metodu <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy. Například následující kód volá <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> metodu.  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3. K vytvoření vlastní vazby použijte prvek vazby. Další informace najdete v tématu [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="mode-descriptions"></a>Popisy režimů  
  
### <a name="anonymousforcertificate"></a>AnonymousForCertificate  
 V tomto režimu ověřování je klient anonymní a služba se ověřuje pomocí certifikátu X. 509. Element vazby zabezpečení je <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> metodou. Případně můžete nastavit `authenticationMode` atribut <`security`> elementu na `AnonymousForCertificate`.  
  
### <a name="anonymousforsslnegotiated"></a>AnonymousForSslNegotiated  
 V tomto režimu ověřování je klient anonymní a služba je ověřena pomocí certifikátu X. 509, který je vyjednáno za běhu. Element vazby zabezpečení je <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácen `false` metodou, <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> Pokud je hodnota předána pro první parametr. Případně nastavte `authenticationMode` atribut na `AnonymousForSslNegotiated`.  
  
### <a name="certificateovertransport"></a>CertificateOverTransport  
 V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako token podporující potvrzení; To znamená, že token, který podepisuje podpis zprávy. Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě. Element vazby zabezpečení je <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A> metodou. Případně nastavte `authenticationMode` atribut na `CertificateOverTransport`.  
  
### <a name="issuedtoken"></a>Třídy IssuedToken  
 V tomto režimu ověřování klient neověřuje službu, jako by to bylo. místo toho se klient ověřuje ve službě tokenů zabezpečení a přijímá token SAML, který je pak vydaný serveru, aby prokázal, že vaše znalost sdíleného klíče je. Služba není ověřena pro klienta, ale služba tokenů zabezpečení šifruje sdílený klíč jako součást vydaného tokenu, aby klíč mohl dešifrovat pouze služba. Element vazby zabezpečení je <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A> metodou. Případně nastavte `authenticationMode` atribut na `IssuedToken`.  
  
### <a name="issuedtokenforcertificate"></a>IssuedTokenForCertificate  
 V tomto režimu ověřování klient neověřuje službu, jako by to bylo. místo toho se klient ověřuje ve službě tokenů zabezpečení a přijímá token SAML, který je pak vydaný serveru, aby prokázal, že vaše znalost sdíleného klíče je. Vydaný token se zobrazí ve vrstvě SOAP jako buď token podpory, nebo nosný token; To znamená, že token, který podepisuje podpis zprávy. Služba se ověřuje pro klienta pomocí certifikátu X. 509. Element vazby zabezpečení je <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A> metodou. Případně nastavte `authenticationMode` atribut na `IssuedTokenForCertificate`.  
  
### <a name="issuedtokenforsslnegotiated"></a>IssuedTokenForSslNegotiated  
 V tomto režimu ověřování klient neověřuje službu, jako by to bylo. místo toho se klient ověřuje ve službě tokenů zabezpečení a přijímá token SAML, který je pak vydaný serveru, aby prokázal, že vaše znalost sdíleného klíče je. Vydaný token se zobrazí ve vrstvě SOAP jako buď token podpory, nebo nosný token; To znamená, že token, který podepisuje podpis zprávy. Služba se ověřuje pomocí certifikátu X. 509. Element vazby zabezpečení je <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A> metodou. Případně nastavte `authenticationMode` atribut na `IssuedTokenForSslnegotiated`.  
  
### <a name="issuedtokenovertransport"></a>IssuedTokenOverTransport  
 V tomto režimu ověřování klient neověřuje službu, jako by to bylo. místo toho se klient ověřuje ve službě tokenů zabezpečení a přijímá token SAML, který je pak vydaný serveru, aby prokázal, že vaše znalost sdíleného klíče je. Vydaný token se zobrazí ve vrstvě SOAP jako buď token podpory, nebo nosný token; To znamená, že token, který podepisuje podpis zprávy. Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě. Element vazby zabezpečení je `TransportSecurityBindingElement` vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A> metodou. Případně nastavte `authenticationMode` atribut na `IssuedTokenOverTransport`.  
  
### <a name="kerberos"></a>Sdílené  
 V tomto režimu ověřování se klient ověřuje ve službě pomocí lístku Kerberos. Stejný lístek taky zajišťuje ověřování serveru. Element vazby zabezpečení je `SymmetricSecurityBindingElement` vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metodou. Případně nastavte `authenticationMode` atribut na `Kerberos`.  
  
> [!NOTE]
> Aby bylo možné použít tento režim ověřování, musí být účet služby přidružen k hlavnímu názvu služby (SPN). Pokud to chcete provést, spusťte službu pod účtem síťové služby nebo pod účtem místní systém. Případně můžete pomocí nástroje SetSpn. exe vytvořit hlavní název služby (SPN) pro účet služby. V obou případech musí klient používat správný hlavní název služby (SPN) v <xref:System.ServiceModel.EndpointAddress> [ \<elementu servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element nebo pomocí konstruktoru. Další informace najdete v tématu [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
> [!NOTE]
> Když se použije režim <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> `Kerberos` ověřování, úrovně a zosobnění se nepodporují.  
  
### <a name="kerberosovertransport"></a>KerberosOverTransport  
 V tomto režimu ověřování se klient ověřuje ve službě pomocí lístku Kerberos. Token protokolu Kerberos se zobrazí ve vrstvě SOAP jako token podporující potvrzení; To znamená, že token, který podepisuje podpis zprávy. Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě. Element vazby zabezpečení je `TransportSecurityBindingElement` vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A> metodou. Případně nastavte `authenticationMode` atribut na `KerberosOverTransport`.  
  
> [!NOTE]
> Aby bylo možné použít tento režim ověřování, musí být účet služby přidružen k hlavnímu názvu služby (SPN). Pokud to chcete provést, spusťte službu pod účtem síťové služby nebo pod účtem místní systém. Případně můžete pomocí nástroje SetSpn. exe vytvořit hlavní název služby (SPN) pro účet služby. V obou případech musí klient používat správný hlavní název služby (SPN) v <xref:System.ServiceModel.EndpointAddress> [ \<elementu servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element nebo pomocí konstruktoru. Další informace najdete v tématu [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
### <a name="mutualcertificate"></a>MutualCertificate  
 V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako token podporující potvrzení; To znamená, že token, který podepisuje podpis zprávy. Služba je také ověřena pomocí certifikátu X. 509. Element vazby zabezpečení je `SymmetricSecurityBindingElement` vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> metodou. Případně nastavte `authenticationMode` atribut na `MutualCertificate`.  
  
### <a name="mutualcertificateduplex"></a>MutualCertificateDuplex  
 V tomto režimu ověřování se klient ověřuje pomocí certifikátu X. 509, který se zobrazí ve vrstvě SOAP jako token podporující potvrzení; To znamená, že token, který podepisuje podpis zprávy. Služba je také ověřena pomocí certifikátu X. 509. Vazba je `AsymmetricSecurityBindingElement` vrácena <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A> metodou. Případně nastavte `authenticationMode` atribut na `MutualCertificateDuplex`.  
  
### <a name="mutualsslnegotiated"></a>MutualSslNegotiated  
 V tomto režimu ověřování se klient a služba ověřují pomocí certifikátů X. 509. Element vazby zabezpečení je `SymmetricSecurityBindingElement` vrácen `true` metodou, <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> Pokud je hodnota předána pro první parametr. Případně nastavte `authenticationMode` atribut na `MutualSslNegotiated`.  
  
### <a name="secureconversation"></a>SecureConversation  
 Element vazby zabezpečení je `SymmetricSecurityBindingElement` vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> metodou. Tato metoda přebírá <xref:System.ServiceModel.Channels.SecurityBindingElement> jako parametr, který se používá během inicializace k vytvoření zabezpečené relace. Případně nastavte `authenticationMode` atribut na `SecureConversation`.  
  
 Pokud není zadána žádná počáteční vazba, `SspiNegotiated` použije se pro Bootstrap režim ověřování.  
  
### <a name="sspinegotiation"></a>SspiNegotiation  
 V tomto režimu ověřování se k ověřování klienta a serveru používá protokol vyjednávání. Kerberos se používá, pokud je to možné. v opačném případě se použije NT LanMan (NTLM). Element vazby zabezpečení je `SymmetricSecurityBindingElement` vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A> metodou. Případně nastavte `authenticationMode` atribut na `SspiNegotiated`.  
  
### <a name="sspinegotiatedovertransport"></a>SspiNegotiatedOverTransport  
 V tomto režimu ověřování se k ověřování klienta a serveru používá protokol vyjednávání. Protokol Kerberos se používá, pokud je to možné. v opačném případě se použije NTLM. Výsledný token se zobrazí ve vrstvě SOAP jako token podporující potvrzení; To znamená, že token, který podepisuje podpis zprávy. Služba se navíc ověřuje na transportní vrstvě pomocí certifikátu X. 509. Element vazby zabezpečení je `TransportSecurityBindingElement` vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A> metodou. Případně nastavte `authenticationMode` atribut na `SspiNegotiatedOverTransport`.  
  
### <a name="usernameforcertificate"></a>UserNameForCertificate  
 V tomto režimu ověřování klient ověřuje službu pomocí tokenu uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token; To znamená token, který je podepsán podpisem zprávy. Služba se ověřuje pro klienta pomocí certifikátu X. 509. Element vazby zabezpečení je `SymmetricSecurityBindingElement` vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> metodou. Případně nastavte `authenticationMode` atribut na `UserNameForCertificate`.  
  
 Pro režim `UserNameForCertificate` ověřování musí klient i služba používat protokol WS-Security 1,1.  
  
### <a name="usernameforsslnegotiated"></a>UserNameForSslNegotiated  
 V tomto režimu ověřování se klient ověřuje pomocí tokenu uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token. To znamená token, který je podepsán podpisem zprávy. Služba se ověřuje pomocí certifikátu X. 509. Element vazby zabezpečení je `SymmetricSecurityBindingElement` vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A> metodou. Případně nastavte `authenticationMode` atribut na `UserNameForSslNegotiated`.  
  
### <a name="usernameovertransport"></a>UserNameOverTransport  
 V tomto režimu ověřování se klient ověřuje pomocí tokenu uživatelského jména, který se zobrazí ve vrstvě SOAP jako podepsaný podpůrný token; To znamená token, který je podepsán podpisem zprávy. Služba se ověřuje pomocí certifikátu X. 509 na transportní vrstvě. Element vazby zabezpečení je `TransportSecurityBindingElement` vrácen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A> metodou. Případně nastavte `authenticationMode` atribut na `UserNameOverTransport`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- [Postupy: Vytvoření SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
