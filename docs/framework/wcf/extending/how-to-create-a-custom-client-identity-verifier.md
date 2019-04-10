---
title: 'Postupy: Vytvoření vlastního ověřovatele identity klientů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: d8529929870b14611c136221f1eefe3eb4ba3d42
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338992"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a><span data-ttu-id="b5251-102">Postupy: Vytvoření vlastního ověřovatele identity klientů</span><span class="sxs-lookup"><span data-stu-id="b5251-102">How to: Create a Custom Client Identity Verifier</span></span>
<span data-ttu-id="b5251-103">*Identity* funkce Windows Communication Foundation (WCF) umožňuje klientovi předem určit Očekávaná identita služby.</span><span class="sxs-lookup"><span data-stu-id="b5251-103">The *identity* feature of Windows Communication Foundation (WCF) enables a client to specify in advance the expected identity of the service.</span></span> <span data-ttu-id="b5251-104">Pokaždé, když se server ověří na klientovi, identita je porovnávána s Očekávaná identita.</span><span class="sxs-lookup"><span data-stu-id="b5251-104">Whenever a server authenticates itself to the client, the identity is checked against the expected identity.</span></span> <span data-ttu-id="b5251-105">(Vysvětlení identity a jak to funguje, najdete v článku [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="b5251-105">(For an explanation of identity and how it works, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span></span>  
  
 <span data-ttu-id="b5251-106">V případě potřeby je možné ověření přizpůsobit pomocí ověřovatele vlastní identity.</span><span class="sxs-lookup"><span data-stu-id="b5251-106">If needed, the verification can be customized using a custom identity verifier.</span></span> <span data-ttu-id="b5251-107">Můžete například provádět kontroly ověření identity další služby.</span><span class="sxs-lookup"><span data-stu-id="b5251-107">For example, you can perform additional service identity verification checks.</span></span> <span data-ttu-id="b5251-108">V tomto příkladu ověřovatele vlastní identity ověří další deklarace identity v certifikátu X.509 vrácená ze serveru.</span><span class="sxs-lookup"><span data-stu-id="b5251-108">In this example, the custom identity verifier checks additional claims in the X.509 certificate returned from the server.</span></span> <span data-ttu-id="b5251-109">Ukázková aplikace, najdete v části [ukázka Identity služby](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b5251-109">For a sample application, see [Service Identity Sample](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span></span>  
  
### <a name="to-extend-the-endpointidentity-class"></a><span data-ttu-id="b5251-110">Rozšíření třídy EndpointIdentity</span><span class="sxs-lookup"><span data-stu-id="b5251-110">To extend the EndpointIdentity class</span></span>  
  
1. <span data-ttu-id="b5251-111">Definovat novou třídu, která je odvozena z <xref:System.ServiceModel.EndpointIdentity> třídy.</span><span class="sxs-lookup"><span data-stu-id="b5251-111">Define a new class that derives from the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="b5251-112">V tomto příkladu názvy rozšíření `OrgEndpointIdentity`.</span><span class="sxs-lookup"><span data-stu-id="b5251-112">This example names the extension `OrgEndpointIdentity`.</span></span>  
  
2. <span data-ttu-id="b5251-113">Přidat soukromé členy spolu s vlastnostmi, které se použijí podle rozšířené <xref:System.ServiceModel.Security.IdentityVerifier> třídy provést kontrolu identity před deklarací identity v tokenu zabezpečení vráceného od služby.</span><span class="sxs-lookup"><span data-stu-id="b5251-113">Add private members along with properties that will be used by the extended <xref:System.ServiceModel.Security.IdentityVerifier> class to perform the identity check against claims in the security token returned from the service.</span></span> <span data-ttu-id="b5251-114">Tento příklad definuje jednu vlastnost: `OrganizationClaim` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b5251-114">This example defines one property: the `OrganizationClaim` property.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a><span data-ttu-id="b5251-115">Rozšíření třídy IdentityVerifier</span><span class="sxs-lookup"><span data-stu-id="b5251-115">To extend the IdentityVerifier class</span></span>  
  
1. <span data-ttu-id="b5251-116">Definovat novou třídu, která je odvozena z <xref:System.ServiceModel.Security.IdentityVerifier>.</span><span class="sxs-lookup"><span data-stu-id="b5251-116">Define a new class that derives from <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="b5251-117">V tomto příkladu názvy rozšíření `CustomIdentityVerifier`.</span><span class="sxs-lookup"><span data-stu-id="b5251-117">This example names the extension `CustomIdentityVerifier`.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2. <span data-ttu-id="b5251-118">Přepsat <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b5251-118">Override the <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> method.</span></span> <span data-ttu-id="b5251-119">Metoda určuje, zda kontrola identity bylo úspěšné nebo neúspěšné.</span><span class="sxs-lookup"><span data-stu-id="b5251-119">The method determines whether the identity check succeeded or failed.</span></span>  
  
3. <span data-ttu-id="b5251-120">`CheckAccess` Metoda má dva parametry.</span><span class="sxs-lookup"><span data-stu-id="b5251-120">The `CheckAccess` method has two parameters.</span></span> <span data-ttu-id="b5251-121">První je instance <xref:System.ServiceModel.EndpointIdentity> třídy.</span><span class="sxs-lookup"><span data-stu-id="b5251-121">The first is an instance of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="b5251-122">Druhá je instance <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="b5251-122">The second is an instance of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
     <span data-ttu-id="b5251-123">V implementaci metody, zkontrolujte sadu deklarací identity vrátí <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> třídy a provádět kontroly ověřování podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="b5251-123">In the method implementation, examine the collection of claims returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class, and perform authentication checks as required.</span></span> <span data-ttu-id="b5251-124">Tento příklad začíná tím, že hledá všechny deklarace identity, která je typu "Rozlišující název" a pak porovná název, který má rozšíření <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span><span class="sxs-lookup"><span data-stu-id="b5251-124">This example begins by finding any claim that is of type "Distinguished Name" and then compares the name to the extension of the <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a><span data-ttu-id="b5251-125">K implementaci TryGetIdentity – metoda</span><span class="sxs-lookup"><span data-stu-id="b5251-125">To implement the TryGetIdentity method</span></span>  
  
1. <span data-ttu-id="b5251-126">Implementace <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> metoda, která určuje, zda instance <xref:System.ServiceModel.EndpointIdentity> třídy může být vrácen klienta.</span><span class="sxs-lookup"><span data-stu-id="b5251-126">Implement the <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> method, which determines whether an instance of the <xref:System.ServiceModel.EndpointIdentity> class can be returned by the client.</span></span> <span data-ttu-id="b5251-127">Infrastruktura WCF volá uplatňování `TryGetIdentity` metoda nejprve se načíst identitu služby ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="b5251-127">The WCF infrastructure calls the implementation of the `TryGetIdentity` method first to retrieve the service's identity from the message.</span></span> <span data-ttu-id="b5251-128">Dále volá infrastruktury `CheckAccess` implementaci vráceného `EndpointIdentity` a <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="b5251-128">Next, the infrastructure calls the `CheckAccess` implementation with the returned `EndpointIdentity` and <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span>  
  
2. <span data-ttu-id="b5251-129">V `TryGetIdentity` metoda, vložte následující kód:</span><span class="sxs-lookup"><span data-stu-id="b5251-129">In the `TryGetIdentity` method, put the following code:</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a><span data-ttu-id="b5251-130">Nastavit vlastní IdentityVerifier a implementovat vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="b5251-130">To implement a custom binding and set the custom IdentityVerifier</span></span>  
  
1. <span data-ttu-id="b5251-131">Vytvořit metodu, která se vrátí <xref:System.ServiceModel.Channels.Binding> objektu.</span><span class="sxs-lookup"><span data-stu-id="b5251-131">Create a method that returns a <xref:System.ServiceModel.Channels.Binding> object.</span></span> <span data-ttu-id="b5251-132">Tento příklad začíná vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy a nastaví její režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message>a jeho <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> k <xref:System.ServiceModel.MessageCredentialType.None>.</span><span class="sxs-lookup"><span data-stu-id="b5251-132">This example begins creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class and sets its security mode to <xref:System.ServiceModel.SecurityMode.Message>, and its <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> to <xref:System.ServiceModel.MessageCredentialType.None>.</span></span>  
  
2. <span data-ttu-id="b5251-133">Vytvoření <xref:System.ServiceModel.Channels.BindingElementCollection> pomocí <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b5251-133">Create a <xref:System.ServiceModel.Channels.BindingElementCollection> using the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="b5251-134">Vrátit <xref:System.ServiceModel.Channels.SecurityBindingElement> z kolekce a přetypovat ji na <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> proměnné.</span><span class="sxs-lookup"><span data-stu-id="b5251-134">Return the <xref:System.ServiceModel.Channels.SecurityBindingElement> from the collection and cast it to a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variable.</span></span>  
  
4. <span data-ttu-id="b5251-135">Nastavte <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> vlastnost <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> novou instanci třídy `CustomIdentityVerifier` třídy, které jste předtím vytvořili.</span><span class="sxs-lookup"><span data-stu-id="b5251-135">Set the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> property of the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class to a new instance of the `CustomIdentityVerifier` class created previously.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5. <span data-ttu-id="b5251-136">Vlastní vazby, který je vrácen se používá k vytvoření instance klienta a třídy.</span><span class="sxs-lookup"><span data-stu-id="b5251-136">The custom binding that is returned is used to create an instance of the client and class.</span></span> <span data-ttu-id="b5251-137">Klient pak můžete provádět kontrolu ověření a vlastní identitu služby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b5251-137">The client can then perform a custom identity verification check of the service as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="b5251-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5251-138">Example</span></span>  
 <span data-ttu-id="b5251-139">Následující příklad ukazuje úplnou implementaci <xref:System.ServiceModel.Security.IdentityVerifier> třídy.</span><span class="sxs-lookup"><span data-stu-id="b5251-139">The following example shows a complete implementation of the <xref:System.ServiceModel.Security.IdentityVerifier> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="b5251-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5251-140">Example</span></span>  
 <span data-ttu-id="b5251-141">Následující příklad ukazuje úplnou implementaci <xref:System.ServiceModel.EndpointIdentity> třídy.</span><span class="sxs-lookup"><span data-stu-id="b5251-141">The following example shows a complete implementation of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="b5251-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5251-142">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [<span data-ttu-id="b5251-143">Ukázka identity služby</span><span class="sxs-lookup"><span data-stu-id="b5251-143">Service Identity Sample</span></span>](../../../../docs/framework/wcf/samples/service-identity-sample.md)
- [<span data-ttu-id="b5251-144">Zásada autorizace</span><span class="sxs-lookup"><span data-stu-id="b5251-144">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
