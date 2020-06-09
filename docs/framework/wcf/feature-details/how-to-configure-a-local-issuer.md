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
ms.openlocfilehash: 7da3cd34d0840eea48c9ef0bb89fb6580b87623b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601241"
---
# <a name="how-to-configure-a-local-issuer"></a><span data-ttu-id="f760f-102">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="f760f-102">How to: Configure a Local Issuer</span></span>

<span data-ttu-id="f760f-103">Toto téma popisuje, jak nakonfigurovat klienta tak, aby používal místního vystavitele pro vydané tokeny.</span><span class="sxs-lookup"><span data-stu-id="f760f-103">This topic describes how to configure a client to use a local issuer for issued tokens.</span></span>

<span data-ttu-id="f760f-104">Když klient komunikuje se službou federované služby, je často určena adresa služby tokenu zabezpečení, u které se očekává vystavení tokenu, který bude klient používat k ověření identity pro federované služby.</span><span class="sxs-lookup"><span data-stu-id="f760f-104">Often, when a client communicates with a federated service, the service specifies the address of the security token service that is expected to issue the token the client will use to authenticate itself to the federated service.</span></span> <span data-ttu-id="f760f-105">V některých situacích může být klient nakonfigurovaný tak, aby používal *místního vystavitele*.</span><span class="sxs-lookup"><span data-stu-id="f760f-105">In certain situations, the client may be configured to use a *local issuer*.</span></span>

<span data-ttu-id="f760f-106">Windows Communication Foundation (WCF) používá místního vystavitele v případech, kdy je adresa vydavatele federované vazby `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` nebo `null` .</span><span class="sxs-lookup"><span data-stu-id="f760f-106">Windows Communication Foundation (WCF) uses a local issuer in cases where the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="f760f-107">V takových případech musíte nakonfigurovat <xref:System.ServiceModel.Description.ClientCredentials> adresu místního vystavitele a vazbu, která se má použít ke komunikaci s tímto vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="f760f-107">In such cases, you must configure the <xref:System.ServiceModel.Description.ClientCredentials> with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>

> [!NOTE]
> <span data-ttu-id="f760f-108">Pokud <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> `ClientCredentials` je vlastnost třídy nastavena na hodnotu `true` , není zadána adresa místního vystavitele a adresa vystavitele, která je určena v [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) nebo jiné federované vazbě `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self` , je, nebo, pak je `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` použit Vystavitel Windows CardSpace.</span><span class="sxs-lookup"><span data-stu-id="f760f-108">If the <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> property of the `ClientCredentials` class is set to `true`, a local issuer address is not specified, and the issuer address specified by the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) or other federated binding is `http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`, `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`, or is `null`, then the Windows CardSpace issuer is used.</span></span>

## <a name="to-configure-the-local-issuer-in-code"></a><span data-ttu-id="f760f-109">Konfigurace místního vystavitele v kódu</span><span class="sxs-lookup"><span data-stu-id="f760f-109">To configure the local issuer in code</span></span>

1. <span data-ttu-id="f760f-110">Vytvořit proměnnou typu<xref:System.ServiceModel.Security.IssuedTokenClientCredential></span><span class="sxs-lookup"><span data-stu-id="f760f-110">Create a variable of type <xref:System.ServiceModel.Security.IssuedTokenClientCredential></span></span>

2. <span data-ttu-id="f760f-111">Nastavte proměnnou na instanci vrácenou z <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> vlastnosti `ClientCredentials` třídy.</span><span class="sxs-lookup"><span data-stu-id="f760f-111">Set the variable to the instance returned from the <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> property of the `ClientCredentials` class.</span></span> <span data-ttu-id="f760f-112">Tato instance je vrácena <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastností klienta (zděděna z <xref:System.ServiceModel.ClientBase%601> ) nebo <xref:System.ServiceModel.ChannelFactory.Credentials%2A> vlastnosti <xref:System.ServiceModel.ChannelFactory> :</span><span class="sxs-lookup"><span data-stu-id="f760f-112">That instance is returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the client (inherited from <xref:System.ServiceModel.ClientBase%601>) or the <xref:System.ServiceModel.ChannelFactory.Credentials%2A> property of the <xref:System.ServiceModel.ChannelFactory>:</span></span>

     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]

