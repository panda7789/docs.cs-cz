---
title: Režimy ověřování SecurityBindingElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
ms.openlocfilehash: 2aed766e6b2da7ebaf7b5b863375ee95b99eb159
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330334"
---
# <a name="securitybindingelement-authentication-modes"></a>Režimy ověřování SecurityBindingElement
Windows Communication Foundation (WCF) poskytuje několik režimů, které služby a klienti ověřování mezi sebou. Můžete vytvořit bezpečnostní prvky vazeb pro tyto režimy ověřování pomocí statické metody na <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy nebo prostřednictvím konfigurace. Tento článek stručně popisuje režimy ověřování 18.  
  
 Příklad použití elementu pro jeden z režimů ověřování najdete v tématu [jak: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="basic-configuration-programming"></a>Základní konfigurace programování  
 Následující postup popisuje, jak nastavit režim ověřování v konfiguračním souboru.  
  
#### <a name="to-set-the-authentication-mode-in-configuration"></a>Chcete-li nastavit režim ověřování v konfiguraci  
  
1. K [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element, přidejte [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2. Jako podřízený prvek, přidejte [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu `<customBinding>` elementu.  
  
3. Přidat `<security>` elementu `<binding>` elementu.  
  
4. Nastavte `authenticationMode` atribut na jednu z hodnot je popsáno níže. Například následující kód nastaví režim na `AnonymousForCertificate`.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SecureCustomBinding">  
         <security authenticationMode ="AnonymousForCertificate" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
#### <a name="to-set-the-mode-programmatically"></a>Pro nastavení režimu prostřednictvím kódu programu  
  
1. Určit návratový typ, který může být jedna z následujících akcí: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>, nebo <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2. Volat odpovídající statickou metodu <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy. Například následující kód volá <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> metody.  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3. Pro vytvoření vlastní vazby pomocí elementu vazby. Další informace najdete v tématu [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="mode-descriptions"></a>Popisy režimu  
  
### <a name="anonymousforcertificate"></a>AnonymousForCertificate  
 Tento režim ověřování klienta je anonymní a ověření služby pomocí certifikátu X.509. Element vazby zabezpečení je <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut <`security`> element `AnonymousForCertificate`.  
  
### <a name="anonymousforsslnegotiated"></a>AnonymousForSslNegotiated  
 Tento režim ověřování klienta je anonymní a ověření služby pomocí certifikátu X.509, který se vyjedná v době běhu. Element vazby zabezpečení je <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> metodu po hodnotu `false` je předán jako první parametr. Můžete také nastavit `authenticationMode` atribut `AnonymousForSslNegotiated`.  
  
### <a name="certificateovertransport"></a>CertificateOverTransport  
 S tímto režimem ověřování klient se ověří pomocí certifikátu X.509, který se zobrazí jako potvrzující podpůrný token; ve vrstvě protokolu SOAP To znamená, že token, který podepisuje podpis zprávy. Služba je ověřený pomocí certifikátu X.509 na transportní vrstvě. Element vazby zabezpečení je <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut `CertificateOverTransport`.  
  
### <a name="issuedtoken"></a>Třídy IssuedToken  
 S tímto režimem ověřování se klient neověřuje ke službě, jako například; Klient místo toho ověřuje u konkrétního služby tokenů zabezpečení a obdrží token SAML, která potom nabídne server k prokázání své znalosti o sdílený klíč. Službu není ověřený klient v důsledku toho ale služby tokenů zabezpečení tak, aby pouze službu může dešifrovat klíč zašifruje sdílený klíč jako součást vydaný token. Element vazby zabezpečení je <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut `IssuedToken`.  
  
### <a name="issuedtokenforcertificate"></a>IssuedTokenForCertificate  
 S tímto režimem ověřování se klient neověřuje ke službě, jako například; Klient místo toho ověřuje u konkrétního služby tokenů zabezpečení a obdrží token SAML, která potom nabídne server k prokázání své znalosti o sdílený klíč. Vydaný token se zobrazí ve vrstvě protokolu SOAP jako potvrzující podpůrný token nebo nosný token; To znamená, že token, který podepisuje podpis zprávy. Služba se ověřuje klienta pomocí certifikátu X.509. Element vazby zabezpečení je <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut `IssuedTokenForCertificate`.  
  
### <a name="issuedtokenforsslnegotiated"></a>IssuedTokenForSslNegotiated  
 S tímto režimem ověřování se klient neověřuje ke službě, jako například; Klient místo toho ověřuje u konkrétního služby tokenů zabezpečení a obdrží token SAML, která potom nabídne server k prokázání své znalosti o sdílený klíč. Vydaný token se zobrazí ve vrstvě protokolu SOAP jako potvrzující podpůrný token nebo nosný token; To znamená, že token, který podepisuje podpis zprávy. Služba je ověřený pomocí certifikátu X.509. Element vazby zabezpečení je <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut `IssuedTokenForSslnegotiated`.  
  
### <a name="issuedtokenovertransport"></a>IssuedTokenOverTransport  
 S tímto režimem ověřování se klient neověřuje ke službě, jako například; Klient místo toho ověřuje u konkrétního služby tokenů zabezpečení a obdrží token SAML, která potom nabídne server k prokázání své znalosti o sdílený klíč. Vydaný token se zobrazí ve vrstvě protokolu SOAP jako potvrzující podpůrný token nebo nosný token; To znamená, že token, který podepisuje podpis zprávy. Služba je ověřený pomocí certifikátu X.509 na transportní vrstvě. Element vazby zabezpečení je `TransportSecurityBindingElement` vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut `IssuedTokenOverTransport`.  
  
### <a name="kerberos"></a>Protokol Kerberos  
 S tímto režimem ověřování klient se ověří ve službě pomocí lístku protokolu Kerberos. Tento lístek stejné také poskytuje ověřování serveru. Element vazby zabezpečení je `SymmetricSecurityBindingElement` vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut `Kerberos`.  
  
> [!NOTE]
>  Chcete-li použít tento režim ověřování, musí být přidružen hlavní název služby (SPN) účtu služby. K tomuto účelu spuštění služby pod účtem síťové služby nebo účet místní systém. Můžete také pomocí nástroje SetSpn.exe vytvořte SPN pro účet služby. V obou případech musí klient použít správný hlavní název služby v [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element, nebo pomocí <xref:System.ServiceModel.EndpointAddress> konstruktoru. Další informace najdete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
> [!NOTE]
>  Když `Kerberos` se používá režim ověřování, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> a <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> úrovní zosobnění se nepodporují.  
  
### <a name="kerberosovertransport"></a>KerberosOverTransport  
 S tímto režimem ověřování klient se ověří ve službě pomocí lístku protokolu Kerberos. Token protokolu Kerberos se zobrazí ve vrstvě protokolu SOAP jako potvrzující podpůrný token; To znamená, že token, který podepisuje podpis zprávy. Služba je ověřený pomocí certifikátu X.509 na transportní vrstvě. Element vazby zabezpečení je `TransportSecurityBindingElement` vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut `KerberosOverTransport`.  
  
> [!NOTE]
>  Chcete-li použít tento režim ověřování, účet služby musí být přidružený název SPN. K tomuto účelu spuštění služby pod účtem síťové služby nebo účet místní systém. Můžete také pomocí nástroje SetSpn.exe vytvořte SPN pro účet služby. V obou případech musí klient použít správný hlavní název služby v [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element, nebo pomocí <xref:System.ServiceModel.EndpointAddress> konstruktoru. Další informace najdete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
### <a name="mutualcertificate"></a>MutualCertificate  
 S tímto režimem ověřování klient se ověří pomocí certifikátu X.509, který se zobrazí jako potvrzující podpůrný token; ve vrstvě protokolu SOAP To znamená, že token, který podepisuje podpis zprávy. Služba je také ověřit pomocí certifikátu X.509. Element vazby zabezpečení je `SymmetricSecurityBindingElement` vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut `MutualCertificate`.  
  
### <a name="mutualcertificateduplex"></a>MutualCertificateDuplex  
 S tímto režimem ověřování klient se ověří pomocí certifikátu X.509, který se zobrazí jako potvrzující podpůrný token; ve vrstvě protokolu SOAP To znamená, že token, který podepisuje podpis zprávy. Služba je také ověřit pomocí certifikátu X.509. Vazba není `AsymmetricSecurityBindingElement` vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut `MutualCertificateDuplex`.  
  
### <a name="mutualsslnegotiated"></a>MutualSslNegotiated  
 S tímto režimem ověřování ověřování klienta a služby pomocí certifikátů X.509. Element vazby zabezpečení je `SymmetricSecurityBindingElement` vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> metodu po hodnotu `true` je předán jako první parametr. Můžete také nastavit `authenticationMode` atribut `MutualSslNegotiated`.  
  
### <a name="secureconversation"></a>SecureConversation  
 Element vazby zabezpečení je `SymmetricSecurityBindingElement` vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> metoda. Tato metoda přebírá <xref:System.ServiceModel.Channels.SecurityBindingElement> jako parametr, který se používá během inicializace k navázání zabezpečené relace. Můžete také nastavit `authenticationMode` atribut `SecureConversation`.  
  
 Pokud není zadána žádná vazba bootstrap, pak bude `SspiNegotiated` režim ověřování se používá pro spuštění.  
  
### <a name="sspinegotiation"></a>Účel třídy SspiNegotiation  
 S tímto režimem ověřování protokolu vyjednávání slouží k provádění ověření klienta a serveru. Protokol Kerberos se používá v případě je to možné. v opačném případě se používá LanMan NT (NTLM). Element vazby zabezpečení je `SymmetricSecurityBindingElement` vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut `SspiNegotiated`.  
  
### <a name="sspinegotiatedovertransport"></a>SspiNegotiatedOverTransport  
 S tímto režimem ověřování protokolu vyjednávání slouží k provádění ověření klienta a serveru. Pokud je to možné; se používá protokol Kerberos v opačném případě je použit protokol NTLM. Výsledný token se zobrazí ve vrstvě protokolu SOAP jako potvrzující podpůrný token; To znamená, že token, který podepisuje podpis zprávy. Služba je kromě ověřit na transportní vrstvě pomocí certifikátu X.509. Element vazby zabezpečení je `TransportSecurityBindingElement` vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut `SspiNegotiatedOverTransport`.  
  
### <a name="usernameforcertificate"></a>UserNameForCertificate  
 S tímto režimem ověřování klient se ověří ve službě pomocí uživatelského jména Token, který se zobrazí jako podepsaný podpůrný token; ve vrstvě protokolu SOAP To znamená, že token, který je podepsaný podpis zprávy. Služba se ověřuje klienta pomocí certifikátu X.509. Element vazby zabezpečení je `SymmetricSecurityBindingElement` vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut `UserNameForCertificate`.  
  
 Pro `UserNameForCertificate` musí být v režimu ověřování, klient a služba WS-Security 1.1.  
  
### <a name="usernameforsslnegotiated"></a>UserNameForSslNegotiated  
 Tento režim ověřování, klient se ověří pomocí tokenu uživatelské jméno, které se zobrazí jako podepsaný podpůrný token; ve vrstvě protokolu SOAP To znamená, že token, který je podepsaný podpis zprávy. Služba je ověřený pomocí certifikátu X.509. Element vazby zabezpečení je `SymmetricSecurityBindingElement` vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut `UserNameForSslNegotiated`.  
  
### <a name="usernameovertransport"></a>UserNameOverTransport  
 S tímto režimem ověřování klient se ověří pomocí uživatelského jména Token, který se zobrazí jako podepsaný podpůrný token; ve vrstvě protokolu SOAP To znamená, že token, který je podepsaný podpis zprávy. Služba je ověřený pomocí certifikátu X.509 na transportní vrstvě. Element vazby zabezpečení je `TransportSecurityBindingElement` vrácených <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A> metoda. Můžete také nastavit `authenticationMode` atribut `UserNameOverTransport`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- [Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
