---
title: "Postupy: vytvoření zprostředkovatele tokenu vlastní zabezpečení"
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
helpviewer_keywords: security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 0bf616b1af46c62166b0430c1b67b3a97f0613ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-security-token-provider"></a>Postupy: vytvoření zprostředkovatele tokenu vlastní zabezpečení
Toto téma ukazuje, jak vytvořit nové typy tokenů s poskytovatele tokenu vlastní zabezpečení a postup pro integraci zprostředkovatele tokenu správce vlastní zabezpečení.  
  
> [!NOTE]
>  Vytvořit vlastní zprostředkovatele tokenu, pokud v nalezen tokeny poskytované systémem <xref:System.IdentityModel.Tokens> obor názvů se neshodují vašim požadavkům.  
  
 Poskytovatele tokenu zabezpečení slouží k vytvoření tokenu vyjádření zabezpečení na základě informací v klienta služby Windows nebo pověření. Použití zprostředkovatele tokenu vlastní zabezpečení v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zabezpečení, musíte vytvořit vlastní pověření a implementace Správce tokenu zabezpečení.  
  
 Další informace o vlastní pověření a Správce tokenů zabezpečení najdete v článku [návod: vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Další informace o pověření zabezpečení tokenu správce, zprostředkovatele a ověřovací třídách naleznete v tématu [Architektura zabezpečení](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f).  
  
### <a name="to-create-a-custom-security-token-provider"></a>Chcete-li vytvořit poskytovatele tokenu vlastní zabezpečení  
  
1.  Definovat nové třídy odvozené od <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy.  
  
2.  Implementace <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metoda. Metoda odpovídá za vytváření a vrací instanci třídy token zabezpečení. Následující příklad vytvoří třídu s názvem `MySecurityTokenProvider`a přepíše <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metoda vrátí instanci <xref:System.IdentityModel.Tokens.X509SecurityToken> třídy. Konstruktoru třídy vyžaduje instanci systému <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy.  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a>Pro integraci poskytovatele tokenu zabezpečení vlastní Správce tokenů vlastní zabezpečení  
  
1.  Definovat nové třídy odvozené od <xref:System.IdentityModel.Selectors.SecurityTokenManager> třídy. (Následující příklad je odvozena z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třída, která je odvozena z <xref:System.IdentityModel.Selectors.SecurityTokenManager> třídy.)  
  
2.  Přepsání <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metoda, pokud již není přepsána.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> Metoda odpovídá za vrací instanci třídy <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třída vhodné <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametr předaný metodě podle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework zabezpečení. Změňte metodu vrátit implementaci zprostředkovatele tokenu vlastní zabezpečení (vytvořený v předchozím postupu) Pokud je metoda volána s parametrem tokenu příslušné zabezpečení. Další informace o tokenu správce zabezpečení najdete v tématu [návod: vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
3.  Přidat vlastní logiky do způsob ho vrátit vašeho poskytovatele tokenu vlastní zabezpečení na základě povolení <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametr. Následující příklad vrátí poskytovatele tokenu vlastní zabezpečení, pokud jsou splněny požadavky na tokenu. Požadavky na zahrnují token zabezpečení X.509 a směr zprávy (aby token se používá pro výstup zpráv). Všech ostatních případech kód zavolá základní třídy, chcete-li udržovat poskytované systémem chování pro jiné požadavky na tokenu zabezpečení.  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a>Příklad  
 Následující příklad zobrazuje úplná <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementace spolu s odpovídající <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementace.  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.X509SecurityToken>  
 [Návod: Vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Postupy: Vytvoření ověřovacího modulu tokenu vlastní zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Architektura zabezpečení](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)
