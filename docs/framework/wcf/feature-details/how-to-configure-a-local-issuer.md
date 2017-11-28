---
title: "Postupy: Konfigurace místního vystavitele"
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
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 413f534bacd1f5551cd3b5d7c83e3722104fa0c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-a-local-issuer"></a>Postupy: Konfigurace místního vystavitele
Toto téma popisuje postup konfigurace klienta pro použití místního vystavitele pro vydané tokeny.  
  
 Často Pokud klient komunikuje s federované služby, služby určuje adresu tokenu služby, kterou je očekáván k vydání tokenu klient použije k vlastnímu ověření federované služby zabezpečení. V některých situacích může být klient nakonfigurován pro použití *místního vystavitele*.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]používá místního vystavitele v případech, kdy je na adresu vystavitele federované vazby http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous nebo `null`. V takových případech musíte nakonfigurovat <xref:System.ServiceModel.Description.ClientCredentials> s adresou místního vystavitele a vazby, které používají ke komunikaci s této vystavitele.  
  
> [!NOTE]
>  Pokud <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> vlastnost `ClientCredentials` třída je nastaven na `true`, není zadána adresa místního vystavitele a vystavitele adresu zadanou [ \<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) či jiné federované vazby je http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self, http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous, nebo je `null`, pak Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] vystavitele se používá.  
  
### <a name="to-configure-the-local-issuer-in-code"></a>Konfigurace místního vystavitele v kódu  
  
1.  Vytvoření proměnné typu<xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
2.  Nastavte proměnnou na instance, kterou vrátil <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> vlastnost `ClientCredentials` třídy. Tato instance je vrácený <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost klienta (zděděno z <xref:System.ServiceModel.ClientBase%601>) nebo <xref:System.ServiceModel.ChannelFactory.Credentials%2A> vlastnost <xref:System.ServiceModel.ChannelFactory>:  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  Nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> vlastnost novou instanci třídy <xref:System.ServiceModel.EndpointAddress>, s na adresu místního vystavitele jako argument konstruktoru.  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     Alternativně vytvořte novou <xref:System.Uri> instance jako argument konstruktoru.  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     `addressHeaders` Parametr je pole <xref:System.ServiceModel.Channels.AddressHeader> instance, jak je vidět.  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  Nastavit vazby pro místního vystavitele pomocí <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> vlastnost.  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  Volitelné. Přidání chování nakonfigurovaný koncový bod pro místního vystavitele přidáním takové chování do kolekce vrácené <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> vlastnost.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a>Konfigurace místního vystavitele v konfiguraci  
  
1.  Vytvoření [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) jako podřízený element [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element, který je sám podřízeným [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element v chování koncového bodu.  
  
2.  Nastavte `address` atribut na adresu místního vystavitele, který bude přijímat žádosti o tokeny.  
  
3.  Nastavte `binding` a `bindingConfiguration` atributy hodnoty, které odkazují na odpovídající vazby použít při komunikaci s koncovým bodem místního vystavitele.  
  
4.  Volitelné. Nastavte [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) jako podřízený element <`localIssuer`> elementu a zadejte informace o identitě pro místního vystavitele.  
  
5.  Volitelné. Nastavte [ \<hlavičky >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) jako podřízený element <`localIssuer`> elementu a zadejte další hlavičky, které jsou požadovány k správně adres místního vystavitele.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Všimněte si, že pokud vystavitele adresu a vazby jsou zadané pro danou vazbu, místního vystavitele se nepoužije pro koncové body, které tuto vazbu používají. Klienti, kteří měli vždycky používat místního vystavitele zajistil nepoužívají takovou vazbu nebo jejich upravovat vazby, abyste je adresa vystavitele `null`.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Konfigurace pověření ve službě Federation](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Postupy: vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Postupy: vytvoření třídy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
