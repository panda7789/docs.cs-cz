---
title: Ověřování ve WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: b513c9713bd2c04e125915d1a0a87c86ce249666
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597641"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="450fa-102">Ověřování ve WCF</span><span class="sxs-lookup"><span data-stu-id="450fa-102">Authentication in WCF</span></span>
<span data-ttu-id="450fa-103">V následujících tématech najdete řadu různých mechanismů v Windows Communication Foundation (WCF), které poskytují ověřování, například ověřování systému Windows, certifikáty X. 509 a uživatelské jméno a hesla.</span><span class="sxs-lookup"><span data-stu-id="450fa-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="450fa-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="450fa-104">In This Section</span></span>  
 [<span data-ttu-id="450fa-105">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="450fa-105">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="450fa-106">Funkce ASP.NET zahrnují členství a poskytovatele rolí, databázi pro ukládání párů uživatelských jmen a hesel pro ověřování a role uživatelů pro autorizaci.</span><span class="sxs-lookup"><span data-stu-id="450fa-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="450fa-107">Toto téma vysvětluje, jak můžou služby WCF používat stejnou databázi k ověřování a autorizaci uživatelů.</span><span class="sxs-lookup"><span data-stu-id="450fa-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="450fa-108">Postupy: Použití validátoru vlastního uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="450fa-108">How to: Use a Custom User Name and Password Validator</span></span>](how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="450fa-109">Ukazuje, jak integrovat vlastní validátor uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="450fa-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="450fa-110">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="450fa-110">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)  
 <span data-ttu-id="450fa-111">Jako dodatečná ochrana může klient ověřit službu zadáním očekávané *identity* služby.</span><span class="sxs-lookup"><span data-stu-id="450fa-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="450fa-112">Pokud Očekávaná identita a identita, kterou služba vrátila, se neshodují, ověřování se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="450fa-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="450fa-113">Vyjednávání a časové limity zabezpečení</span><span class="sxs-lookup"><span data-stu-id="450fa-113">Security Negotiation and Timeouts</span></span>](security-negotiation-and-timeouts.md)  
 <span data-ttu-id="450fa-114">Popisuje, jak použít <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> vlastnost ve <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídě.</span><span class="sxs-lookup"><span data-stu-id="450fa-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="450fa-115">Ladění chyb u ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="450fa-115">Debugging Windows Authentication Errors</span></span>](debugging-windows-authentication-errors.md)  
 <span data-ttu-id="450fa-116">Při použití ověřování systému Windows se zaměřuje na běžné problémy, ke kterým došlo.</span><span class="sxs-lookup"><span data-stu-id="450fa-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="450fa-117">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="450fa-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="450fa-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="450fa-118">Related Sections</span></span>  
 [<span data-ttu-id="450fa-119">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="450fa-119">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="450fa-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="450fa-120">See also</span></span>

- [<span data-ttu-id="450fa-121">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="450fa-121">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="450fa-122">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="450fa-122">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
