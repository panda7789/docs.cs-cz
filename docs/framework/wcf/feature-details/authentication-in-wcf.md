---
title: Ověřování ve WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: ebff66e185bdca75a0150b22a16392bfd08892d3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165463"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="4b782-102">Ověřování ve WCF</span><span class="sxs-lookup"><span data-stu-id="4b782-102">Authentication in WCF</span></span>
<span data-ttu-id="4b782-103">Následující témata ukazují celou řadou různých mechanismů ve Windows Communication Foundation (WCF), které poskytují ověřování, například, ověřování Windows, certifikáty X.509 a uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="4b782-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b782-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4b782-104">In This Section</span></span>  
 [<span data-ttu-id="4b782-105">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4b782-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="4b782-106">Funkce ASP.NET zahrnují členství a zprostředkovatel rolí, databázi k ukládání párů jméno/heslo uživatele pro ověřování a uživatelských rolí pro autorizaci.</span><span class="sxs-lookup"><span data-stu-id="4b782-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="4b782-107">Toto téma vysvětluje, jak můžete používat stejnou databázi k ověřování a autorizaci uživatelů služby WCF.</span><span class="sxs-lookup"><span data-stu-id="4b782-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="4b782-108">Postupy: Použití validátoru vlastního uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="4b782-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="4b782-109">Ukazuje, jak integrovat validátor vlastní uživatelské jméno/heslo.</span><span class="sxs-lookup"><span data-stu-id="4b782-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="4b782-110">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="4b782-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="4b782-111">Jako dodatečné zabezpečení, klient může ověřit službu tak, že zadáte očekávané *identity* služby.</span><span class="sxs-lookup"><span data-stu-id="4b782-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="4b782-112">Pokud je Očekávaná identita neshodují identity vrácené službou, ověření se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="4b782-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="4b782-113">Vyjednávání a časové limity zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4b782-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="4b782-114">Popisuje způsob použití <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> vlastnost <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídy.</span><span class="sxs-lookup"><span data-stu-id="4b782-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="4b782-115">Ladění chyb ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="4b782-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="4b782-116">Zaměřuje se na běžné problémy při použití ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="4b782-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4b782-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="4b782-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="4b782-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4b782-118">Related Sections</span></span>  
 [<span data-ttu-id="4b782-119">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4b782-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="4b782-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b782-120">See also</span></span>

- [<span data-ttu-id="4b782-121">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4b782-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="4b782-122">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="4b782-122">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
