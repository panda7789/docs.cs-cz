---
title: "Postupy: vytvoření zprostředkovatele tokenu vlastní zabezpečení"
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
helpviewer_keywords: security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 0bf616b1af46c62166b0430c1b67b3a97f0613ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-security-token-provider"></a><span data-ttu-id="68b2c-102">Postupy: vytvoření zprostředkovatele tokenu vlastní zabezpečení</span><span class="sxs-lookup"><span data-stu-id="68b2c-102">How to: Create a Custom Security Token Provider</span></span>
<span data-ttu-id="68b2c-103">Toto téma ukazuje, jak vytvořit nové typy tokenů s poskytovatele tokenu vlastní zabezpečení a postup pro integraci zprostředkovatele tokenu správce vlastní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="68b2c-103">This topic shows how to create new token types with a custom security token provider and how to integrate the provider with a custom security token manager.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68b2c-104">Vytvořit vlastní zprostředkovatele tokenu, pokud v nalezen tokeny poskytované systémem <xref:System.IdentityModel.Tokens> obor názvů se neshodují vašim požadavkům.</span><span class="sxs-lookup"><span data-stu-id="68b2c-104">Create a custom token provider if the system-provided tokens found in the <xref:System.IdentityModel.Tokens> namespace do not match your requirements.</span></span>  
  
 <span data-ttu-id="68b2c-105">Poskytovatele tokenu zabezpečení slouží k vytvoření tokenu vyjádření zabezpečení na základě informací v klienta služby Windows nebo pověření.</span><span class="sxs-lookup"><span data-stu-id="68b2c-105">The security token provider creates a security token representation based on information in the client or service credentials.</span></span> <span data-ttu-id="68b2c-106">Použití zprostředkovatele tokenu vlastní zabezpečení v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zabezpečení, musíte vytvořit vlastní pověření a implementace Správce tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="68b2c-106">To use the custom security token provider in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] security, you must create custom credentials and security token manager implementations.</span></span>  
  
 <span data-ttu-id="68b2c-107">Další informace o vlastní pověření a Správce tokenů zabezpečení najdete v článku [návod: vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="68b2c-107">For more information about custom credentials and security token manager see the [Walkthrough: Creating Custom Client and Service Credentials](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
 <span data-ttu-id="68b2c-108">Další informace o pověření zabezpečení tokenu správce, zprostředkovatele a ověřovací třídách naleznete v tématu [Architektura zabezpečení](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f).</span><span class="sxs-lookup"><span data-stu-id="68b2c-108">For more information about credentials, security token manager, provider and authenticator classes, see the [Security Architecture](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f).</span></span>  
  
### <a name="to-create-a-custom-security-token-provider"></a><span data-ttu-id="68b2c-109">Chcete-li vytvořit poskytovatele tokenu vlastní zabezpečení</span><span class="sxs-lookup"><span data-stu-id="68b2c-109">To create a custom security token provider</span></span>  
  
1.  <span data-ttu-id="68b2c-110">Definovat nové třídy odvozené od <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třídy.</span><span class="sxs-lookup"><span data-stu-id="68b2c-110">Define a new class derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class.</span></span>  
  
2.  <span data-ttu-id="68b2c-111">Implementace <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metoda.</span><span class="sxs-lookup"><span data-stu-id="68b2c-111">Implement the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="68b2c-112">Metoda odpovídá za vytváření a vrací instanci třídy token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="68b2c-112">The method is responsible for creating and returning an instance of the security token.</span></span> <span data-ttu-id="68b2c-113">Následující příklad vytvoří třídu s názvem `MySecurityTokenProvider`a přepíše <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> metoda vrátí instanci <xref:System.IdentityModel.Tokens.X509SecurityToken> třídy.</span><span class="sxs-lookup"><span data-stu-id="68b2c-113">The following example creates a class named `MySecurityTokenProvider`, and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method to return an instance of the <xref:System.IdentityModel.Tokens.X509SecurityToken> class.</span></span> <span data-ttu-id="68b2c-114">Konstruktoru třídy vyžaduje instanci systému <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> třídy.</span><span class="sxs-lookup"><span data-stu-id="68b2c-114">The class constructor requires an instance of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> class.</span></span>  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a><span data-ttu-id="68b2c-115">Pro integraci poskytovatele tokenu zabezpečení vlastní Správce tokenů vlastní zabezpečení</span><span class="sxs-lookup"><span data-stu-id="68b2c-115">To integrate a custom security token provider with a custom security token manager</span></span>  
  
1.  <span data-ttu-id="68b2c-116">Definovat nové třídy odvozené od <xref:System.IdentityModel.Selectors.SecurityTokenManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="68b2c-116">Define a new class derived from the <xref:System.IdentityModel.Selectors.SecurityTokenManager> class.</span></span> <span data-ttu-id="68b2c-117">(Následující příklad je odvozena z <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> třída, která je odvozena z <xref:System.IdentityModel.Selectors.SecurityTokenManager> třídy.)</span><span class="sxs-lookup"><span data-stu-id="68b2c-117">(The example below derives from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class, which derives from the <xref:System.IdentityModel.Selectors.SecurityTokenManager> class.)</span></span>  
  
2.  <span data-ttu-id="68b2c-118">Přepsání <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> metoda, pokud již není přepsána.</span><span class="sxs-lookup"><span data-stu-id="68b2c-118">Override the <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> method if is not already overridden.</span></span>  
  
     <span data-ttu-id="68b2c-119"><xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> Metoda odpovídá za vrací instanci třídy <xref:System.IdentityModel.Selectors.SecurityTokenProvider> třída vhodné <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametr předaný metodě podle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] framework zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="68b2c-119">The <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> method is responsible for returning an instance of the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class appropriate to the <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parameter passed to the method by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security framework.</span></span> <span data-ttu-id="68b2c-120">Změňte metodu vrátit implementaci zprostředkovatele tokenu vlastní zabezpečení (vytvořený v předchozím postupu) Pokud je metoda volána s parametrem tokenu příslušné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="68b2c-120">Modify the method to return the custom security token provider implementation (created in the previous procedure) when the method is called with an appropriate security token parameter.</span></span> <span data-ttu-id="68b2c-121">Další informace o tokenu správce zabezpečení najdete v tématu [návod: vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="68b2c-121">For more information about the security token manager, see the [Walkthrough: Creating Custom Client and Service Credentials](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).</span></span>  
  
3.  <span data-ttu-id="68b2c-122">Přidat vlastní logiky do způsob ho vrátit vašeho poskytovatele tokenu vlastní zabezpečení na základě povolení <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parametr.</span><span class="sxs-lookup"><span data-stu-id="68b2c-122">Add custom logic to the method to enable it to return your custom security token provider based on the <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> parameter.</span></span> <span data-ttu-id="68b2c-123">Následující příklad vrátí poskytovatele tokenu vlastní zabezpečení, pokud jsou splněny požadavky na tokenu.</span><span class="sxs-lookup"><span data-stu-id="68b2c-123">The following sample returns the custom security token provider if the token requirements are met.</span></span> <span data-ttu-id="68b2c-124">Požadavky na zahrnují token zabezpečení X.509 a směr zprávy (aby token se používá pro výstup zpráv).</span><span class="sxs-lookup"><span data-stu-id="68b2c-124">The requirements include an X.509 security token and the message direction (that the token is used for message output).</span></span> <span data-ttu-id="68b2c-125">Všech ostatních případech kód zavolá základní třídy, chcete-li udržovat poskytované systémem chování pro jiné požadavky na tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="68b2c-125">For all other cases, the code calls the base class to maintain the system-provided behavior for other security token requirements.</span></span>  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="68b2c-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="68b2c-126">Example</span></span>  
 <span data-ttu-id="68b2c-127">Následující příklad zobrazuje úplná <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementace spolu s odpovídající <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementace.</span><span class="sxs-lookup"><span data-stu-id="68b2c-127">The following shows a complete <xref:System.IdentityModel.Selectors.SecurityTokenProvider> implementation along with a corresponding <xref:System.IdentityModel.Selectors.SecurityTokenManager> implementation.</span></span>  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="68b2c-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="68b2c-128">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.X509SecurityToken>  
 [<span data-ttu-id="68b2c-129">Návod: Vytvoření vlastního klienta a pověření služby</span><span class="sxs-lookup"><span data-stu-id="68b2c-129">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [<span data-ttu-id="68b2c-130">Postupy: Vytvoření ověřovacího modulu tokenu vlastní zabezpečení</span><span class="sxs-lookup"><span data-stu-id="68b2c-130">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [<span data-ttu-id="68b2c-131">Architektura zabezpečení</span><span class="sxs-lookup"><span data-stu-id="68b2c-131">Security Architecture</span></span>](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)
