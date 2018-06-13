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
ms.openlocfilehash: 9b340c01a9eb4ce4007e93f2b38e292cd6543ba1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803450"
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="76cf0-102">Vlastní pověření a ověřování pověření</span><span class="sxs-lookup"><span data-stu-id="76cf0-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="76cf0-103">Zabezpečení ve Windows Communication Foundation (WCF) je založena na výměnu přihlašovacích údajů mezi služeb a klientů.</span><span class="sxs-lookup"><span data-stu-id="76cf0-103">Security in Windows Communication Foundation (WCF) is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="76cf0-104">Většina scénářů zabezpečení může obsloužit pomocí běžné typy přihlašovacích údajů, jako jsou Windows (Kerberos), uživatelského jména a hesla a certifikáty.</span><span class="sxs-lookup"><span data-stu-id="76cf0-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="76cf0-105">Ale pokud nový typ pověření je zapotřebí, témata v této části popisují, jak ke zpracování a ověření nové typy.</span><span class="sxs-lookup"><span data-stu-id="76cf0-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="76cf0-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="76cf0-106">In This Section</span></span>  
 [<span data-ttu-id="76cf0-107">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="76cf0-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="76cf0-108">Vysvětluje, jak přizpůsobit WCF ověření, která dědí z <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="76cf0-108">Explains how to customize WCF validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="76cf0-109">Návod: Vytvoření vlastních přihlašovacích údajů klienta a služby</span><span class="sxs-lookup"><span data-stu-id="76cf0-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="76cf0-110">Ukazuje, jak rozšířit <xref:System.ServiceModel.Description.ClientCredentials> a <xref:System.ServiceModel.Description.ServiceCredentials> třídy pro uložení nové přihlašovací údaje typy.</span><span class="sxs-lookup"><span data-stu-id="76cf0-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="76cf0-111">Toto je první v řadě témata, které umožňují vytváření typů vlastní pověření.</span><span class="sxs-lookup"><span data-stu-id="76cf0-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="76cf0-112">Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="76cf0-112">How to: Create a Custom Security Token Provider</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="76cf0-113">Vysvětluje, jak vytvořit poskytovatele tokenu zabezpečení ke zpracování nových typů přihlašovacích údajů a vrátí nové tokeny pro přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="76cf0-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="76cf0-114">Toto je druhý téma v řadě.</span><span class="sxs-lookup"><span data-stu-id="76cf0-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="76cf0-115">Postupy: Vytvoření vlastních ověřovacích dat tokenu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="76cf0-115">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="76cf0-116">Vysvětluje, jak vytvořit vlastní ověřovací k ověření nový typ přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="76cf0-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="76cf0-117">Toto je třetí téma v řadě.</span><span class="sxs-lookup"><span data-stu-id="76cf0-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="76cf0-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="76cf0-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="76cf0-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="76cf0-119">Related Sections</span></span>  
 [<span data-ttu-id="76cf0-120">Ověřování</span><span class="sxs-lookup"><span data-stu-id="76cf0-120">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="76cf0-121">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="76cf0-121">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="76cf0-122">Autorizace</span><span class="sxs-lookup"><span data-stu-id="76cf0-122">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="76cf0-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="76cf0-123">See Also</span></span>  
 [<span data-ttu-id="76cf0-124">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="76cf0-124">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
