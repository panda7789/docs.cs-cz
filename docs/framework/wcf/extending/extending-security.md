---
title: Rozšíření zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 45216493a3afa23f24a085964a2c43e19b197d4b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797129"
---
# <a name="extending-security"></a><span data-ttu-id="55d0d-102">Rozšíření zabezpečení</span><span class="sxs-lookup"><span data-stu-id="55d0d-102">Extending Security</span></span>
<span data-ttu-id="55d0d-103">Chcete-li přizpůsobit nové typy deklarací identity a vlastní tokeny, můžete roztáhnout infrastrukturu zabezpečení Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="55d0d-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="55d0d-104">Témata v této části vám ukážou, jak to uděláte.</span><span class="sxs-lookup"><span data-stu-id="55d0d-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55d0d-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="55d0d-105">In This Section</span></span>  
  
 [<span data-ttu-id="55d0d-106">Vlastní přihlašovací údaje a jejich ověřování</span><span class="sxs-lookup"><span data-stu-id="55d0d-106">Custom Credential and Credential Validation</span></span>](custom-credential-and-credential-validation.md)  
 <span data-ttu-id="55d0d-107">Vysvětluje, jak se používá model identity při ověřování vlastních přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="55d0d-107">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="55d0d-108">Vlastní tokeny</span><span class="sxs-lookup"><span data-stu-id="55d0d-108">Custom Tokens</span></span>](custom-tokens.md)  
 <span data-ttu-id="55d0d-109">Vydané tokeny ze služby tokenů zabezpečení (STS) jsou obvykle tokeny SAML.</span><span class="sxs-lookup"><span data-stu-id="55d0d-109">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="55d0d-110">Toto téma vysvětluje, jak vytvořit vlastní typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="55d0d-110">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="55d0d-111">Vlastní autorizace</span><span class="sxs-lookup"><span data-stu-id="55d0d-111">Custom Authorization</span></span>](custom-authorization.md)  
 <span data-ttu-id="55d0d-112">Vysvětluje, jak implementovat vlastní autorizaci.</span><span class="sxs-lookup"><span data-stu-id="55d0d-112">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="55d0d-113">Přepsání identity služby kvůli ověřování</span><span class="sxs-lookup"><span data-stu-id="55d0d-113">Overriding the Identity of a Service for Authentication</span></span>](overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="55d0d-114">Popisuje, jak přepsat identitu služby pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="55d0d-114">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="55d0d-115">Postupy: Vytvoření vlastního ověřovatele identity klienta</span><span class="sxs-lookup"><span data-stu-id="55d0d-115">How to: Create a Custom Client Identity Verifier</span></span>](how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="55d0d-116">Ukazuje, jak ověřit identitu vlastního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="55d0d-116">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="55d0d-117">Postupy: Použití samostatných certifikátů X. 509 pro podepisování a šifrování</span><span class="sxs-lookup"><span data-stu-id="55d0d-117">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="55d0d-118">Zprávy jsou obvykle podepsané a šifrované pomocí jednoho certifikátu.</span><span class="sxs-lookup"><span data-stu-id="55d0d-118">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="55d0d-119">V tomto tématu se dozvíte, jak můžou být v případě potřeby použity dva certifikáty.</span><span class="sxs-lookup"><span data-stu-id="55d0d-119">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="55d0d-120">Postupy: Změna zprostředkovatele kryptografických služeb pro privátní klíč certifikátu X. 509</span><span class="sxs-lookup"><span data-stu-id="55d0d-120">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="55d0d-121">Vysvětluje, jak změnit zprostředkovatele kryptografických služeb, který poskytuje privátní klíč certifikátu X. 509 a jak integrovat zprostředkovatele do architektury Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="55d0d-121">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the Windows Communication Foundation (WCF) framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="55d0d-122">Reference</span><span class="sxs-lookup"><span data-stu-id="55d0d-122">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="55d0d-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="55d0d-123">Related Sections</span></span>  
 [<span data-ttu-id="55d0d-124">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="55d0d-124">Security</span></span>](../feature-details/security.md)  
  
 [<span data-ttu-id="55d0d-125">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="55d0d-125">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="55d0d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55d0d-126">See also</span></span>

- [<span data-ttu-id="55d0d-127">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="55d0d-127">Security Overview</span></span>](../feature-details/security-overview.md)
