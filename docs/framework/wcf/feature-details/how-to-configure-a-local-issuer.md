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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c24b039709a013f210a42d67c744c03489e4cf73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="a2ea1-102">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="a2ea1-102">How to: Configure a Local Issuer</span></span>
<span data-ttu-id="a2ea1-103">Toto téma popisuje postup konfigurace klienta pro použití místního vystavitele pro vydané tokeny.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>  
  
 <span data-ttu-id="a2ea1-104">Často Pokud klient komunikuje s federované služby, služby určuje adresu tokenu služby, kterou je očekáván k vydání tokenu klient použije k vlastnímu ověření federované služby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="a2ea1-105">V některých situacích může být klient nakonfigurován pro použití *místního vystavitele*.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="a2ea1-106">používá místního vystavitele v případech, kdy je na adresu vystavitele federované vazby http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous nebo `null`.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-106"> uses a local issuer in cases where the issuer address of a federated binding is http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous or `null`.</span></span> <span data-ttu-id="a2ea1-107">V takových případech musíte nakonfigurovat <xref:System.ServiceModel.Description.ClientCredentials> s adresou místního vystavitele a vazby, které používají ke komunikaci s této vystavitele.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2ea1-108">Pokud <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> vlastnost `ClientCredentials` třída je nastaven na `true`, není zadána adresa místního vystavitele a vystavitele adresu zadanou [ \<– wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) či jiné federované vazby je http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self, http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous, nebo je `null`, pak Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] vystavitele se používá.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self, http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous, or is `null`, then the Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] issuer is used.</span></span>  
  
### <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="a2ea1-109">Konfigurace místního vystavitele v kódu</span><span class="sxs-lookup"><span data-stu-id="a2ea1-109">To configure the local issuer in code</span></span>  
  
1.  <span data-ttu-id="a2ea1-110">Vytvoření proměnné typu<xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="a2ea1-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>  
  
2.  <span data-ttu-id="a2ea1-111">Nastavte proměnnou na instance, kterou vrátil <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> vlastnost `ClientCredentials` třídy.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="a2ea1-112">Tato instance je vrácený <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost klienta (zděděno z <xref:System.ServiceModel.ClientBase%601>) nebo <xref:System.ServiceModel.ChannelFactory.Credentials%2A> vlastnost <xref:System.ServiceModel.ChannelFactory>:</span><span class="sxs-lookup"><span data-stu-id="a2ea1-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  <span data-ttu-id="a2ea1-113">Nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> vlastnost novou instanci třídy <xref:System.ServiceModel.EndpointAddress>, s na adresu místního vystavitele jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     <span data-ttu-id="a2ea1-114">Alternativně vytvořte novou <xref:System.Uri> instance jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     <span data-ttu-id="a2ea1-115">`addressHeaders` Parametr je pole <xref:System.ServiceModel.Channels.AddressHeader> instance, jak je vidět.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  <span data-ttu-id="a2ea1-116">Nastavit vazby pro místního vystavitele pomocí <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  <span data-ttu-id="a2ea1-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-117">Optional.</span></span> <span data-ttu-id="a2ea1-118">Přidání chování nakonfigurovaný koncový bod pro místního vystavitele přidáním takové chování do kolekce vrácené <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="a2ea1-119">Konfigurace místního vystavitele v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="a2ea1-119">To configure the local issuer in configuration</span></span>  
  
1.  <span data-ttu-id="a2ea1-120">Vytvoření [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) jako podřízený element [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element, který je sám podřízeným [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element v chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-120">Create a [\<localIssuer>](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>  
  
2.  <span data-ttu-id="a2ea1-121">Nastavte `address` atribut na adresu místního vystavitele, který bude přijímat žádosti o tokeny.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>  
  
3.  <span data-ttu-id="a2ea1-122">Nastavte `binding` a `bindingConfiguration` atributy hodnoty, které odkazují na odpovídající vazby použít při komunikaci s koncovým bodem místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>  
  
4.  <span data-ttu-id="a2ea1-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-123">Optional.</span></span> <span data-ttu-id="a2ea1-124">Nastavte [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) jako podřízený element <`localIssuer`> elementu a zadejte informace o identitě pro místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-124">Set the [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>  
  
5.  <span data-ttu-id="a2ea1-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-125">Optional.</span></span> <span data-ttu-id="a2ea1-126">Nastavte [ \<hlavičky >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) jako podřízený element <`localIssuer`> elementu a zadejte další hlavičky, které jsou požadovány k správně adres místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-126">Set the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a2ea1-127">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a2ea1-127">.NET Framework Security</span></span>  
 <span data-ttu-id="a2ea1-128">Všimněte si, že pokud vystavitele adresu a vazby jsou zadané pro danou vazbu, místního vystavitele se nepoužije pro koncové body, které tuto vazbu používají.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="a2ea1-129">Klienti, kteří měli vždycky používat místního vystavitele zajistil nepoužívají takovou vazbu nebo jejich upravovat vazby, abyste je adresa vystavitele `null`.</span><span class="sxs-lookup"><span data-stu-id="a2ea1-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ea1-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2ea1-130">See Also</span></span>  
 [<span data-ttu-id="a2ea1-131">Postupy: Konfigurace přihlašovacích údajů ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="a2ea1-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="a2ea1-132">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="a2ea1-132">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="a2ea1-133">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a2ea1-133">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
