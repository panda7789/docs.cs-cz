---
title: 'Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
ms.openlocfilehash: 1ca12274358ed6de475b0c2b8b47dd5cb52e941e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797029"
---
# <a name="how-to-create-a-custom-security-token-provider"></a>Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení
V tomto tématu se dozvíte, jak vytvořit nové typy tokenů s vlastním poskytovatelem tokenů zabezpečení a jak integrovat zprostředkovatele s vlastním správcem tokenů zabezpečení.  
  
> [!NOTE]
> Pokud tokeny poskytnuté systémem v <xref:System.IdentityModel.Tokens> oboru názvů neodpovídají vašim požadavkům, vytvořte vlastního poskytovatele tokenů.  
  
 Poskytovatel tokenu zabezpečení vytvoří reprezentaci tokenu zabezpečení na základě informací v pověření klienta nebo služby. Pokud chcete použít vlastního poskytovatele tokenu zabezpečení ve službě Windows Communication Foundation (WCF), musíte vytvořit vlastní pověření a implementace správce tokenů zabezpečení.  
  
 Další informace o vlastních přihlašovacích údajích a správci tokenů [zabezpečení najdete v tomto návodu: Vytváření vlastních přihlašovacích údajů](walkthrough-creating-custom-client-and-service-credentials.md)klienta a služby.  
  
### <a name="to-create-a-custom-security-token-provider"></a>Vytvoření vlastního zprostředkovatele tokenů zabezpečení  
  
1. Definujte novou třídu odvozenou z <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy.  
  
2. Implementujte <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metodu. Metoda zodpovídá za vytváření a vracení instance tokenu zabezpečení. Následující příklad vytvoří třídu s názvem `MySecurityTokenProvider`a <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> přepíše metodu pro <xref:System.IdentityModel.Tokens.X509SecurityToken> vrácení instance třídy. Konstruktor třídy vyžaduje instanci <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy.  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a>Integrace vlastního zprostředkovatele tokenů zabezpečení s vlastním správcem tokenů zabezpečení  
  
1. Definujte novou třídu odvozenou z <xref:System.IdentityModel.Selectors.SecurityTokenManager> třídy. (Následující příklad je odvozen od <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třídy, která je odvozena <xref:System.IdentityModel.Selectors.SecurityTokenManager> od třídy.)  
  
2. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> Přepsat metodu, pokud již není přepsána.  
  
     Metoda zodpovídá za vrácení instance <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy odpovídající <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametru předanému do metody v rámci architektury zabezpečení WCF. <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> Upravte metodu tak, aby vracela vlastní implementaci poskytovatele tokenu zabezpečení (vytvořenou v předchozím postupu), pokud je metoda volána s odpovídajícím parametrem tokenu zabezpečení. Další informace o Správci tokenů zabezpečení najdete [v návodu: Vytváření vlastních přihlašovacích údajů](walkthrough-creating-custom-client-and-service-credentials.md)klienta a služby.  
  
3. Přidejte vlastní logiku do metody, která umožňuje vrátit vlastního poskytovatele tokenu zabezpečení na základě <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametru. Následující ukázka vrátí vlastního poskytovatele tokenu zabezpečení, pokud jsou splněny požadavky tokenu. Požadavky zahrnují token zabezpečení X. 509 a směr zprávy (který token slouží pro výstup zprávy). Pro všechny ostatní případy kód volá základní třídu pro zachování chování poskytovaného systémem pro jiné požadavky na tokeny zabezpečení.  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je uvedena <xref:System.IdentityModel.Selectors.SecurityTokenProvider> kompletní implementace spolu s odpovídající <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementací.  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Selectors.SecurityTokenProvider>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.IdentityModel.Tokens.X509SecurityToken>
- [Návod: Vytváření vlastních přihlašovacích údajů klienta a služby](walkthrough-creating-custom-client-and-service-credentials.md)
- [Postupy: Vytvořit vlastní ověřovací data tokenu zabezpečení](how-to-create-a-custom-security-token-authenticator.md)
