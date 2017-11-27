---
title: "Postupy: Použití samostatných certifikátů X.509 pro přihlašování a šifrování"
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
helpviewer_keywords:
- WCF, extensibility
- ClientCredentials class
- ClientCredentialsSecurityTokenManager class
ms.assetid: 0b06ce4e-7835-4d82-8baf-d525c71a0e49
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 51ee500b048bbd8ba2b26fdd993a18663bd433c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a>Postupy: Použití samostatných certifikátů X.509 pro přihlašování a šifrování
Toto téma ukazuje, jak nakonfigurovat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] používat různé certifikáty pro podepisování zpráv a šifrování na klientovi a služby.  
  
 Chcete-li samostatný certifikátů, který se má použít pro podepisování a šifrování, vlastní klienta nebo služby přihlašovací údaje (nebo obě) musí vytvořit, protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] neposkytuje rozhraní API nastavit několik certifikátů klienta nebo služby. Kromě toho zabezpečení Správce tokenu musí být za předpokladu, že využívat více certifikátů informace a vytvořte poskytovatele tokenu příslušné zabezpečení pro zadaný klíče směr využití a zprávy.  
  
 Následující diagram znázorňuje hlavní třídy, třídy dědí z (viz šipkou ukazující vzhůru) a návratové typy určité metod a vlastností.  
  
-   `MyClientCredentials`je vlastní implementace <xref:System.ServiceModel.Description.ClientCredentials>.  
  
    -   Jeho vlastnosti zobrazené v diagramu všechny návratové instancí <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>.  
  
    -   Jeho metoda <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> vrací instanci třídy `MyClientCredentialsSecurityTokenManager`.  
  
-   `MyClientCredentialsSecurityTokenManager`je vlastní implementace <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
    -   Jeho metoda <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> vrací instanci třídy <xref:System.IdentityModel.Selectors.X509SecurityTokenProvider>.  
  
 ![Graf zobrazující použití pověření klienta](../../../../docs/framework/wcf/extending/media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]vlastní pověření, najdete v části [návod: vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Kromě toho musíte vytvořit vlastní identitu ověřovatele a odkaz na element vazby a zabezpečení v vlastní vazby. Vlastní pověření musí používají taky místo výchozích pověření.  
  
 Následující diagram znázorňuje tříd zahrnutých v vlastní vazby a jak je propojena ověřovatele vlastní identitu. Existuje několik vazby související prvky, které dědí <xref:System.ServiceModel.Channels.BindingElement>. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> Má <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> vlastnosti, která vrací instanci třídy <xref:System.ServiceModel.Security.IdentityVerifier>, ze kterého `MyIdentityVerifier` přizpůsobit.  
  
 ![Graf zobrazující element vlastní vazby](../../../../docs/framework/wcf/extending/media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]vytváření ověřovatel vlastní identity, najdete v části Postup: [postupy: vytvoření vlastního ověřování Identity klienta](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md).  
  
### <a name="to-use-separate-certificates-for-signing-and-encryption"></a>Použití samostatných certifikátů pro podepisování a šifrování  
  
1.  Zadejte novou třídu pověření klienta, která dědí z <xref:System.ServiceModel.Description.ClientCredentials> třídy. Implementace čtyři nové vlastnosti umožňující specifikaci více certifikátů: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, a `ServiceEncryptingCertificate`. Také přepsat <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> metoda vrátí instanci vlastní <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídu, která je definována v dalším kroku.  
  
     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]  
  
2.  Definování nového klienta zabezpečení tokenu správce která dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy. Přepsání <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> metodu pro vytvoření poskytovatele tokenu příslušné zabezpečení. `requirement` Parametr ( <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) poskytuje zpráva směr a klíč využití.  
  
     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]  
  
3.  Zadejte novou třídu přihlašovací údaje služby, která dědí z <xref:System.ServiceModel.Description.ServiceCredentials> třídy. Implementace čtyři nové vlastnosti umožňující specifikaci více certifikátů: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, a `ServiceEncryptingCertificate`. Také přepsat <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> metoda vrátí instanci vlastní <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídu, která je definována v dalším kroku.  
  
     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]  
  
4.  Definování nové služby Správce tokenů zabezpečení která dědí z <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídy. Přepsání <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> metodu pro vytvoření poskytovatele tokenu příslušná bezpečnostní danou zprávu předané směr a klíč využití.  
  
     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]  
  
### <a name="to-use-multiple-certificates-on-the-client"></a>Používání více certifikátů na straně klienta  
  
1.  Vytvoření vlastní vazby. Element vazby zabezpečení musí fungovat v duplexní režim umožňující jiné bezpečnostní poskytovatele tokenů, aby byly pro požadavky a odpovědi. Jeden ze způsobů, jak provést toto je podporující duplexní režim přenosu nebo používat <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> jak je znázorněno v následujícím kódu. Odkaz vlastní <xref:System.ServiceModel.Security.IdentityVerifier> který je definován v dalším kroku k prvku vazby zabezpečení. Výchozí pověření klienta nahraďte vlastní klientská přihlašovací údaje předtím vytvořili.  
  
     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]  
  
2.  Definovat vlastní <xref:System.ServiceModel.Security.IdentityVerifier>. Služba má více identit, protože různé certifikáty se používají k šifrování žádosti a podepsat odpovědi.  
  
    > [!NOTE]
    >  V následující ukázce ověřovatele zadaný vlastní identitu neprovede žádné identitu koncového bodu kontrola pro demonstrační účely. Postup pro kód produkční toto se nedoporučuje.  
  
     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]  
  
### <a name="to-use-multiple-certificates-on-the-service"></a>Používání více certifikátů ve službě  
  
1.  Vytvoření vlastní vazby. Element vazby zabezpečení musí fungovat v duplexní režim umožňující jiné bezpečnostní poskytovatele tokenů, aby byly pro požadavky a odpovědi. Jako s klientem, použijte podporující duplexní režim přenosu nebo použijte <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> jak je znázorněno v následujícím kódu. Nahraďte přihlašovací údaje služby výchozí přihlašovací údaje služby s vlastním nastavením vytvořili.  
  
     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>  
 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>  
 <xref:System.ServiceModel.Security.IdentityVerifier>  
 [Návod: Vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
