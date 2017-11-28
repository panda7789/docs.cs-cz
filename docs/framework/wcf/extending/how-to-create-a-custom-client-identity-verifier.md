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
# <a name="how-to-create-a-custom-client-identity-verifier"></a><span data-ttu-id="16b80-102">Postupy: vytvoření Identity ověřovatel vlastní klienta</span><span class="sxs-lookup"><span data-stu-id="16b80-102">How to: Create a Custom Client Identity Verifier</span></span>
<span data-ttu-id="16b80-103">*Identity* funkce [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] umožňuje klientovi k určení předem očekávanou identitu služby.</span><span class="sxs-lookup"><span data-stu-id="16b80-103">The *identity* feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] enables a client to specify in advance the expected identity of the service.</span></span> <span data-ttu-id="16b80-104">Vždy, když server se ověří na klienta, je identita kontrolovat očekávanou identitu.</span><span class="sxs-lookup"><span data-stu-id="16b80-104">Whenever a server authenticates itself to the client, the identity is checked against the expected identity.</span></span> <span data-ttu-id="16b80-105">(Vysvětlení identit a jak to funguje, najdete v článku [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span><span class="sxs-lookup"><span data-stu-id="16b80-105">(For an explanation of identity and how it works, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).)</span></span>  
  
 <span data-ttu-id="16b80-106">V případě potřeby ověření jde přizpůsobit pomocí ověřovatele vlastní identitu.</span><span class="sxs-lookup"><span data-stu-id="16b80-106">If needed, the verification can be customized using a custom identity verifier.</span></span> <span data-ttu-id="16b80-107">Můžete například provést kontroly ověření identity další služby.</span><span class="sxs-lookup"><span data-stu-id="16b80-107">For example, you can perform additional service identity verification checks.</span></span> <span data-ttu-id="16b80-108">V tomto příkladu kontroluje ověřovatele vlastní identitu další deklarace identity v certifikátu X.509 vrácená serverem.</span><span class="sxs-lookup"><span data-stu-id="16b80-108">In this example, the custom identity verifier checks additional claims in the X.509 certificate returned from the server.</span></span> <span data-ttu-id="16b80-109">Ukázkovou aplikaci, najdete v části [ukázka Identity služby](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span><span class="sxs-lookup"><span data-stu-id="16b80-109">For a sample application, see [Service Identity Sample](../../../../docs/framework/wcf/samples/service-identity-sample.md).</span></span>  
  
### <a name="to-extend-the-endpointidentity-class"></a><span data-ttu-id="16b80-110">Rozšíření třídy třída EndpointIdentity</span><span class="sxs-lookup"><span data-stu-id="16b80-110">To extend the EndpointIdentity class</span></span>  
  
1.  <span data-ttu-id="16b80-111">Zadejte novou třídu odvozenou od <xref:System.ServiceModel.EndpointIdentity> třídy.</span><span class="sxs-lookup"><span data-stu-id="16b80-111">Define a new class that derives from the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="16b80-112">Tento příklad názvy rozšíření `OrgEndpointIdentity`.</span><span class="sxs-lookup"><span data-stu-id="16b80-112">This example names the extension `OrgEndpointIdentity`.</span></span>  
  
2.  <span data-ttu-id="16b80-113">Přidat soukromé členy společně s vlastností, které se použijí podle rozšířené <xref:System.ServiceModel.Security.IdentityVerifier> třída provést kontrolu identity před nároky v vrácená ze služby tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="16b80-113">Add private members along with properties that will be used by the extended <xref:System.ServiceModel.Security.IdentityVerifier> class to perform the identity check against claims in the security token returned from the service.</span></span> <span data-ttu-id="16b80-114">Tento příklad definuje jednu vlastnost: `OrganizationClaim` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="16b80-114">This example defines one property: the `OrganizationClaim` property.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a><span data-ttu-id="16b80-115">Rozšíření třídy IdentityVerifier</span><span class="sxs-lookup"><span data-stu-id="16b80-115">To extend the IdentityVerifier class</span></span>  
  
1.  <span data-ttu-id="16b80-116">Zadejte novou třídu odvozenou od <xref:System.ServiceModel.Security.IdentityVerifier>.</span><span class="sxs-lookup"><span data-stu-id="16b80-116">Define a new class that derives from <xref:System.ServiceModel.Security.IdentityVerifier>.</span></span> <span data-ttu-id="16b80-117">Tento příklad názvy rozšíření `CustomIdentityVerifier`.</span><span class="sxs-lookup"><span data-stu-id="16b80-117">This example names the extension `CustomIdentityVerifier`.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2.  <span data-ttu-id="16b80-118">Přepsání <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="16b80-118">Override the <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> method.</span></span> <span data-ttu-id="16b80-119">Metoda určuje, zda kontrola identity byla úspěšná nebo neúspěšná.</span><span class="sxs-lookup"><span data-stu-id="16b80-119">The method determines whether the identity check succeeded or failed.</span></span>  
  
3.  <span data-ttu-id="16b80-120">`CheckAccess` Metoda má dva parametry.</span><span class="sxs-lookup"><span data-stu-id="16b80-120">The `CheckAccess` method has two parameters.</span></span> <span data-ttu-id="16b80-121">První je instance <xref:System.ServiceModel.EndpointIdentity> třídy.</span><span class="sxs-lookup"><span data-stu-id="16b80-121">The first is an instance of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span> <span data-ttu-id="16b80-122">Druhá je instance <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="16b80-122">The second is an instance of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
     <span data-ttu-id="16b80-123">K implementaci metoda zkontrolujte kolekci deklarací identity vrátí <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> třídy a provádění kontrol ověřování podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="16b80-123">In the method implementation, examine the collection of claims returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class, and perform authentication checks as required.</span></span> <span data-ttu-id="16b80-124">Tento příklad začíná tak, že najdete všechny deklarace identity, která je typu "Rozlišující název" a pak porovná název, který má rozšíření <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span><span class="sxs-lookup"><span data-stu-id="16b80-124">This example begins by finding any claim that is of type "Distinguished Name" and then compares the name to the extension of the <xref:System.ServiceModel.EndpointIdentity> (`OrgEndpointIdentity`).</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a><span data-ttu-id="16b80-125">Chcete-li implementovat metodu TryGetIdentity</span><span class="sxs-lookup"><span data-stu-id="16b80-125">To implement the TryGetIdentity method</span></span>  
  
1.  <span data-ttu-id="16b80-126">Implementace <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> metoda, která určuje, zda instanci <xref:System.ServiceModel.EndpointIdentity> třídy mohou být vráceny klientem.</span><span class="sxs-lookup"><span data-stu-id="16b80-126">Implement the <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> method, which determines whether an instance of the <xref:System.ServiceModel.EndpointIdentity> class can be returned by the client.</span></span> <span data-ttu-id="16b80-127">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Infrastruktury volá implementace `TryGetIdentity` metodu nejdřív načíst identitu služby ze zprávy.</span><span class="sxs-lookup"><span data-stu-id="16b80-127">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure calls the implementation of the `TryGetIdentity` method first to retrieve the service's identity from the message.</span></span> <span data-ttu-id="16b80-128">V dalším kroku infrastruktury volá `CheckAccess` implementace s vrácený `EndpointIdentity` a <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="16b80-128">Next, the infrastructure calls the `CheckAccess` implementation with the returned `EndpointIdentity` and <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span>  
  
2.  <span data-ttu-id="16b80-129">V `TryGetIdentity` metoda, vložte následující kód:</span><span class="sxs-lookup"><span data-stu-id="16b80-129">In the `TryGetIdentity` method, put the following code:</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a><span data-ttu-id="16b80-130">K implementaci vlastních vazeb a nastavit vlastní IdentityVerifier</span><span class="sxs-lookup"><span data-stu-id="16b80-130">To implement a custom binding and set the custom IdentityVerifier</span></span>  
  
1.  <span data-ttu-id="16b80-131">Vytvoření metody, která vrátí <xref:System.ServiceModel.Channels.Binding> objektu.</span><span class="sxs-lookup"><span data-stu-id="16b80-131">Create a method that returns a <xref:System.ServiceModel.Channels.Binding> object.</span></span> <span data-ttu-id="16b80-132">Tento příklad začíná vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy a nastaví režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message>a jeho <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> k <xref:System.ServiceModel.MessageCredentialType.None>.</span><span class="sxs-lookup"><span data-stu-id="16b80-132">This example begins creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class and sets its security mode to <xref:System.ServiceModel.SecurityMode.Message>, and its <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> to <xref:System.ServiceModel.MessageCredentialType.None>.</span></span>  
  
2.  <span data-ttu-id="16b80-133">Vytvoření <xref:System.ServiceModel.Channels.BindingElementCollection> pomocí <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="16b80-133">Create a <xref:System.ServiceModel.Channels.BindingElementCollection> using the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3.  <span data-ttu-id="16b80-134">Vrátí <xref:System.ServiceModel.Channels.SecurityBindingElement> z kolekce a vysílat <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> proměnné.</span><span class="sxs-lookup"><span data-stu-id="16b80-134">Return the <xref:System.ServiceModel.Channels.SecurityBindingElement> from the collection and cast it to a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> variable.</span></span>  
  
4.  <span data-ttu-id="16b80-135">Nastavte <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> vlastnost <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> novou instanci třídy `CustomIdentityVerifier` třídy, které jste vytvořili dříve.</span><span class="sxs-lookup"><span data-stu-id="16b80-135">Set the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> property of the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class to a new instance of the `CustomIdentityVerifier` class created previously.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5.  <span data-ttu-id="16b80-136">Vlastní vazby, která je vrácena slouží k vytvoření instance klienta a třída.</span><span class="sxs-lookup"><span data-stu-id="16b80-136">The custom binding that is returned is used to create an instance of the client and class.</span></span> <span data-ttu-id="16b80-137">Klient pak můžete provádět kontrolu ověření vlastní identitu služby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="16b80-137">The client can then perform a custom identity verification check of the service as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="16b80-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="16b80-138">Example</span></span>  
 <span data-ttu-id="16b80-139">Následující příklad ukazuje na dokončení implementace <xref:System.ServiceModel.Security.IdentityVerifier> třídy.</span><span class="sxs-lookup"><span data-stu-id="16b80-139">The following example shows a complete implementation of the <xref:System.ServiceModel.Security.IdentityVerifier> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="16b80-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="16b80-140">Example</span></span>  
 <span data-ttu-id="16b80-141">Následující příklad ukazuje na dokončení implementace <xref:System.ServiceModel.EndpointIdentity> třídy.</span><span class="sxs-lookup"><span data-stu-id="16b80-141">The following example shows a complete implementation of the <xref:System.ServiceModel.EndpointIdentity> class.</span></span>  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="16b80-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="16b80-142">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 <xref:System.ServiceModel.EndpointIdentity>  
 <xref:System.ServiceModel.Security.IdentityVerifier>  
 [<span data-ttu-id="16b80-143">Ukázka Identity služby</span><span class="sxs-lookup"><span data-stu-id="16b80-143">Service Identity Sample</span></span>](../../../../docs/framework/wcf/samples/service-identity-sample.md)  
 [<span data-ttu-id="16b80-144">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="16b80-144">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [<span data-ttu-id="16b80-145">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="16b80-145">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
