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
ms.openlocfilehash: e464aff46f311ede1cd629fb459ade9a6e627d59
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796957"
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a>Postupy: Použití samostatných certifikátů X.509 pro přihlašování a šifrování

V tomto tématu se dozvíte, jak nakonfigurovat Windows Communication Foundation (WCF) pro použití různých certifikátů pro podepisování a šifrování zpráv na straně klienta i služby.

Aby bylo možné používat samostatné certifikáty pro podepisování a šifrování, je nutné vytvořit vlastní klienta nebo pověření služby (nebo obojí), protože služba WCF neposkytuje rozhraní API pro nastavení více certifikátů klienta nebo služby. Kromě toho musí být k dispozici Správce tokenů zabezpečení, který využívá informace o více certifikátech, a vytvořit vhodného poskytovatele tokenu zabezpečení pro zadané použití klíče a směr zprávy.

Následující diagram znázorňuje používané hlavní třídy, třídy, ze kterých dědí (zobrazené pomocí šipky směřující nahoru), a návratové typy určitých metod a vlastností.

- `MyClientCredentials`je vlastní implementace <xref:System.ServiceModel.Description.ClientCredentials>.

  - Vlastnosti zobrazené v diagramu všechny návratové instance <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>.

  - Jeho metoda <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> vrátí `MyClientCredentialsSecurityTokenManager`instanci.

- `MyClientCredentialsSecurityTokenManager`je vlastní implementace <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.

  - Jeho metoda <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> vrátí <xref:System.IdentityModel.Selectors.X509SecurityTokenProvider>instanci.

![Graf znázorňující, jak se používají přihlašovací údaje klienta](./media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")

Další informace o vlastních přihlašovacích údajích [najdete v tématu Návod: Vytváření vlastních přihlašovacích údajů](walkthrough-creating-custom-client-and-service-credentials.md)klienta a služby.

Kromě toho musíte vytvořit vlastní ověřovatel identity a propojit ho s elementem vazby zabezpečení ve vlastní vazbě. Místo výchozích přihlašovacích údajů musíte použít taky vlastní přihlašovací údaje.

Následující diagram znázorňuje třídy, které jsou součástí vlastní vazby, a způsob, jakým je propojen vlastní ověřovatel identity. Existuje několik prvků vazby, z nichž všechny dědí z <xref:System.ServiceModel.Channels.BindingElement>. Má vlastnost, která vrací instanci `MyIdentityVerifier` , ze které je upravena. <xref:System.ServiceModel.Security.IdentityVerifier> <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>

![Graf znázorňující vlastní element vazby](./media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")

Další informace o vytvoření vlastního ověřovatele identity najdete v tématu How to: [Postupy: Vytvořte vlastního ověřovatele](how-to-create-a-custom-client-identity-verifier.md)identity klienta.

### <a name="to-use-separate-certificates-for-signing-and-encryption"></a>Použití oddělených certifikátů pro podepisování a šifrování

1. Definujte novou třídu přihlašovacích údajů klienta, která dědí <xref:System.ServiceModel.Description.ClientCredentials> z třídy. Implementujte čtyři nové vlastnosti, aby bylo možné specifikaci `ClientSigningCertificate`více `ClientEncryptingCertificate`certifikátů `ServiceSigningCertificate`:, `ServiceEncryptingCertificate`, a. Také přepište <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> metodu pro návrat instance vlastní <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy, která je definována v dalším kroku.

     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]

2. Definujte nového Správce tokenu zabezpečení klienta, který dědí z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy. Přepsáním <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> metody vytvořte vhodného poskytovatele tokenu zabezpečení. Parametr (a <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) poskytuje směr zprávy a použití klíče. `requirement`

     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]

3. Definujte novou třídu přihlašovacích údajů služby, která dědí <xref:System.ServiceModel.Description.ServiceCredentials> z třídy. Implementujte čtyři nové vlastnosti, aby bylo možné specifikaci `ClientSigningCertificate`více `ClientEncryptingCertificate`certifikátů `ServiceSigningCertificate`:, `ServiceEncryptingCertificate`, a. Také přepište <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> metodu pro návrat instance vlastní <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídy, která je definována v dalším kroku.

     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]

4. Definujte nového Správce tokenu zabezpečení služby, který dědí z <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> třídy. Přepište <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> metodu pro vytvoření vhodného poskytovatele tokenu zabezpečení pro daný směr a použití klíče zprávy.

     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]

### <a name="to-use-multiple-certificates-on-the-client"></a>Použití více certifikátů na klientovi

1. Vytvořte vlastní vazbu. Element vazby zabezpečení musí fungovat v duplexovém režimu, aby bylo možné pro žádosti a odpovědi použít různé zprostředkovatele tokenů zabezpečení. Jedním ze způsobů, jak to provést, je použít duplexní přenos, který je možné <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> použít, jak je znázorněno v následujícím kódu. Propojte přizpůsobenou <xref:System.ServiceModel.Security.IdentityVerifier> definici, která je definována v dalším kroku elementu vazby zabezpečení. Nahraďte výchozí pověření klienta vlastními přihlašovacími údaji klienta, které jste vytvořili dříve.

     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]

2. Definujte vlastní <xref:System.ServiceModel.Security.IdentityVerifier>. Služba má více identit, protože k zašifrování žádosti a k podepsání odpovědi slouží jiné certifikáty.

    > [!NOTE]
    > V následující ukázce poskytnuté vlastní ověřovatel identity neprovádí žádnou kontrolu identity koncového bodu pro demonstrační účely. Toto není doporučený postup pro produkční kód.

     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]

### <a name="to-use-multiple-certificates-on-the-service"></a>Používání více certifikátů v rámci služby

1. Vytvořte vlastní vazbu. Element vazby zabezpečení musí fungovat v duplexovém režimu, aby bylo možné pro žádosti a odpovědi použít různé zprostředkovatele tokenů zabezpečení. Stejně jako u klienta použijte duplexní přenos nebo použití <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> , jak je znázorněno v následujícím kódu. Nahraďte výchozí přihlašovací údaje služby dříve vytvořenými vlastními pověřeními služby.

     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [Návod: Vytváření vlastních přihlašovacích údajů klienta a služby](walkthrough-creating-custom-client-and-service-credentials.md)
