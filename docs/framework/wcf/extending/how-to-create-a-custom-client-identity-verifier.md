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
# <a name="how-to-create-a-custom-client-identity-verifier"></a><span data-ttu-id="423a1-102">Postupy: Vytvoření vlastního ověřovatele identity klientů</span><span class="sxs-lookup"><span data-stu-id="423a1-102">How to: Create a Custom Client Identity Verifier</span></span>
<span data-ttu-id="423a1-103">Funkce *identity* Windows Communication Foundation (WCF) umožňuje klientovi zadat předem očekávanou identitu služby.</span><span class="sxs-lookup"><span data-stu-id="423a1-103">The *identity* feature of Windows Communication Foundation (WCF) enables a client to specify in advance the expected identity of the service.</span></span> <span data-ttu-id="423a1-104">Pokaždé, když se server sám ověřuje pro klienta, je identita ověřená na očekávanou identitu.</span><span class="sxs-lookup"><span data-stu-id="423a1-104">Whenever a server authenticates itself to the client, the identity is checked against the expected identity.</span></span> <span data-ttu-id="423a1-105">(Vysvětlení identity a způsobu, jakým funguje, najdete v tématu [Identita a ověřování služby](../feature-details/service-identity-and-authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="423a1-105">(For an explanation of identity and how it works, see [Service Identity and Authentication](../feature-details/service-identity-and-authentication.md).)</span></span>  
  
 <span data-ttu-id="423a1-106">V případě potřeby je možné ověřování upravit pomocí vlastního ověřovatele identity.</span><span class="sxs-lookup"><span data-stu-id="423a1-106">If needed, the verification can be customized using a custom identity verifier.</span></span> <span data-ttu-id="423a1-107">Můžete třeba provést další kontroly ověřování identity služby.</span><span class="sxs-lookup"><span data-stu-id="423a1-107">For example, you can perform additional service identity verification checks.</span></span> <span data-ttu-id="423a1-108">V tomto příkladu vlastní ověřovatel identity kontroluje další deklarace identity v certifikátu X. 509 vráceném ze serveru.</span><span class="sxs-lookup"><span data-stu-id="423a1-108">In this example, the custom identity verifier checks additional claims in the X.509 certificate returned from the server.</span></span> <span data-ttu-id="423a1-109">Ukázkovou aplikaci najdete v tématu [Ukázka identity služby](../samples/service-identity-sample.md).</span><span class="sxs-lookup"><span data-stu-id="423a1-109">For a sample application, see [Service Identity Sample](../samples/service-identity-sample.md).</span></span>  
  
### <a name="to-extend-the-endpointidentity-class"></a><span data-ttu-id="423a1-110">Postup rozšiřování třídy EndpointIdentity</span><span class="sxs-lookup"><span data-stu-id="423a1-110">To extend the EndpointIdentity class</span></span>  
  
1. <span data-ttu-id="423a1-111">Definujte novou třídu, která je odvozena od <xref:System.ServiceModel.EndpointIdentity> třídy.</span><span class="sxs-lookup"><span data-stu-id="423a1-111">Define a new class that derives from the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="423a1-112">Tento příklad pojmenuje `OrgEndpointIdentity`rozšíření.</span><span class="sxs-lookup"><span data-stu-id="423a1-112">This example names the extension `OrgEndpointIdentity`.</span></span>  
  
2. <span data-ttu-id="423a1-113">Přidejte soukromé členy spolu s vlastnostmi, které budou použity rozšířenou <xref:System.ServiceModel.Security.IdentityVerifier> třídou k provedení kontroly identity u deklarací identity v tokenu zabezpečení vráceném službou.</span><span class="sxs-lookup"><span data-stu-id="423a1-113">Add private members along with properties that will be used by the extended <xref:System.ServiceModel.Security.IdentityVerifier> class to perform the identity check against claims in the security token returned from the service.</span></span> <span data-ttu-id="423a1-114">Tento příklad definuje jednu vlastnost: `OrganizationClaim` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="423a1-114">This example defines one property: the `OrganizationClaim` property.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a><span data-ttu-id="423a1-115">Postup rozšiřování třídy IdentityVerifier</span><span class="sxs-lookup"><span data-stu-id="423a1-115">To extend the IdentityVerifier class</span></span>  
  
1. <span data-ttu-id="423a1-116">Definujte novou třídu, která je odvozena <xref:System.ServiceModel.Security.IdentityVerifier>z.</span><span class="sxs-lookup"><span data-stu-id="423a1-116">Define a new class that derives from <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="423a1-117">Tento příklad pojmenuje `CustomIdentityVerifier`rozšíření.</span><span class="sxs-lookup"><span data-stu-id="423a1-117">This example names the extension `CustomIdentityVerifier`.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2. <span data-ttu-id="423a1-118">Přepsat <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="423a1-118">Override the <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> method.</span></span> <span data-ttu-id="423a1-119">Metoda určuje, zda byla ověření identity úspěšná nebo neúspěšná.</span><span class="sxs-lookup"><span data-stu-id="423a1-119">The method determines whether the identity check succeeded or failed.</span></span>  
  
3. <span data-ttu-id="423a1-120">`CheckAccess` Metoda má dva parametry.</span><span class="sxs-lookup"><span data-stu-id="423a1-120">The `CheckAccess` method has two parameters.</span></span> <span data-ttu-id="423a1-121">První je instance <xref:System.ServiceModel.EndpointIdentity> třídy.</span><span class="sxs-lookup"><span data-stu-id="423a1-121">The first is an instance of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="423a1-122">Druhá je instance <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="423a1-122">The second is an instance of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
     <span data-ttu-id="423a1-123">V implementaci metody zkontrolujte kolekci deklarací vrácených <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastností <xref:System.IdentityModel.Policy.AuthorizationContext> třídy a proveďte kontroly ověřování podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="423a1-123">In the method implementation, examine the collection of claims returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class, and perform authentication checks as required.</span></span> <span data-ttu-id="423a1-124">Tento příklad začíná hledáním jakékoli deklarace identity, která je typu "rozlišující název", a poté porovná název s příponou <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span><span class="sxs-lookup"><span data-stu-id="423a1-124">This example begins by finding any claim that is of type "Distinguished Name" and then compares the name to the extension of the <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a><span data-ttu-id="423a1-125">Implementace metody TryGetIdentity</span><span class="sxs-lookup"><span data-stu-id="423a1-125">To implement the TryGetIdentity method</span></span>  
  
1. <span data-ttu-id="423a1-126">Implementujte <xref:System.ServiceModel.EndpointIdentity> metodu, která určuje, zda může klient vrátit instanci třídy. <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A></span><span class="sxs-lookup"><span data-stu-id="423a1-126">Implement the <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> method, which determines whether an instance of the <xref:System.ServiceModel.EndpointIdentity> class can be returned by the client.</span></span> <span data-ttu-id="423a1-127">Infrastruktura WCF zavolá implementaci `TryGetIdentity` metody jako první, aby získala identitu služby ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="423a1-127">The WCF infrastructure calls the implementation of the `TryGetIdentity` method first to retrieve the service's identity from the message.</span></span> <span data-ttu-id="423a1-128">Dále infrastruktura volá `CheckAccess` implementaci s vrácenými `EndpointIdentity` a <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="423a1-128">Next, the infrastructure calls the `CheckAccess` implementation with the returned `EndpointIdentity` and <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span>  
  
2. <span data-ttu-id="423a1-129">`TryGetIdentity` V metodě vložte následující kód:</span><span class="sxs-lookup"><span data-stu-id="423a1-129">In the `TryGetIdentity` method, put the following code:</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a><span data-ttu-id="423a1-130">Implementace vlastní vazby a nastavení vlastního IdentityVerifier</span><span class="sxs-lookup"><span data-stu-id="423a1-130">To implement a custom binding and set the custom IdentityVerifier</span></span>  
  
1. <span data-ttu-id="423a1-131">Vytvořte metodu, která vrací <xref:System.ServiceModel.Channels.Binding> objekt.</span><span class="sxs-lookup"><span data-stu-id="423a1-131">Create a method that returns a <xref:System.ServiceModel.Channels.Binding> object.</span></span> <span data-ttu-id="423a1-132">Tento příklad začne vytvářet <xref:System.ServiceModel.WSHttpBinding> instanci třídy a nastaví její režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message>a <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> na <xref:System.ServiceModel.MessageCredentialType.None>.</span><span class="sxs-lookup"><span data-stu-id="423a1-132">This example begins creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class and sets its security mode to <xref:System.ServiceModel.SecurityMode.Message>, and its <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> to <xref:System.ServiceModel.MessageCredentialType.None>.</span></span>  
  
2. <span data-ttu-id="423a1-133"><xref:System.ServiceModel.Channels.BindingElementCollection> Vytvořte<xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="423a1-133">Create a <xref:System.ServiceModel.Channels.BindingElementCollection> using the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="423a1-134">Vrátit z kolekce a přetypovat ji <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> na proměnnou. <xref:System.ServiceModel.Channels.SecurityBindingElement></span><span class="sxs-lookup"><span data-stu-id="423a1-134">Return the <xref:System.ServiceModel.Channels.SecurityBindingElement> from the collection and cast it to a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variable.</span></span>  
  
4. <span data-ttu-id="423a1-135"><xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> Nastavte vlastnost <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> třídy na novou instanci `CustomIdentityVerifier` třídy, kterou jste vytvořili dříve.</span><span class="sxs-lookup"><span data-stu-id="423a1-135">Set the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> property of the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class to a new instance of the `CustomIdentityVerifier` class created previously.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5. <span data-ttu-id="423a1-136">Vlastní vazba, která je vrácena, slouží k vytvoření instance klienta a třídy.</span><span class="sxs-lookup"><span data-stu-id="423a1-136">The custom binding that is returned is used to create an instance of the client and class.</span></span> <span data-ttu-id="423a1-137">Klient pak může provést kontrolu vlastní ověření identity služby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="423a1-137">The client can then perform a custom identity verification check of the service as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="423a1-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="423a1-138">Example</span></span>  
 <span data-ttu-id="423a1-139">Následující příklad ukazuje úplnou implementaci <xref:System.ServiceModel.Security.IdentityVerifier> třídy.</span><span class="sxs-lookup"><span data-stu-id="423a1-139">The following example shows a complete implementation of the <xref:System.ServiceModel.Security.IdentityVerifier> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="423a1-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="423a1-140">Example</span></span>  
 <span data-ttu-id="423a1-141">Následující příklad ukazuje úplnou implementaci <xref:System.ServiceModel.EndpointIdentity> třídy.</span><span class="sxs-lookup"><span data-stu-id="423a1-141">The following example shows a complete implementation of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="423a1-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="423a1-142">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [<span data-ttu-id="423a1-143">Ukázka identity služby</span><span class="sxs-lookup"><span data-stu-id="423a1-143">Service Identity Sample</span></span>](../samples/service-identity-sample.md)
- [<span data-ttu-id="423a1-144">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="423a1-144">Authorization Policy</span></span>](../samples/authorization-policy.md)
