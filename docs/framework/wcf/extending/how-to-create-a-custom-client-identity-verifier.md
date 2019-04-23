---
title: 'Postupy: Vytvoření vlastního ověřovatele identity klientů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: d8529929870b14611c136221f1eefe3eb4ba3d42
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338992"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a>Postupy: Vytvoření vlastního ověřovatele identity klientů
*Identity* funkce Windows Communication Foundation (WCF) umožňuje klientovi předem určit Očekávaná identita služby. Pokaždé, když se server ověří na klientovi, identita je porovnávána s Očekávaná identita. (Vysvětlení identity a jak to funguje, najdete v článku [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)  
  
 V případě potřeby je možné ověření přizpůsobit pomocí ověřovatele vlastní identity. Můžete například provádět kontroly ověření identity další služby. V tomto příkladu ověřovatele vlastní identity ověří další deklarace identity v certifikátu X.509 vrácená ze serveru. Ukázková aplikace, najdete v části [ukázka Identity služby](../../../../docs/framework/wcf/samples/service-identity-sample.md).  
  
### <a name="to-extend-the-endpointidentity-class"></a>Rozšíření třídy EndpointIdentity  
  
1. Definovat novou třídu, která je odvozena z <xref:System.ServiceModel.EndpointIdentity> třídy. V tomto příkladu názvy rozšíření `OrgEndpointIdentity`.  
  
2. Přidat soukromé členy spolu s vlastnostmi, které se použijí podle rozšířené <xref:System.ServiceModel.Security.IdentityVerifier> třídy provést kontrolu identity před deklarací identity v tokenu zabezpečení vráceného od služby. Tento příklad definuje jednu vlastnost: `OrganizationClaim` vlastnost.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a>Rozšíření třídy IdentityVerifier  
  
1. Definovat novou třídu, která je odvozena z <xref:System.ServiceModel.Security.IdentityVerifier>. V tomto příkladu názvy rozšíření `CustomIdentityVerifier`.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2. Přepsat <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> metody. Metoda určuje, zda kontrola identity bylo úspěšné nebo neúspěšné.  
  
3. `CheckAccess` Metoda má dva parametry. První je instance <xref:System.ServiceModel.EndpointIdentity> třídy. Druhá je instance <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.  
  
     V implementaci metody, zkontrolujte sadu deklarací identity vrátí <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> třídy a provádět kontroly ověřování podle potřeby. Tento příklad začíná tím, že hledá všechny deklarace identity, která je typu "Rozlišující název" a pak porovná název, který má rozšíření <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a>K implementaci TryGetIdentity – metoda  
  
1. Implementace <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> metoda, která určuje, zda instance <xref:System.ServiceModel.EndpointIdentity> třídy může být vrácen klienta. Infrastruktura WCF volá uplatňování `TryGetIdentity` metoda nejprve se načíst identitu služby ze zprávy. Dále volá infrastruktury `CheckAccess` implementaci vráceného `EndpointIdentity` a <xref:System.IdentityModel.Policy.AuthorizationContext>.  
  
2. V `TryGetIdentity` metoda, vložte následující kód:  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a>Nastavit vlastní IdentityVerifier a implementovat vlastní vazby  
  
1. Vytvořit metodu, která se vrátí <xref:System.ServiceModel.Channels.Binding> objektu. Tento příklad začíná vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy a nastaví její režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message>a jeho <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> k <xref:System.ServiceModel.MessageCredentialType.None>.  
  
2. Vytvoření <xref:System.ServiceModel.Channels.BindingElementCollection> pomocí <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metody.  
  
3. Vrátit <xref:System.ServiceModel.Channels.SecurityBindingElement> z kolekce a přetypovat ji na <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> proměnné.  
  
4. Nastavte <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> vlastnost <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> novou instanci třídy `CustomIdentityVerifier` třídy, které jste předtím vytvořili.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5. Vlastní vazby, který je vrácen se používá k vytvoření instance klienta a třídy. Klient pak můžete provádět kontrolu ověření a vlastní identitu služby, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje úplnou implementaci <xref:System.ServiceModel.Security.IdentityVerifier> třídy.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje úplnou implementaci <xref:System.ServiceModel.EndpointIdentity> třídy.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [Ukázka identity služby](../../../../docs/framework/wcf/samples/service-identity-sample.md)
- [Zásady autorizace](../../../../docs/framework/wcf/samples/authorization-policy.md)
