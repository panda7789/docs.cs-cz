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
ms.openlocfilehash: 0028a0522447588ee0fb183b5b2f93d334a7b2b2
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972070"
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="4f923-102">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="4f923-102">How to: Configure a Local Issuer</span></span>

<span data-ttu-id="4f923-103">Toto téma popisuje, jak nakonfigurovat klienta tak, aby používal místního vystavitele pro vydané tokeny.</span><span class="sxs-lookup"><span data-stu-id="4f923-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>

<span data-ttu-id="4f923-104">Když klient komunikuje se službou federované služby, je často určena adresa služby tokenu zabezpečení, u které se očekává vystavení tokenu, který bude klient používat k ověření identity pro federované služby.</span><span class="sxs-lookup"><span data-stu-id="4f923-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="4f923-105">V některých situacích může být klient nakonfigurovaný tak, aby používal *místního*vystavitele.</span><span class="sxs-lookup"><span data-stu-id="4f923-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>

<span data-ttu-id="4f923-106">Windows Communication Foundation (WCF) používá místního vystavitele v případech, kdy je `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` adresa vydavatele federované vazby nebo. `null`</span><span class="sxs-lookup"><span data-stu-id="4f923-106">Windows Communication Foundation (WCF) uses a local issuer in cases where the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="4f923-107">V takových případech musíte nakonfigurovat <xref:System.ServiceModel.Description.ClientCredentials> adresu místního vystavitele a vazbu, která se má použít ke komunikaci s tímto vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="4f923-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>

> [!NOTE]
> <span data-ttu-id="4f923-108">Pokud je `ClientCredentials` `true`vlastnost třídy nastavena na hodnotu, není zadána adresa místního vystavitele a adresa vystavitele [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) , kterou určuje WSFederationHttpBinding > nebo jiná federované vazba, je <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` ,`http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`nebo je`null`, použije se Vystavitel Windows CardSpace.</span><span class="sxs-lookup"><span data-stu-id="4f923-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, or is `null`, then the Windows CardSpace issuer is used.</span></span>

## <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="4f923-109">Konfigurace místního vystavitele v kódu</span><span class="sxs-lookup"><span data-stu-id="4f923-109">To configure the local issuer in code</span></span>

1. <span data-ttu-id="4f923-110">Vytvořit proměnnou typu<xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="4f923-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>

2. <span data-ttu-id="4f923-111">Nastavte proměnnou na instanci vrácenou z <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> vlastnosti `ClientCredentials` třídy.</span><span class="sxs-lookup"><span data-stu-id="4f923-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="4f923-112">Tato <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> instance je vrácena vlastností klienta (zděděna z <xref:System.ServiceModel.ClientBase%601>) <xref:System.ServiceModel.ChannelFactory>nebo <xref:System.ServiceModel.ChannelFactory.Credentials%2A> vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="4f923-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. <span data-ttu-id="4f923-113">Nastavte vlastnost na novou instanci <xref:System.ServiceModel.EndpointAddress>s adresou místního vystavitele jako argument konstruktoru. <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A></span><span class="sxs-lookup"><span data-stu-id="4f923-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     <span data-ttu-id="4f923-114">Alternativně vytvořte novou <xref:System.Uri> instanci jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4f923-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     <span data-ttu-id="4f923-115">`addressHeaders` Parametr je<xref:System.ServiceModel.Channels.AddressHeader> pole instancí, jak je znázorněno na obrázku.</span><span class="sxs-lookup"><span data-stu-id="4f923-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. <span data-ttu-id="4f923-116">Nastavte vazbu pro místního vystavitele pomocí <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4f923-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. <span data-ttu-id="4f923-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4f923-117">Optional.</span></span> <span data-ttu-id="4f923-118">Přidejte nakonfigurované chování koncového bodu pro místního vystavitele přidáním takového chování do kolekce vrácené <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="4f923-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="4f923-119">Konfigurace místního vystavitele v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="4f923-119">To configure the local issuer in configuration</span></span>

1. <span data-ttu-id="4f923-120">Vytvořte prvek [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) localIssuer > jako podřízený prvek třídy IssuedToken >, který je sám podřízenou položkou prvku ClientCredentials > v chování koncového bodu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)</span><span class="sxs-lookup"><span data-stu-id="4f923-120">Create a [\<localIssuer>](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>

2. <span data-ttu-id="4f923-121">`address` Nastavte atribut na adresu místního vystavitele, který bude přijímat žádosti o tokeny.</span><span class="sxs-lookup"><span data-stu-id="4f923-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>

3. <span data-ttu-id="4f923-122">Nastavte atributy `bindingConfiguration` a na hodnoty, které odkazují na příslušnou vazbu, která se má použít při komunikaci s místním koncovým bodem vystavitele. `binding`</span><span class="sxs-lookup"><span data-stu-id="4f923-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>

4. <span data-ttu-id="4f923-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4f923-123">Optional.</span></span> <span data-ttu-id="4f923-124">Nastavte prvek`localIssuer`identity > jako podřízený prvek elementu < > a určete informace o identitě pro místního vystavitele. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)</span><span class="sxs-lookup"><span data-stu-id="4f923-124">Set the [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>

5. <span data-ttu-id="4f923-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4f923-125">Optional.</span></span> <span data-ttu-id="4f923-126">`localIssuer` [ Nastavte>elementHeadersjakopodřízenýprvekelementu<>aurčetedalšíhlavičky,kteréjsoupožadoványprosprávnéadresovánímístního\<](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) vystavitele.</span><span class="sxs-lookup"><span data-stu-id="4f923-126">Set the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="4f923-127">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4f923-127">.NET Framework Security</span></span>

<span data-ttu-id="4f923-128">Všimněte si, že pokud je pro danou vazbu určena adresa vydavatele a vazba, místní vystavitel není použit pro koncové body, které používají tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="4f923-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="4f923-129">Klienti, kteří očekávají, že mají vždy používat místního vystavitele, by měli zajistit, aby nepoužívali takovou vazbu ani nezměnili vazbu tak, `null`aby byla adresa vystavitele.</span><span class="sxs-lookup"><span data-stu-id="4f923-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f923-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f923-130">See also</span></span>

- [<span data-ttu-id="4f923-131">Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="4f923-131">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="4f923-132">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="4f923-132">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="4f923-133">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="4f923-133">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
