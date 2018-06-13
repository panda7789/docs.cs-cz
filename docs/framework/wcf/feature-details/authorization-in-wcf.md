---
title: Autorizace ve WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: c6bf779c7baeea1f9a253ad0bde966cea67b57aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488569"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="72caa-102">Autorizace ve WCF</span><span class="sxs-lookup"><span data-stu-id="72caa-102">Authorization in WCF</span></span>
<span data-ttu-id="72caa-103">Autorizace je proces řízení přístupu a oprávnění k prostředkům, jako jsou služby nebo soubory.</span><span class="sxs-lookup"><span data-stu-id="72caa-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="72caa-104">Témata v této části ukazují, jak to provést základní ve Windows Communication Foundation (WCF) v mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="72caa-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72caa-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="72caa-105">In This Section</span></span>  
 [<span data-ttu-id="72caa-106">Mechanismy řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="72caa-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="72caa-107">Poskytuje stručný obrys mechanismy ověřování ve WCF a navrhované používá.</span><span class="sxs-lookup"><span data-stu-id="72caa-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="72caa-108">Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="72caa-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="72caa-109">Proces omezení přístupu ke službě se zobrazuje <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="72caa-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="72caa-110">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="72caa-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="72caa-111">Provede konfiguraci této služby ji používat funkci poskytovatele role zapnout [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="72caa-111">Walks through the configuration of a service to enable it to use the role provider feature of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span></span>  
  
 [<span data-ttu-id="72caa-112">Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="72caa-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="72caa-113"> Správce autorizací můžete použít ke správě ověřování pro webovou stránku.</span><span class="sxs-lookup"><span data-stu-id="72caa-113"> can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="72caa-114">Podobně můžete využít WCF [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/Authorization správce kombinaci pro ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="72caa-114">WCF can similarly leverage the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="72caa-115">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="72caa-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="72caa-116">Vysvětluje základy používání infrastruktury modelu Identity pro ověřování založené na deklaracích identity.</span><span class="sxs-lookup"><span data-stu-id="72caa-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="72caa-117">Delegace a zosobnění</span><span class="sxs-lookup"><span data-stu-id="72caa-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="72caa-118">Vysvětluje rozdíl mezi delegace a zosobnění.</span><span class="sxs-lookup"><span data-stu-id="72caa-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="72caa-119">Odkaz</span><span class="sxs-lookup"><span data-stu-id="72caa-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="72caa-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="72caa-120">Related Sections</span></span>  
 [<span data-ttu-id="72caa-121">Ověřování</span><span class="sxs-lookup"><span data-stu-id="72caa-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="72caa-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="72caa-122">See Also</span></span>  
 [<span data-ttu-id="72caa-123">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="72caa-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="72caa-124">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="72caa-124">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
