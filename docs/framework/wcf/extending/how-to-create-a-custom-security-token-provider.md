---
title: 'Postupy: vytvoření vlastního zprostředkovatele tokenů zabezpečení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
author: BrucePerlerMS
ms.openlocfilehash: 3e304aa12d5e1c7aaa992191e6ed9ed25b026f9f
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121191"
---
# <a name="how-to-create-a-custom-security-token-provider"></a>Postupy: vytvoření vlastního zprostředkovatele tokenů zabezpečení
Toto téma ukazuje, jak vytvořit nové typy tokenů s vlastního zprostředkovatele tokenů zabezpečení a jak integrovat Správce tokenů zabezpečení vlastního zprostředkovatele.  
  
> [!NOTE]
>  Vytvoření vlastního zprostředkovatele tokenů, pokud tokeny poskytované systémem najdete v <xref:System.IdentityModel.Tokens> oboru názvů neodpovídají vašim požadavkům.  
  
 Poskytovatel tokenu zabezpečení vytvoří reprezentaci token zabezpečení na základě informací v přihlašovacích údajů klienta nebo službě. Vlastního zprostředkovatele tokenů zabezpečení používané k zabezpečení Windows Communication Foundation (WCF), musíte vytvořit vlastní přihlašovací údaje a implementace Správce tokenů zabezpečení.  
  
 Další informace o vlastní přihlašovací údaje a Správce tokenů zabezpečení najdete v článku [návod: vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Další informace o pověření, token správce, zprostředkovatele a authenticator třídy zabezpečení, najdete v článku [architektury zabezpečení](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f).  
  
### <a name="to-create-a-custom-security-token-provider"></a>Chcete-li vytvořit vlastního zprostředkovatele tokenů zabezpečení  
  
1.  Definovat nové třídy odvozené od <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy.  
  
2.  Implementace <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metody. Metoda je zodpovědný za vytváření a vrácení instance tokenu zabezpečení. Následující příklad vytvoří třídu s názvem `MySecurityTokenProvider`a přepíše <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metoda vrátí instanci <xref:System.IdentityModel.Tokens.X509SecurityToken> třídy. Konstruktor třídy vyžaduje instanci <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy.  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a>Správce tokenů zabezpečení vlastní integrovat vlastního zprostředkovatele tokenů zabezpečení  
  
1.  Definovat nové třídy odvozené od <xref:System.IdentityModel.Selectors.SecurityTokenManager> třídy. (Následující příklad je odvozen od <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třída, která je odvozena z <xref:System.IdentityModel.Selectors.SecurityTokenManager> třídy.)  
  
2.  Přepsat <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metody, pokud se už je přepsaný.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> Metoda je zodpovědný za vrácení instance <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy vhodné <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametr předaný metodě rozhraním zabezpečení WCF. Upravte metodu vrátit implementaci poskytovatele tokenu, kterého vlastní bezpečnostní (vytvořený v předchozím postupu) při volání metody s parametrem tokenu zabezpečení. Další informace o správce tokenů zabezpečení, najdete v článku [návod: vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
3.  Přidat vlastní logiku do metody, který umožňuje vrátit vašeho vlastního zprostředkovatele tokenů zabezpečení na základě <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametru. Následující příklad vrátí vlastního zprostředkovatele tokenů zabezpečení, pokud jsou splněny požadavky tokenu. Požadavky zahrnují token zabezpečení X.509 a směr zpráv (že token, který se používá pro výstup zpráv). U všech ostatních případech volá kód základní třídy, chcete-li zachovat shodné chování poskytované systémem další požadavky tokenu zabezpečení.  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zobrazuje kompletní <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementace společně s odpovídající <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementace.  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.X509SecurityToken>  
 [Návod: Vytvoření vlastních přihlašovacích údajů klienta a služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Postupy: Vytvoření vlastních ověřovacích dat tokenu zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Architektura zabezpečení](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
