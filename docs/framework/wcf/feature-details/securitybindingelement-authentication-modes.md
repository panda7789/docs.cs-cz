---
title: "Režimy ověřování SecurityBindingElement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 05b44d9972a393b36a97fd5afcb6581229332df9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="securitybindingelement-authentication-modes"></a>Režimy ověřování SecurityBindingElement
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]poskytuje několik režimy, které služby a klienti ověřování jednu na druhou. Můžete vytvořit bezpečnostní prvky vazeb pro tyto režimy ověřování pomocí statické metody <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy nebo prostřednictvím konfigurace. Toto téma stručně popisuje režimy ověřování 18.  
  
 Příklad použití elementu pro jeden z režimů ověřování, naleznete v části [postupy: vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="basic-configuration-programming"></a>Základní konfigurace programování  
 Následující postup popisuje, jak nastavit režim ověřování v konfiguračním souboru.  
  
#### <a name="to-set-the-authentication-mode-in-configuration"></a>Chcete-li nastavit režim ověřování v konfiguraci  
  
1.  K [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu, přidejte [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2.  Jako podřízený element přidat [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu, který chcete `<customBinding>` elementu.  
  
3.  Přidat `<security>` elementu, který chcete `<binding>` elementu.  
  
4.  Nastavte `authenticationMode` atribut na jednu z hodnot popsané dole. Například následující kód nastaví režim na `AnonymousForCertificate`.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SecureCustomBinding">  
         <security authenticationMode ="AnonymousForCertificate" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
#### <a name="to-set-the-mode-programmatically"></a>Nastavení režimu prostřednictvím kódu programu  
  
1.  Určení návratový typ, který může být jedna z následujících: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>, nebo <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2.  Volání vhodné statické metody <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy. Například následující kód volání <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> metoda.  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3.  Pro vytvoření vlastní vazby pomocí elementu vazby. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="mode-descriptions"></a>Popisy režimu  
  
### <a name="anonymousforcertificate"></a>AnonymousForCertificate  
 U tento režim ověřování klienta je anonymní a službu ověření pomocí certifikátu X.509. Element vazby zabezpečení <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut <`security`> elementu, který chcete `AnonymousForCertificate`.  
  
### <a name="anonymousforsslnegotiated"></a>AnonymousForSslNegotiated  
 U tento režim ověřování klienta je anonymní a službu ověření pomocí certifikátu X.509, který je vyjednal za běhu. Element vazby zabezpečení <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácený <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> metoda při hodnotu `false` byla předána pro první parametr. Alternativně nastavte `authenticationMode` atribut `AnonymousForSslNegotiated`.  
  
### <a name="certificateovertransport"></a>CertificateOverTransport  
 Tento režim ověřování klient se ověří pomocí certifikát X.509, který se zobrazí jako tokenu či identifikaci podpůrné; ve vrstvě protokolu SOAP To znamená, token, který podepisuje podpis zprávy. Služba je ověřen pomocí certifikátu X.509. certifikát v přenosové vrstvě. Element vazby zabezpečení <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut `CertificateOverTransport`.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Tento režim ověřování klienta neověřuje služby, jako například; Klient místo toho přihlásí k služby tokenů zabezpečení a obdrží token SAML, která potom nabídne k serveru k prokázání své znalosti o sdílený klíč. Služba není ověřen klientovi, jako například ale služby tokenů zabezpečení tak, aby pouze služby může dešifrovat klíč zašifruje sdílený klíč jako součást vydaných tokenu. Element vazby zabezpečení <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut `IssuedToken`.  
  
### <a name="issuedtokenforcertificate"></a>IssuedTokenForCertificate  
 Tento režim ověřování klienta neověřuje služby, jako například; Klient místo toho přihlásí k služby tokenů zabezpečení a obdrží token SAML, která potom nabídne k serveru k prokázání své znalosti o sdílený klíč. Vystavený token se zobrazí ve vrstvě protokolu SOAP jako token podporující potvrzení nebo token nosiče; To znamená, token, který podepisuje podpis zprávy. Služba se ověřuje na klienta pomocí certifikátu X.509. Element vazby zabezpečení <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut `IssuedTokenForCertificate`.  
  
### <a name="issuedtokenforsslnegotiated"></a>IssuedTokenForSslNegotiated  
 Tento režim ověřování klienta neověřuje služby, jako například; Klient místo toho přihlásí k služby tokenů zabezpečení a obdrží token SAML, která potom nabídne k serveru k prokázání své znalosti o sdílený klíč. Vystavený token se zobrazí ve vrstvě protokolu SOAP jako token podporující potvrzení nebo token nosiče; To znamená, token, který podepisuje podpis zprávy. Služba je ověřen pomocí certifikátu X.509. Element vazby zabezpečení <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut `IssuedTokenForSslnegotiated`.  
  
### <a name="issuedtokenovertransport"></a>IssuedTokenOverTransport  
 Tento režim ověřování klienta neověřuje služby, jako například; Klient místo toho přihlásí k služby tokenů zabezpečení a obdrží token SAML, která potom nabídne k serveru k prokázání své znalosti o sdílený klíč. Vystavený token se zobrazí ve vrstvě protokolu SOAP jako token podporující potvrzení nebo token nosiče; To znamená, token, který podepisuje podpis zprávy. Služba je ověřen pomocí certifikátu X.509. certifikát v přenosové vrstvě. Element vazby zabezpečení `TransportSecurityBindingElement` vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut `IssuedTokenOverTransport`.  
  
### <a name="kerberos"></a>Pomocí protokolu Kerberos  
 Klient se ověří do služby pomocí lístek protokolu Kerberos s Tento režim ověřování. Tento stejný lístek taky poskytuje ověřování serveru. Element vazby zabezpečení `SymmetricSecurityBindingElement` vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut `Kerberos`.  
  
> [!NOTE]
>  Chcete-li použít tento režim ověřování, musí být přidružen hlavní název služby (SPN) účtu služby. K tomu, spusťte službu pod účtem síťové služby nebo účtu LOCAL SYSTEM. Chcete-li vytvořit název SPN pro účet služby můžete taky pomocí nástroje SetSpn.exe. V obou případech musí klient použít správný název SPN [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element, nebo pomocí <xref:System.ServiceModel.EndpointAddress> konstruktor. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Služby identit a ověření](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
> [!NOTE]
>  Když `Kerberos` se používá režim ověřování, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> a <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> úrovní zosobnění nejsou podporovány.  
  
### <a name="kerberosovertransport"></a>KerberosOverTransport  
 Klient se ověří do služby pomocí lístek protokolu Kerberos s Tento režim ověřování. Token protokolu Kerberos se zobrazí ve vrstvě protokolu SOAP jako tokenu či identifikaci podpůrné; To znamená, token, který podepisuje podpis zprávy. Služba je ověřen pomocí certifikátu X.509. certifikát v přenosové vrstvě. Element vazby zabezpečení `TransportSecurityBindingElement` vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut `KerberosOverTransport`.  
  
> [!NOTE]
>  Chcete-li použít tento režim ověřování, musí být přidružen název SPN účtu služby. K tomu, spusťte službu pod účtem síťové služby nebo účtu LOCAL SYSTEM. Chcete-li vytvořit název SPN pro účet služby můžete taky pomocí nástroje SetSpn.exe. V obou případech musí klient použít správný název SPN [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) element, nebo pomocí <xref:System.ServiceModel.EndpointAddress> konstruktor. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Služby identit a ověření](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
### <a name="mutualcertificate"></a>MutualCertificate  
 Tento režim ověřování klient se ověří pomocí certifikát X.509, který se zobrazí jako tokenu či identifikaci podpůrné; ve vrstvě protokolu SOAP To znamená, token, který podepisuje podpis zprávy. Služba je také ověřit pomocí certifikátu X.509. Element vazby zabezpečení `SymmetricSecurityBindingElement` vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut `MutualCertificate`.  
  
### <a name="mutualcertificateduplex"></a>MutualCertificateDuplex  
 Tento režim ověřování klient se ověří pomocí certifikát X.509, který se zobrazí jako tokenu či identifikaci podpůrné; ve vrstvě protokolu SOAP To znamená, token, který podepisuje podpis zprávy. Služba je také ověřit pomocí certifikátu X.509. Vazba není `AsymmetricSecurityBindingElement` vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut `MutualCertificateDuplex`.  
  
### <a name="mutalsslnegotiation"></a>MutalSslNegotiation  
 S Tento režim ověřování ověřování klienta a služby pomocí certifikátů X.509. Element vazby zabezpečení `SymmetricSecurityBindingElement` vrácený <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> metoda při hodnotu `true` byla předána pro první parametr. Alternativně nastavte `authenticationMode` atribut `MutualSslNegotiated`.  
  
### <a name="secureconversation"></a>SecureConversation  
 Element vazby zabezpečení `SymmetricSecurityBindingElement` vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> metoda. Tato metoda přebírá <xref:System.ServiceModel.Channels.SecurityBindingElement> jako parametr, který se používá během inicializace k navázání zabezpečené relace. Alternativně nastavte `authenticationMode` atribut `SecureConversation`.  
  
 Pokud je zadána žádná vazba bootstrap, pak se `SspiNegotiated` režim ověřování se používá pro bootstrap.  
  
### <a name="sspinegotiation"></a>Účel třídy SspiNegotiation  
 S Tento režim ověřování vyjednávání protokolu slouží k provádění ověření klienta a serveru. Pokud je to možné; používá protokol Kerberos jinak je použít LanMan NT (NTLM). Element vazby zabezpečení `SymmetricSecurityBindingElement` vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut `SspiNegotiated`.  
  
### <a name="sspinegotiatedovertransport"></a>SspiNegotiatedOverTransport  
 S Tento režim ověřování vyjednávání protokolu slouží k provádění ověření klienta a serveru. Pokud je to možné; se používá protokol Kerberos jinak se používá protokol NTLM. Výsledný token se zobrazí ve vrstvě protokolu SOAP jako tokenu či identifikaci podpůrné; To znamená, token, který podepisuje podpis zprávy. Služba je kromě ověřit v přenosové vrstvě certifikát X.509. Element vazby zabezpečení `TransportSecurityBindingElement` vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut `SspiNegotiatedOverTransport`.  
  
### <a name="usernameforcertificate"></a>UserNameForCertificate  
 Tento režim ověřování klient se ověří do služby pomocí uživatelského jména Token, který se zobrazí jako podepsaný token; ve vrstvě protokolu SOAP To znamená, token, který je podepsaný podpis zprávy. Služba se ověřuje na klienta pomocí certifikátu X.509. Element vazby zabezpečení `SymmetricSecurityBindingElement` vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut `UserNameForCertificate`.  
  
 Pro `UserNameForCertificate` režim ověřování, klient a služba musí používat WS-zabezpečení 1.1.  
  
### <a name="usernameforsslnegotiated"></a>UserNameForSslNegotiated  
 Tento režim ověřování je klient se ověří pomocí uživatelského jména Token, který se zobrazí jako podepsaný token; ve vrstvě protokolu SOAP To znamená, token, který je podepsaný podpis zprávy. Služba je ověřen pomocí certifikátu X.509. Element vazby zabezpečení `SymmetricSecurityBindingElement` vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut `UserNameForSslNegotiated`.  
  
### <a name="usernameovertransport"></a>UserNameOverTransport  
 Tento režim ověřování klient se ověří pomocí uživatelského jména Token, který se zobrazí jako podepsaný token; ve vrstvě protokolu SOAP To znamená, token, který je podepsaný podpis zprávy. Služba je ověřen pomocí certifikátu X.509. certifikát v přenosové vrstvě. Element vazby zabezpečení `TransportSecurityBindingElement` vrácené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A> metoda. Alternativně nastavte `authenticationMode` atribut `UserNameOverTransport`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 [Postupy: Vytvoření SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