3. <span data-ttu-id="f760f-113">Nastavte <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> vlastnost na novou instanci <xref:System.ServiceModel.EndpointAddress> s adresou místního vystavitele jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f760f-113">Set the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> property to a new instance of the <xref:System.ServiceModel.EndpointAddress>, with the address of the local issuer as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]

     <span data-ttu-id="f760f-114">Alternativně vytvořte novou <xref:System.Uri> instanci jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f760f-114">Alternatively, create a new <xref:System.Uri> instance as an argument to the constructor.</span></span>

     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]

     <span data-ttu-id="f760f-115">`addressHeaders`Parametr je pole <xref:System.ServiceModel.Channels.AddressHeader> instancí, jak je znázorněno na obrázku.</span><span class="sxs-lookup"><span data-stu-id="f760f-115">The `addressHeaders` parameter is an array of <xref:System.ServiceModel.Channels.AddressHeader> instances, as shown.</span></span>

     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]

4. <span data-ttu-id="f760f-116">Nastavte vazbu pro místního vystavitele pomocí <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f760f-116">Set the binding for the local issuer using the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]

5. <span data-ttu-id="f760f-117">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f760f-117">Optional.</span></span> <span data-ttu-id="f760f-118">Přidejte nakonfigurované chování koncového bodu pro místního vystavitele přidáním takového chování do kolekce vrácené <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="f760f-118">Add configured endpoint behaviors for the local issuer by adding such behaviors to the collection returned by the <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> property.</span></span>

     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]

## <a name="to-configure-the-local-issuer-in-configuration"></a><span data-ttu-id="f760f-119">Konfigurace místního vystavitele v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="f760f-119">To configure the local issuer in configuration</span></span>

1. <span data-ttu-id="f760f-120">Vytvořte [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) prvek jako podřízený [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) prvek prvku, který je podřízeným prvkem [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) prvku v chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f760f-120">Create a [\<localIssuer>](../../configure-apps/file-schema/wcf/localissuer.md) element as a child of the [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) element that is itself a child of the [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element in an endpoint behavior.</span></span>

2. <span data-ttu-id="f760f-121">Nastavte `address` atribut na adresu místního vystavitele, který bude přijímat žádosti o tokeny.</span><span class="sxs-lookup"><span data-stu-id="f760f-121">Set the `address` attribute to the address of the local issuer that will accept token requests.</span></span>

3. <span data-ttu-id="f760f-122">Nastavte `binding` atributy a `bindingConfiguration` na hodnoty, které odkazují na příslušnou vazbu, která se má použít při komunikaci s místním koncovým bodem vystavitele.</span><span class="sxs-lookup"><span data-stu-id="f760f-122">Set the `binding` and `bindingConfiguration` attributes to values that reference the appropriate binding to use when communicating with the local issuer endpoint.</span></span>

4. <span data-ttu-id="f760f-123">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f760f-123">Optional.</span></span> <span data-ttu-id="f760f-124">Nastavte [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element jako podřízenou položku `localIssuer` prvku <> a zadejte informace o identitě místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="f760f-124">Set the [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element as a child of the <`localIssuer`> element and specify identity information for the local issuer.</span></span>

5. <span data-ttu-id="f760f-125">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f760f-125">Optional.</span></span> <span data-ttu-id="f760f-126">Nastavte [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element jako podřízený `localIssuer` prvek <> a určete další hlavičky, které jsou požadovány pro správné adresování místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="f760f-126">Set the [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element as a child of the <`localIssuer`> element and specify additional headers that are required in order to correctly address the local issuer.</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="f760f-127">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f760f-127">.NET Framework Security</span></span>

<span data-ttu-id="f760f-128">Všimněte si, že pokud je pro danou vazbu určena adresa vydavatele a vazba, místní vystavitel není použit pro koncové body, které používají tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="f760f-128">Note that if an issuer address and binding are specified for a given binding, the local issuer is not used for endpoints that use that binding.</span></span> <span data-ttu-id="f760f-129">Klienti, kteří očekávají, že mají vždy používat místního vystavitele, by měli zajistit, aby nepoužívali takovou vazbu ani nezměnili vazbu tak, aby byla adresa vystavitele `null` .</span><span class="sxs-lookup"><span data-stu-id="f760f-129">Clients who expect to always use the local issuer should ensure that they do not use such a binding or that they modify the binding so that the issuer address is `null`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f760f-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="f760f-130">See also</span></span>

- [<span data-ttu-id="f760f-131">Postupy: Konfigurace pověření ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="f760f-131">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="f760f-132">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="f760f-132">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="f760f-133">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f760f-133">How to: Create a WSFederationHttpBinding</span></span>](how-to-create-a-wsfederationhttpbinding.md)
