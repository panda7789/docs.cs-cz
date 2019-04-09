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
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="c3ce0-102">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="c3ce0-102">How to: Configure a Local Issuer</span></span>
<span data-ttu-id="c3ce0-103">Toto téma popisuje, jak nakonfigurovat klienta k využití místního vystavitele pro vydané tokeny.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>  
  
 <span data-ttu-id="c3ce0-104">Často se stává Pokud klient komunikuje s federované služby, služby určuje adresu služby tokenů, který má token vydat klient použije ke svému ověření ke službě federovaného zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="c3ce0-105">V určitých situacích může být klient nakonfigurován pro použití *lokálního vystavitele*.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>  
  
 <span data-ttu-id="c3ce0-106">Windows Communication Foundation (WCF) používá místního vystavitele v případech, kdy je adresa vystavitele federované vazby `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` nebo `null`.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-106">Windows Communication Foundation (WCF) uses a local issuer in cases where the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="c3ce0-107">V takových případech musíte nakonfigurovat <xref:System.ServiceModel.Description.ClientCredentials> adresou místního vystavitele a vazbu používají ke komunikaci s tohoto vydavatele.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3ce0-108">Pokud <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> vlastnost `ClientCredentials` třídy je nastavena na `true`se nezadala adresa místního vystavitele a zadána adresa vystavitele ve [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) nebo jiné federované vazby je `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, nebo je `null`, pak Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] vystavitele se používá.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, or is `null`, then the Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] issuer is used.</span></span>  
  
### <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="c3ce0-109">Konfigurace místního vystavitele v kódu</span><span class="sxs-lookup"><span data-stu-id="c3ce0-109">To configure the local issuer in code</span></span>  
  
1.  <span data-ttu-id="c3ce0-110">Vytvořte proměnnou typu</span><span class="sxs-lookup"><span data-stu-id="c3ce0-110">Create a variable of type</span></span> <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
2.  <span data-ttu-id="c3ce0-111">Nastavte proměnnou na instanci vrácenou z <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> vlastnost `ClientCredentials` třídy.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="c3ce0-112">Tato instance je vrácený <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost klienta (zděděno z <xref:System.ServiceModel.ClientBase%601>) nebo <xref:System.ServiceModel.ChannelFactory.Credentials%2A> vlastnost <xref:System.ServiceModel.ChannelFactory>:</span><span class="sxs-lookup"><span data-stu-id="c3ce0-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  <span data-ttu-id="c3ce0-113">Nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> vlastností nové instance <xref:System.ServiceModel.EndpointAddress>, adresou místního vystavitele jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     <span data-ttu-id="c3ce0-114">Alternativně vytvořte novou <xref:System.Uri> instanci jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     <span data-ttu-id="c3ce0-115">`addressHeaders` Parametr je pole <xref:System.ServiceModel.Channels.AddressHeader> instance, jak je znázorněno.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  <span data-ttu-id="c3ce0-116">Nastavit vazbu lokálního vystavitele pomocí <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  <span data-ttu-id="c3ce0-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-117">Optional.</span></span> <span data-ttu-id="c3ce0-118">Přidání chování konfigurovaný koncový bod pro lokálního vystavitele tak, že přidáte toto chování na kolekci vrácené poskytovatelem <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="c3ce0-119">Konfigurace místního vystavitele v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="c3ce0-119">To configure the local issuer in configuration</span></span>  
  
1.  <span data-ttu-id="c3ce0-120">Vytvoření [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element jako podřízený objekt [ \<třídy issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element, který je sám podřízeným prvkem [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) prvek chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-120">Create a [\<localIssuer>](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>  
  
2.  <span data-ttu-id="c3ce0-121">Nastavte `address` atribut na adresu místního vystavitele, který bude přijímat žádosti o tokeny.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>  
  
3.  <span data-ttu-id="c3ce0-122">Nastavte `binding` a `bindingConfiguration` atributy na hodnoty, které odkazují na příslušnou datovou vazbu při komunikaci s koncovým bodem lokálního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>  
  
4.  <span data-ttu-id="c3ce0-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-123">Optional.</span></span> <span data-ttu-id="c3ce0-124">Nastavte [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element jako podřízený objekt <`localIssuer`> element a zadejte informace o identitě pro lokálního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-124">Set the [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>  
  
5.  <span data-ttu-id="c3ce0-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-125">Optional.</span></span> <span data-ttu-id="c3ce0-126">Nastavte [ \<záhlaví >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element jako podřízený objekt <`localIssuer`> element a zadejte dodatečné hlavičky, které jsou nutné ke správnému adresování lokálního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-126">Set the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c3ce0-127">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c3ce0-127">.NET Framework Security</span></span>  
 <span data-ttu-id="c3ce0-128">Všimněte si, že případného vystavitele adresu a vazbu jsou pro danou vazbu lokálního vystavitele se pro koncové body, které tuto vazbu používají.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="c3ce0-129">Klienti, kteří očekávají, že vždy používejte lokálního vystavitele zajistil nepoužívají takovou vazbu nebo jejich upravte vazbu tak, aby byla adresa vystavitele ve `null`.</span><span class="sxs-lookup"><span data-stu-id="c3ce0-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ce0-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3ce0-130">See also</span></span>

- [<span data-ttu-id="c3ce0-131">Postupy: Konfigurace pověření ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="c3ce0-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="c3ce0-132">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="c3ce0-132">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="c3ce0-133">Postupy: Vytvoření instance WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c3ce0-133">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
