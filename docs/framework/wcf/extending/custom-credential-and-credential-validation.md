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
ms.openlocfilehash: 3b1ff700010f471a4d9be117f363083b6cbed493
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210630"
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="f9ea5-102">Vlastní pověření a ověřování pověření</span><span class="sxs-lookup"><span data-stu-id="f9ea5-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="f9ea5-103">Zabezpečení Windows Communication Foundation (WCF) je založeno na výměnou přihlašovacích údajů mezi služeb a klientů.</span><span class="sxs-lookup"><span data-stu-id="f9ea5-103">Security in Windows Communication Foundation (WCF) is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="f9ea5-104">Většina scénářů zabezpečení je možné splnit pomocí běžných typů přihlašovacích údajů, jako jsou Windows (Kerberos), uživatelského jména a hesla a certifikáty.</span><span class="sxs-lookup"><span data-stu-id="f9ea5-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="f9ea5-105">Ale pokud se vyžaduje nový typ přihlašovacích údajů, témata v této části popisují, jak zpracovat a nové typy ověření.</span><span class="sxs-lookup"><span data-stu-id="f9ea5-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f9ea5-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f9ea5-106">In This Section</span></span>  
 [<span data-ttu-id="f9ea5-107">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="f9ea5-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="f9ea5-108">Vysvětluje, jak přizpůsobit WCF ověření děděním z <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="f9ea5-108">Explains how to customize WCF validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="f9ea5-109">Návod: Vytvoření vlastního klienta a pověření služby</span><span class="sxs-lookup"><span data-stu-id="f9ea5-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="f9ea5-110">Ukazuje, jak rozšířit <xref:System.ServiceModel.Description.ClientCredentials> a <xref:System.ServiceModel.Description.ServiceCredentials> třídy tak, aby vyhovovaly nových přihlašovacích údajů typy.</span><span class="sxs-lookup"><span data-stu-id="f9ea5-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="f9ea5-111">Toto je první v řadě témat, které umožňují vytváření typů vlastních přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="f9ea5-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="f9ea5-112">Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f9ea5-112">How to: Create a Custom Security Token Provider</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="f9ea5-113">Vysvětluje, jak vytvořit poskytovatele tokenu zabezpečení ke zpracování nových typů přihlašovacích údajů a vrátí nové tokeny pro přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="f9ea5-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="f9ea5-114">Toto je druhá téma v řadě.</span><span class="sxs-lookup"><span data-stu-id="f9ea5-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="f9ea5-115">Postupy: Vytvořit vlastní bezpečnostní ověřovací data tokenu</span><span class="sxs-lookup"><span data-stu-id="f9ea5-115">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="f9ea5-116">Vysvětluje, jak vytvořit vlastní ověřovací data k ověření nový typ přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="f9ea5-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="f9ea5-117">Toto je třetí téma v řadě.</span><span class="sxs-lookup"><span data-stu-id="f9ea5-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f9ea5-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="f9ea5-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="f9ea5-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f9ea5-119">Related Sections</span></span>  
 [<span data-ttu-id="f9ea5-120">Ověřování</span><span class="sxs-lookup"><span data-stu-id="f9ea5-120">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="f9ea5-121">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="f9ea5-121">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="f9ea5-122">Autorizace</span><span class="sxs-lookup"><span data-stu-id="f9ea5-122">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="f9ea5-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9ea5-123">See also</span></span>

- [<span data-ttu-id="f9ea5-124">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f9ea5-124">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
