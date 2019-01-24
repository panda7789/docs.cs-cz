---
title: 'Postupy: Použití samostatných certifikátů X.509 pro přihlašování a šifrování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, extensibility
- ClientCredentials class
- ClientCredentialsSecurityTokenManager class
ms.assetid: 0b06ce4e-7835-4d82-8baf-d525c71a0e49
ms.openlocfilehash: 6910b7abeb6a97cce1da9655fdab99b5295cc346
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500483"
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a>Postupy: Použití samostatných certifikátů X.509 pro přihlašování a šifrování
Toto téma ukazuje, jak konfigurovat Windows Communication Foundation (WCF) používat různé certifikáty pro podepisování zpráv a šifrování na klienta a služby.  
  
 Pokud chcete povolit samostatné certifikáty pro podepisování a šifrování, vlastní klienta služby přihlašovací údaje (nebo obojí) musí vytvořit, protože WCF neposkytuje rozhraní API pro nastavení více certifikátů klienta nebo službě. Kromě toho zabezpečení Správce tokenů musí být zadán využívat více certifikátů informace a vytvořit poskytovatele tokenů zabezpečení pro zadanou klíče směr využití a zprávy.  
  
 Následující diagram znázorňuje hlavní třídy, třídy dědí z (zobrazují se šipkou ukazující vzhůru) a návratové typy některých metod a vlastností.  
  
-   `MyClientCredentials` je vlastní implementace <xref:System.ServiceModel.Description.ClientCredentials>.  
  
    -   Její vlastnosti, které je zobrazeno na diagramu všechny návratové výskyty <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>.  
  
    -   Jeho metoda <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> vrátí instanci `MyClientCredentialsSecurityTokenManager`.  
  
-   `MyClientCredentialsSecurityTokenManager` je vlastní implementace <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
    -   Jeho metoda <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> vrátí instanci <xref:System.IdentityModel.Selectors.X509SecurityTokenProvider>.  
  
 ![Graf zobrazující, jak se používají přihlašovací údaje pro klienta](../../../../docs/framework/wcf/extending/media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")  
  
 Další informace o vlastní přihlašovací údaje, najdete v části [názorný postup: Vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Kromě toho musíte vytvořit ověřovatele vlastní identity a odkaz na element vazby zabezpečení ve vlastní vazby. Také je nutné použít vlastní přihlašovací údaje místo výchozí přihlašovací údaje.  
  
 Následující diagram znázorňuje třídy používané ve vlastní vazby, a jak je propojena ověřovatele vlastní identity. Existuje několik vazeb související prvky, které dědí <xref:System.ServiceModel.Channels.BindingElement>. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> Má <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> vlastnost, která vrací instanci <xref:System.ServiceModel.Security.IdentityVerifier>, ze kterého `MyIdentityVerifier` upravíte.  
  
 ![Graf zobrazující vlastní prvek vazby](../../../../docs/framework/wcf/extending/media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")  
  
 Další informace o vytváření ověřovatele vlastní identity, naleznete v tématu Postupy: [Postupy: Vytvoření vlastního ověřovatele Identity](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md).  
  
### <a name="to-use-separate-certificates-for-signing-and-encryption"></a>Použití samostatných certifikátů pro podepisování a šifrování  
  
1.  Definovat novou třídu přihlašovací údaje klienta, která dědí z <xref:System.ServiceModel.Description.ClientCredentials> třídy. Implementace čtyři nové vlastnosti umožňující specifikaci více certifikátů: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, a `ServiceEncryptingCertificate`. Také přepsat <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> metoda vrátí instanci upravené <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídu, která je definována v dalším kroku.  
  
     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]  
  
2.  Definování nového klienta Správce tokenů zabezpečení, která dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy. Přepsat <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> metodu pro vytvoření poskytovatele tokenu zabezpečení. `requirement` Parametr ( <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) poskytuje využití směr a klíč zprávy.  
  
     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]  
  
3.  Definovat novou třídu přihlašovací údaje služby, která dědí z <xref:System.ServiceModel.Description.ServiceCredentials> třídy. Implementace čtyři nové vlastnosti umožňující specifikaci více certifikátů: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, a `ServiceEncryptingCertificate`. Také přepsat <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> metoda vrátí instanci upravené <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídu, která je definována v dalším kroku.  
  
     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]  
  
4.  Definování nové služby Správce tokenů zabezpečení, která dědí z <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídy. Přepsat <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> metodu pro vytvoření poskytovatele tokenu zabezpečení zadaný směr a klíč využití předané zprávy.  
  
     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]  
  
### <a name="to-use-multiple-certificates-on-the-client"></a>Použití více certifikátů na straně klienta  
  
1.  Vytvoření vlastní vazby. Element vazby zabezpečení musí pracovat v duplexním režimu povolit zabezpečení poskytovatele tokenů bude k dispozici pro požadavky a odpovědi. Můžete provést například jde používat podporující duplexní režim přenosu ani pomocí <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> jak je znázorněno v následujícím kódu. Odkaz vlastní <xref:System.ServiceModel.Security.IdentityVerifier> který je definován v dalším kroku k prvku vazby zabezpečení. Nahraďte výchozí pověření klienta s přihlašovacími údaji přizpůsobené klientů předtím vytvořili.  
  
     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]  
  
2.  Definování vlastní <xref:System.ServiceModel.Security.IdentityVerifier>. Služba má více identit, protože různé certifikáty se používají k zašifrování žádosti a podepsat odpověď.  
  
    > [!NOTE]
    >  V následující ukázce ověřovatele zadaná vlastní identity neprovádí žádné identitě koncového bodu kontrolu pro demonstrační účely. Toto nastavení nedoporučujeme normy pro produkčního kódu.  
  
     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]  
  
### <a name="to-use-multiple-certificates-on-the-service"></a>Použití více certifikátů ve službě  
  
1.  Vytvoření vlastní vazby. Element vazby zabezpečení musí pracovat v duplexním režimu povolit zabezpečení poskytovatele tokenů bude k dispozici pro požadavky a odpovědi. S klientem, používejte podporující duplexní přenos nebo používáte <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> jak je znázorněno v následujícím kódu. Nahraďte výchozí pověření služby s přihlašovacími údaji služby předtím vytvořili.  
  
     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [Návod: Vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
