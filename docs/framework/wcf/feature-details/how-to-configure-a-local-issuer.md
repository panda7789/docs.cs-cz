---
title: 'Postupy: Konfigurace místního vystavitele'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: cb4a2bcc6f62fac5d0dde82ab32ed6e04e8a9b7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095552"
---
# <a name="how-to-configure-a-local-issuer"></a>Postupy: Konfigurace místního vystavitele
Toto téma popisuje, jak nakonfigurovat klienta k využití místního vystavitele pro vydané tokeny.  
  
 Často se stává Pokud klient komunikuje s federované služby, služby určuje adresu služby tokenů, který má token vydat klient použije ke svému ověření ke službě federovaného zabezpečení. V určitých situacích může být klient nakonfigurován pro použití *lokálního vystavitele*.  
  
 Windows Communication Foundation (WCF) používá místního vystavitele v případech, kdy je adresa vystavitele federované vazby `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` nebo `null`. V takových případech musíte nakonfigurovat <xref:System.ServiceModel.Description.ClientCredentials> adresou místního vystavitele a vazbu používají ke komunikaci s tohoto vydavatele.  
  
> [!NOTE]
>  Pokud <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> vlastnost `ClientCredentials` třídy je nastavena na `true`se nezadala adresa místního vystavitele a zadána adresa vystavitele ve [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) nebo jiné federované vazby je `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, nebo je `null`, pak Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] vystavitele se používá.  
  
### <a name="to-configure-the-local-issuer-in-code"></a>Konfigurace místního vystavitele v kódu  
  
1.  Vytvořte proměnnou typu <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
2.  Nastavte proměnnou na instanci vrácenou z <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> vlastnost `ClientCredentials` třídy. Tato instance je vrácený <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost klienta (zděděno z <xref:System.ServiceModel.ClientBase%601>) nebo <xref:System.ServiceModel.ChannelFactory.Credentials%2A> vlastnost <xref:System.ServiceModel.ChannelFactory>:  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  Nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> vlastností nové instance <xref:System.ServiceModel.EndpointAddress>, adresou místního vystavitele jako argument konstruktoru.  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     Alternativně vytvořte novou <xref:System.Uri> instanci jako argument konstruktoru.  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     `addressHeaders` Parametr je pole <xref:System.ServiceModel.Channels.AddressHeader> instance, jak je znázorněno.  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  Nastavit vazbu lokálního vystavitele pomocí <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> vlastnost.  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  Volitelné. Přidání chování konfigurovaný koncový bod pro lokálního vystavitele tak, že přidáte toto chování na kolekci vrácené poskytovatelem <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> vlastnost.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a>Konfigurace místního vystavitele v konfiguraci  
  
1.  Vytvoření [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element jako podřízený objekt [ \<třídy issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element, který je sám podřízeným prvkem [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) prvek chování koncového bodu.  
  
2.  Nastavte `address` atribut na adresu místního vystavitele, který bude přijímat žádosti o tokeny.  
  
3.  Nastavte `binding` a `bindingConfiguration` atributy na hodnoty, které odkazují na příslušnou datovou vazbu při komunikaci s koncovým bodem lokálního vystavitele.  
  
4.  Volitelné. Nastavte [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element jako podřízený objekt <`localIssuer`> element a zadejte informace o identitě pro lokálního vystavitele.  
  
5.  Volitelné. Nastavte [ \<záhlaví >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element jako podřízený objekt <`localIssuer`> element a zadejte dodatečné hlavičky, které jsou nutné ke správnému adresování lokálního vystavitele.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Všimněte si, že případného vystavitele adresu a vazbu jsou pro danou vazbu lokálního vystavitele se pro koncové body, které tuto vazbu používají. Klienti, kteří očekávají, že vždy používejte lokálního vystavitele zajistil nepoužívají takovou vazbu nebo jejich upravte vazbu tak, aby byla adresa vystavitele ve `null`.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Konfigurace pověření ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Postupy: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Postupy: Vytvoření instance WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
