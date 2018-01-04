---
title: "Rozšíření zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
caps.latest.revision: "23"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ecbbaac0023ca528967abe2cb60c3d790772fb2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="extending-security"></a><span data-ttu-id="d07a8-102">Rozšíření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d07a8-102">Extending Security</span></span>
<span data-ttu-id="d07a8-103">Abychom vyhověli nové typy deklarací identity a vlastní tokeny, můžete rozšířit Infrastruktura zabezpečení [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d07a8-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="d07a8-104">Témata v této části ukazují, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="d07a8-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d07a8-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d07a8-105">In This Section</span></span>  
 [<span data-ttu-id="d07a8-106">Architektura zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d07a8-106">Security Architecture</span></span>](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)  
 <span data-ttu-id="d07a8-107">Provede architektura [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení systému.</span><span class="sxs-lookup"><span data-stu-id="d07a8-107">Walks through the architecture of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security system.</span></span>  
  
 [<span data-ttu-id="d07a8-108">Vlastní přihlašovací údaje a jejich ověřování</span><span class="sxs-lookup"><span data-stu-id="d07a8-108">Custom Credential and Credential Validation</span></span>](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 <span data-ttu-id="d07a8-109">Vysvětluje, jak modelem Identity se používá při ověření vlastní pověření.</span><span class="sxs-lookup"><span data-stu-id="d07a8-109">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="d07a8-110">Vlastní tokeny</span><span class="sxs-lookup"><span data-stu-id="d07a8-110">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 <span data-ttu-id="d07a8-111">Vystavené tokeny z zabezpečení tokenu služby (STS) jsou obvykle tokeny SAML.</span><span class="sxs-lookup"><span data-stu-id="d07a8-111">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="d07a8-112">Toto téma vysvětluje, jak vytvořit vlastní typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="d07a8-112">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="d07a8-113">Vlastní autorizace</span><span class="sxs-lookup"><span data-stu-id="d07a8-113">Custom Authorization</span></span>](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 <span data-ttu-id="d07a8-114">Vysvětluje, jak implementovat vlastní autorizace.</span><span class="sxs-lookup"><span data-stu-id="d07a8-114">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="d07a8-115">Přepsání identity služby kvůli ověřování</span><span class="sxs-lookup"><span data-stu-id="d07a8-115">Overriding the Identity of a Service for Authentication</span></span>](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="d07a8-116">Popisuje, jak k přepsání identity služby kvůli ověřování.</span><span class="sxs-lookup"><span data-stu-id="d07a8-116">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="d07a8-117">Postupy: Vytvoření vlastního ověřovatele identity klientů</span><span class="sxs-lookup"><span data-stu-id="d07a8-117">How to: Create a Custom Client Identity Verifier</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="d07a8-118">Ukazuje, jak ověřit identitu vlastní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="d07a8-118">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="d07a8-119">Postupy: Použití samostatných certifikátů X.509 pro přihlašování a šifrování</span><span class="sxs-lookup"><span data-stu-id="d07a8-119">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="d07a8-120">Zprávy jsou obvykle podepsat a zašifrovat s jeden certifikát.</span><span class="sxs-lookup"><span data-stu-id="d07a8-120">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="d07a8-121">Toto téma vysvětluje, jak dva certifikáty lze použít, když se vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="d07a8-121">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="d07a8-122">Postupy: Změna zprostředkovatele kryptografických služeb pro privátní klíč certifikátu X.509</span><span class="sxs-lookup"><span data-stu-id="d07a8-122">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="d07a8-123">Vysvětluje, jak změnit zprostředkovatele kryptografických služeb používá k zajištění privátní klíč certifikátu X.509 a jak integrovat do zprostředkovatele [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.</span><span class="sxs-lookup"><span data-stu-id="d07a8-123">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d07a8-124">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d07a8-124">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="d07a8-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d07a8-125">Related Sections</span></span>  
 [<span data-ttu-id="d07a8-126">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d07a8-126">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="d07a8-127">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="d07a8-127">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="d07a8-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d07a8-128">See Also</span></span>  
 [<span data-ttu-id="d07a8-129">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d07a8-129">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
