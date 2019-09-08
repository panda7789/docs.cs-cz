---
title: Vlastní pověření a ověřování pověření
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: 1418d4155bc7f2fefc9f3e6caf4d3a264747a667
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795816"
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="13f0c-102">Vlastní pověření a ověřování pověření</span><span class="sxs-lookup"><span data-stu-id="13f0c-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="13f0c-103">Zabezpečení v Windows Communication Foundation (WCF) je založené na výměně přihlašovacích údajů mezi službami a klienty.</span><span class="sxs-lookup"><span data-stu-id="13f0c-103">Security in Windows Communication Foundation (WCF) is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="13f0c-104">Většinu scénářů zabezpečení je možné vyhovět pomocí běžných typů přihlašovacích údajů, jako je Windows (Kerberos), uživatelské jméno a hesla a certifikáty.</span><span class="sxs-lookup"><span data-stu-id="13f0c-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="13f0c-105">Pokud je však požadován nový typ přihlašovacích údajů, témata v této části vysvětlují, jak zpracovávat a ověřovat nové typy.</span><span class="sxs-lookup"><span data-stu-id="13f0c-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13f0c-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="13f0c-106">In This Section</span></span>  
 [<span data-ttu-id="13f0c-107">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="13f0c-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="13f0c-108">Vysvětluje, jak přizpůsobit ověřování WCF děděním z <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="13f0c-108">Explains how to customize WCF validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="13f0c-109">Návod: Vytváření vlastních přihlašovacích údajů klienta a služby</span><span class="sxs-lookup"><span data-stu-id="13f0c-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="13f0c-110">Ukazuje, jak rozšiřuje <xref:System.ServiceModel.Description.ClientCredentials> třídy a <xref:System.ServiceModel.Description.ServiceCredentials> pro přizpůsobení nových typů přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="13f0c-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="13f0c-111">Toto je první v řadě témat, která umožňují vytváření vlastních typů přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="13f0c-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="13f0c-112">Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="13f0c-112">How to: Create a Custom Security Token Provider</span></span>](how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="13f0c-113">Vysvětluje, jak vytvořit poskytovatele tokenu zabezpečení, který bude zpracovávat nové typy přihlašovacích údajů a vracet nové tokeny pro přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="13f0c-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="13f0c-114">Toto je druhé téma v řadě.</span><span class="sxs-lookup"><span data-stu-id="13f0c-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="13f0c-115">Postupy: Vytvořit vlastní ověřovací data tokenu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="13f0c-115">How to: Create a Custom Security Token Authenticator</span></span>](how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="13f0c-116">Vysvětluje, jak vytvořit vlastní ověřovací data pro ověření nového typu přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="13f0c-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="13f0c-117">Toto je třetí téma v řadě.</span><span class="sxs-lookup"><span data-stu-id="13f0c-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="13f0c-118">Reference</span><span class="sxs-lookup"><span data-stu-id="13f0c-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="13f0c-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="13f0c-119">Related Sections</span></span>  
 [<span data-ttu-id="13f0c-120">Ověřování</span><span class="sxs-lookup"><span data-stu-id="13f0c-120">Authentication</span></span>](../feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="13f0c-121">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="13f0c-121">Federation and Issued Tokens</span></span>](../feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="13f0c-122">Autorizace</span><span class="sxs-lookup"><span data-stu-id="13f0c-122">Authorization</span></span>](../feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="13f0c-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13f0c-123">See also</span></span>

- [<span data-ttu-id="13f0c-124">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="13f0c-124">Security</span></span>](../feature-details/security.md)
