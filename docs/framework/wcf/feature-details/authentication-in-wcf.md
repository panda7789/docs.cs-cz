---
title: Ověřování ve WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: abe7aff025207ad8bdf8657daba3584e6a1b2e7f
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964697"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="67e4b-102">Ověřování ve WCF</span><span class="sxs-lookup"><span data-stu-id="67e4b-102">Authentication in WCF</span></span>
<span data-ttu-id="67e4b-103">V následujících tématech najdete řadu různých mechanismů v Windows Communication Foundation (WCF), které poskytují ověřování, například ověřování systému Windows, certifikáty X. 509 a uživatelské jméno a hesla.</span><span class="sxs-lookup"><span data-stu-id="67e4b-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="67e4b-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="67e4b-104">In This Section</span></span>  
 [<span data-ttu-id="67e4b-105">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="67e4b-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="67e4b-106">Funkce ASP.NET zahrnují členství a poskytovatele rolí, databázi pro ukládání párů uživatelských jmen a hesel pro ověřování a role uživatelů pro autorizaci.</span><span class="sxs-lookup"><span data-stu-id="67e4b-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="67e4b-107">Toto téma vysvětluje, jak můžou služby WCF používat stejnou databázi k ověřování a autorizaci uživatelů.</span><span class="sxs-lookup"><span data-stu-id="67e4b-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="67e4b-108">Postupy: Použití validátoru vlastního uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="67e4b-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="67e4b-109">Ukazuje, jak integrovat vlastní validátor uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="67e4b-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="67e4b-110">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="67e4b-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="67e4b-111">Jako dodatečná ochrana může klient ověřit službu zadáním očekávané *identity* služby.</span><span class="sxs-lookup"><span data-stu-id="67e4b-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="67e4b-112">Pokud Očekávaná identita a identita, kterou služba vrátila, se neshodují, ověřování se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="67e4b-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="67e4b-113">Vyjednávání a časové limity zabezpečení</span><span class="sxs-lookup"><span data-stu-id="67e4b-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="67e4b-114">Popisuje, jak použít vlastnost <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> ve třídě <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>.</span><span class="sxs-lookup"><span data-stu-id="67e4b-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="67e4b-115">Ladění chyb u ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="67e4b-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="67e4b-116">Při použití ověřování systému Windows se zaměřuje na běžné problémy, ke kterým došlo.</span><span class="sxs-lookup"><span data-stu-id="67e4b-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="67e4b-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="67e4b-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="67e4b-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="67e4b-118">Related Sections</span></span>  
 [<span data-ttu-id="67e4b-119">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="67e4b-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="67e4b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67e4b-120">See also</span></span>

- [<span data-ttu-id="67e4b-121">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="67e4b-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="67e4b-122">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="67e4b-122">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
