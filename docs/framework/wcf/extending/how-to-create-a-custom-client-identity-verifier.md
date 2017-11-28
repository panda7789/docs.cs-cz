---
title: "Postupy: vytvoření Identity ověřovatel vlastní klienta"
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
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75200cc6aca424befe068a9dd718c6cc76492a91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a>Postupy: vytvoření Identity ověřovatel vlastní klienta
*Identity* funkce [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] umožňuje klientovi k určení předem očekávanou identitu služby. Vždy, když server se ověří na klienta, je identita kontrolovat očekávanou identitu. (Vysvětlení identit a jak to funguje, najdete v článku [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)  
  
 V případě potřeby ověření jde přizpůsobit pomocí ověřovatele vlastní identitu. Můžete například provést kontroly ověření identity další služby. V tomto příkladu kontroluje ověřovatele vlastní identitu další deklarace identity v certifikátu X.509 vrácená serverem. Ukázkovou aplikaci, najdete v části [ukázka Identity služby](../../../../docs/framework/wcf/samples/service-identity-sample.md).  
  
### <a name="to-extend-the-endpointidentity-class"></a>Rozšíření třídy třída EndpointIdentity  
  
1.  Zadejte novou třídu odvozenou od <xref:System.ServiceModel.EndpointIdentity> třídy. Tento příklad názvy rozšíření `OrgEndpointIdentity`.  
  
2.  Přidat soukromé členy společně s vlastností, které se použijí podle rozšířené <xref:System.ServiceModel.Security.IdentityVerifier> třída provést kontrolu identity před nároky v vrácená ze služby tokenu zabezpečení. Tento příklad definuje jednu vlastnost: `OrganizationClaim` vlastnost.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a>Rozšíření třídy IdentityVerifier  
  
1.  Zadejte novou třídu odvozenou od <xref:System.ServiceModel.Security.IdentityVerifier>. Tento příklad názvy rozšíření `CustomIdentityVerifier`.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2.  Přepsání <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> metoda. Metoda určuje, zda kontrola identity byla úspěšná nebo neúspěšná.  
  
3.  `CheckAccess` Metoda má dva parametry. První je instance <xref:System.ServiceModel.EndpointIdentity> třídy. Druhá je instance <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.  
  
     K implementaci metoda zkontrolujte kolekci deklarací identity vrátí <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> třídy a provádění kontrol ověřování podle potřeby. Tento příklad začíná tak, že najdete všechny deklarace identity, která je typu "Rozlišující název" a pak porovná název, který má rozšíření <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a>Chcete-li implementovat metodu TryGetIdentity  
  
1.  Implementace <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> metoda, která určuje, zda instanci <xref:System.ServiceModel.EndpointIdentity> třídy mohou být vráceny klientem. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Infrastruktury volá implementace `TryGetIdentity` metodu nejdřív načíst identitu služby ze zprávy. V dalším kroku infrastruktury volá `CheckAccess` implementace s vrácený `EndpointIdentity` a <xref:System.IdentityModel.Policy.AuthorizationContext>.  
  
2.  V `TryGetIdentity` metoda, vložte následující kód:  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a>K implementaci vlastních vazeb a nastavit vlastní IdentityVerifier  
  
1.  Vytvoření metody, která vrátí <xref:System.ServiceModel.Channels.Binding> objektu. Tento příklad začíná vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy a nastaví režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message>a jeho <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> k <xref:System.ServiceModel.MessageCredentialType.None>.  
  
2.  Vytvoření <xref:System.ServiceModel.Channels.BindingElementCollection> pomocí <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metoda.  
  
3.  Vrátí <xref:System.ServiceModel.Channels.SecurityBindingElement> z kolekce a vysílat <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> proměnné.  
  
4.  Nastavte <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> vlastnost <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> novou instanci třídy `CustomIdentityVerifier` třídy, které jste vytvořili dříve.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5.  Vlastní vazby, která je vrácena slouží k vytvoření instance klienta a třída. Klient pak můžete provádět kontrolu ověření vlastní identitu služby, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje na dokončení implementace <xref:System.ServiceModel.Security.IdentityVerifier> třídy.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje na dokončení implementace <xref:System.ServiceModel.EndpointIdentity> třídy.  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 <xref:System.ServiceModel.EndpointIdentity>  
 <xref:System.ServiceModel.Security.IdentityVerifier>  
 [Ukázka Identity služby](../../../../docs/framework/wcf/samples/service-identity-sample.md)  
 [Zásady autorizace](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [Zásady autorizace](../../../../docs/framework/wcf/samples/authorization-policy.md)
