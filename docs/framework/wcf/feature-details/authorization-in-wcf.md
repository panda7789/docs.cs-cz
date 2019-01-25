---
title: Autorizace ve WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 51bf3c81962c6981affdb96261fc41211142e46d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645545"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="14ee0-102">Autorizace ve WCF</span><span class="sxs-lookup"><span data-stu-id="14ee0-102">Authorization in WCF</span></span>
<span data-ttu-id="14ee0-103">Autorizace je proces řízení přístupu a oprávnění k prostředkům, jako jsou služby nebo soubory.</span><span class="sxs-lookup"><span data-stu-id="14ee0-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="14ee0-104">Témata v této části ukazují, jak k provedení této základní úlohy ve Windows Communication Foundation (WCF) v mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="14ee0-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14ee0-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="14ee0-105">In This Section</span></span>  
 [<span data-ttu-id="14ee0-106">Mechanismy řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="14ee0-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="14ee0-107">Poskytuje stručný přehled autorizačních mechanismů v WCF a navrhované používá.</span><span class="sxs-lookup"><span data-stu-id="14ee0-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="14ee0-108">Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="14ee0-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="14ee0-109">Omezení přístupu ke službě s procesem se zobrazí <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="14ee0-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="14ee0-110">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="14ee0-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="14ee0-111">Provede konfiguraci této služby, který umožňuje použít funkci zprostředkovatele rolí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14ee0-111">Walks through the configuration of a service to enable it to use the role provider feature of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span></span>  
  
 [<span data-ttu-id="14ee0-112">Postupy: Použití zprostředkovatele Role Správce autorizací ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="14ee0-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] <span data-ttu-id="14ee0-113">Správce autorizací můžete použít ke správě autorizace pro webový server.</span><span class="sxs-lookup"><span data-stu-id="14ee0-113">can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="14ee0-114">Podobně můžou využít WCF [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]kombinaci /Authorization správce pro autorizaci klientů.</span><span class="sxs-lookup"><span data-stu-id="14ee0-114">WCF can similarly leverage the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="14ee0-115">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="14ee0-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="14ee0-116">Popisuje základní informace o používání infrastruktury modelu identit pro ověřování na základě deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="14ee0-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="14ee0-117">Delegace a zosobnění</span><span class="sxs-lookup"><span data-stu-id="14ee0-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="14ee0-118">Vysvětluje rozdíl mezi delegace a zosobnění.</span><span class="sxs-lookup"><span data-stu-id="14ee0-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="14ee0-119">Odkaz</span><span class="sxs-lookup"><span data-stu-id="14ee0-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="14ee0-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="14ee0-120">Related Sections</span></span>  
 [<span data-ttu-id="14ee0-121">Ověřování</span><span class="sxs-lookup"><span data-stu-id="14ee0-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="14ee0-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14ee0-122">See also</span></span>
- [<span data-ttu-id="14ee0-123">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="14ee0-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="14ee0-124">Model zabezpečení pro Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="14ee0-124">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
