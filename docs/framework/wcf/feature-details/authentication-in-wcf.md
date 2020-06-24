---
title: Ověřování ve WCF
description: Přečtěte si o několika mechanismech služby WCF, které poskytují ověřování, jako je ověřování systému Windows, certifikáty X. 509 a uživatelské jméno a heslo.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: 4c3348cfb84b8571dc1f24b774ffcd691aaa5001
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247517"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="11acc-103">Ověřování ve WCF</span><span class="sxs-lookup"><span data-stu-id="11acc-103">Authentication in WCF</span></span>
<span data-ttu-id="11acc-104">V následujících tématech najdete řadu různých mechanismů v Windows Communication Foundation (WCF), které poskytují ověřování, například ověřování systému Windows, certifikáty X. 509 a uživatelské jméno a hesla.</span><span class="sxs-lookup"><span data-stu-id="11acc-104">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11acc-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="11acc-105">In This Section</span></span>  
 [<span data-ttu-id="11acc-106">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="11acc-106">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="11acc-107">Funkce ASP.NET zahrnují členství a poskytovatele rolí, databázi pro ukládání párů uživatelských jmen a hesel pro ověřování a role uživatelů pro autorizaci.</span><span class="sxs-lookup"><span data-stu-id="11acc-107">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="11acc-108">Toto téma vysvětluje, jak můžou služby WCF používat stejnou databázi k ověřování a autorizaci uživatelů.</span><span class="sxs-lookup"><span data-stu-id="11acc-108">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="11acc-109">Postupy: Použití validátoru vlastního uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="11acc-109">How to: Use a Custom User Name and Password Validator</span></span>](how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="11acc-110">Ukazuje, jak integrovat vlastní validátor uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="11acc-110">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="11acc-111">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="11acc-111">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)  
 <span data-ttu-id="11acc-112">Jako dodatečná ochrana může klient ověřit službu zadáním očekávané *identity* služby.</span><span class="sxs-lookup"><span data-stu-id="11acc-112">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="11acc-113">Pokud Očekávaná identita a identita, kterou služba vrátila, se neshodují, ověřování se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="11acc-113">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="11acc-114">Vyjednávání a časové limity zabezpečení</span><span class="sxs-lookup"><span data-stu-id="11acc-114">Security Negotiation and Timeouts</span></span>](security-negotiation-and-timeouts.md)  
 <span data-ttu-id="11acc-115">Popisuje, jak použít <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> vlastnost ve <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídě.</span><span class="sxs-lookup"><span data-stu-id="11acc-115">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="11acc-116">Ladění chyb u ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="11acc-116">Debugging Windows Authentication Errors</span></span>](debugging-windows-authentication-errors.md)  
 <span data-ttu-id="11acc-117">Při použití ověřování systému Windows se zaměřuje na běžné problémy, ke kterým došlo.</span><span class="sxs-lookup"><span data-stu-id="11acc-117">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="11acc-118">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="11acc-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="11acc-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="11acc-119">Related Sections</span></span>  
 [<span data-ttu-id="11acc-120">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="11acc-120">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="11acc-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="11acc-121">See also</span></span>

- [<span data-ttu-id="11acc-122">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="11acc-122">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="11acc-123">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="11acc-123">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
