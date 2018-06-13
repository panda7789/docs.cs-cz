---
title: Ověřování ve WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: a4f9b719024db1334b599f0f02fe01bc083bf3c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489107"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="b20cf-102">Ověřování ve WCF</span><span class="sxs-lookup"><span data-stu-id="b20cf-102">Authentication in WCF</span></span>
<span data-ttu-id="b20cf-103">Následující témata ukazují počet různé mechanismy ve Windows Communication Foundation (WCF), ověřování, například zadáte, ověřování systému Windows, certifikáty X.509 a uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="b20cf-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b20cf-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b20cf-104">In This Section</span></span>  
 [<span data-ttu-id="b20cf-105">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b20cf-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="b20cf-106">Funkce ASP.NET zahrnují členství a zprostředkovatele rolí, databázi k ukládání páry uživatelské jméno a heslo pro ověřování a role uživatele pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="b20cf-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="b20cf-107">Toto téma vysvětluje, jak můžete použít stejnou databázi k ověřování a autorizaci uživatelů služby WCF.</span><span class="sxs-lookup"><span data-stu-id="b20cf-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="b20cf-108">Postupy: Použití validátoru vlastního uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="b20cf-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="b20cf-109">Ukazuje, jak integrovat validátor vlastní uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="b20cf-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="b20cf-110">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="b20cf-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="b20cf-111">Jako další ochranná, klient může ověřit službu zadáním očekávané *identity* služby.</span><span class="sxs-lookup"><span data-stu-id="b20cf-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="b20cf-112">Pokud očekávaný identity a identity vrácený službou neshodují, ověření se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="b20cf-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="b20cf-113">Vyjednávání a časové limity zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b20cf-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="b20cf-114">Popisuje způsob použití <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> vlastnost v <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídy.</span><span class="sxs-lookup"><span data-stu-id="b20cf-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="b20cf-115">Ladění chyb u ověřování Windows</span><span class="sxs-lookup"><span data-stu-id="b20cf-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="b20cf-116">Zaměřuje se na běžné problémy při použití ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b20cf-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b20cf-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="b20cf-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="b20cf-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b20cf-118">Related Sections</span></span>  
 [<span data-ttu-id="b20cf-119">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b20cf-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="b20cf-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b20cf-120">See Also</span></span>  
 [<span data-ttu-id="b20cf-121">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b20cf-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="b20cf-122">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="b20cf-122">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
