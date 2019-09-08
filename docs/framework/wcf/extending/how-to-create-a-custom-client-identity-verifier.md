---
title: 'Postupy: Vytvoření vlastního ověřovatele identity klientů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: 86e7869efdba50d72cc61a1aebb767cf43927546
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795630"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a>Postupy: Vytvoření vlastního ověřovatele identity klientů
Funkce *identity* Windows Communication Foundation (WCF) umožňuje klientovi zadat předem očekávanou identitu služby. Pokaždé, když se server sám ověřuje pro klienta, je identita ověřená na očekávanou identitu. (Vysvětlení identity a způsobu, jakým funguje, najdete v tématu [Identita a ověřování služby](../feature-details/service-identity-and-authentication.md).)  
  
 V případě potřeby je možné ověřování upravit pomocí vlastního ověřovatele identity. Můžete třeba provést další kontroly ověřování identity služby. V tomto příkladu vlastní ověřovatel identity kontroluje další deklarace identity v certifikátu X. 509 vráceném ze serveru. Ukázkovou aplikaci najdete v tématu [Ukázka identity služby](../samples/service-identity-sample.md).  
  
### <a name="to-extend-the-endpointidentity-class"></a>Postup rozšiřování třídy EndpointIdentity  
  
1. Definujte novou třídu, která je odvozena od <xref:System.ServiceModel.EndpointIdentity> třídy. Tento příklad pojmenuje `OrgEndpointIdentity`rozšíření.  
  
2. Přidejte soukromé členy spolu s vlastnostmi, které budou použity rozšířenou <xref:System.ServiceModel.Security.IdentityVerifier> třídou k provedení kontroly identity u deklarací identity v tokenu zabezpečení vráceném službou. Tento příklad definuje jednu vlastnost: `OrganizationClaim` vlastnost.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a>Postup rozšiřování třídy IdentityVerifier  
  
1. Definujte novou třídu, která je odvozena <xref:System.ServiceModel.Security.IdentityVerifier>z. Tento příklad pojmenuje `CustomIdentityVerifier`rozšíření.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2. Přepsat <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> metody. Metoda určuje, zda byla ověření identity úspěšná nebo neúspěšná.  
  
3. `CheckAccess` Metoda má dva parametry. První je instance <xref:System.ServiceModel.EndpointIdentity> třídy. Druhá je instance <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.  
  
     V implementaci metody zkontrolujte kolekci deklarací vrácených <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastností <xref:System.IdentityModel.Policy.AuthorizationContext> třídy a proveďte kontroly ověřování podle potřeby. Tento příklad začíná hledáním jakékoli deklarace identity, která je typu "rozlišující název", a poté porovná název s příponou <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a>Implementace metody TryGetIdentity  
  
1. Implementujte <xref:System.ServiceModel.EndpointIdentity> metodu, která určuje, zda může klient vrátit instanci třídy. <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> Infrastruktura WCF zavolá implementaci `TryGetIdentity` metody jako první, aby získala identitu služby ze zprávy. Dále infrastruktura volá `CheckAccess` implementaci s vrácenými `EndpointIdentity` a <xref:System.IdentityModel.Policy.AuthorizationContext>.  
  
2. `TryGetIdentity` V metodě vložte následující kód:  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a>Implementace vlastní vazby a nastavení vlastního IdentityVerifier  
  
1. Vytvořte metodu, která vrací <xref:System.ServiceModel.Channels.Binding> objekt. Tento příklad začne vytvářet <xref:System.ServiceModel.WSHttpBinding> instanci třídy a nastaví její režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message>a <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> na <xref:System.ServiceModel.MessageCredentialType.None>.  
  
2. <xref:System.ServiceModel.Channels.BindingElementCollection> Vytvořte<xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> pomocí metody.  
  
3. Vrátit z kolekce a přetypovat ji <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> na proměnnou. <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
4. <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> Nastavte vlastnost <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> třídy na novou instanci `CustomIdentityVerifier` třídy, kterou jste vytvořili dříve.  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5. Vlastní vazba, která je vrácena, slouží k vytvoření instance klienta a třídy. Klient pak může provést kontrolu vlastní ověření identity služby, jak je znázorněno v následujícím kódu.  
  
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
- [Ukázka identity služby](../samples/service-identity-sample.md)
- [Zásady autorizace](../samples/authorization-policy.md)
