---
title: "Ověřování ve WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9a08627e213196c2d5fb296f458a5d3a8c7bb1a0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="31128-102">Ověřování ve WCF</span><span class="sxs-lookup"><span data-stu-id="31128-102">Authentication in WCF</span></span>
<span data-ttu-id="31128-103">Následující témata ukazují počet různých mechanismech [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] , poskytovat ověřování, například, ověřování systému Windows, certifikáty X.509 a uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="31128-103">The following topics show a number of different mechanisms in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="31128-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="31128-104">In This Section</span></span>  
 [<span data-ttu-id="31128-105">Postupy: použití poskytovatele členství prostředí ASP.NET</span><span class="sxs-lookup"><span data-stu-id="31128-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="31128-106">Funkce ASP.NET zahrnují členství a zprostředkovatele rolí, databázi k ukládání páry uživatelské jméno a heslo pro ověřování a role uživatele pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="31128-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="31128-107">Toto téma vysvětluje, jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby můžete použít stejnou databázi k ověřování a autorizaci uživatelů.</span><span class="sxs-lookup"><span data-stu-id="31128-107">This topic explains how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="31128-108">Postupy: použití vlastního uživatelského jména a hesla validátoru</span><span class="sxs-lookup"><span data-stu-id="31128-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="31128-109">Ukazuje, jak integrovat validátor vlastní uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="31128-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="31128-110">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="31128-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="31128-111">Jako další ochranná, klient může ověřit službu zadáním očekávané *identity* služby.</span><span class="sxs-lookup"><span data-stu-id="31128-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="31128-112">Pokud očekávaný identity a identity vrácený službou neshodují, ověření se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="31128-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="31128-113">Zabezpečení vyjednávání a časové limity</span><span class="sxs-lookup"><span data-stu-id="31128-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="31128-114">Popisuje způsob použití <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> vlastnost v <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídy.</span><span class="sxs-lookup"><span data-stu-id="31128-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="31128-115">Ladění chyb ověřování systému Windows</span><span class="sxs-lookup"><span data-stu-id="31128-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="31128-116">Zaměřuje se na běžné problémy při použití ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="31128-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="31128-117">Odkaz</span><span class="sxs-lookup"><span data-stu-id="31128-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="31128-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="31128-118">Related Sections</span></span>  
 [<span data-ttu-id="31128-119">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="31128-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="31128-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="31128-120">See Also</span></span>  
 [<span data-ttu-id="31128-121">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="31128-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="31128-122">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="31128-122">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
