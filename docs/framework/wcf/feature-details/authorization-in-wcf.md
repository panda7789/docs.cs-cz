---
title: Autorizace ve WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 0097adc3d9677d9ce5595a3ac632b51d94d53f6f
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964686"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="44f23-102">Autorizace ve WCF</span><span class="sxs-lookup"><span data-stu-id="44f23-102">Authorization in WCF</span></span>
<span data-ttu-id="44f23-103">Autorizace je proces řízení přístupu a práv k prostředkům, jako jsou služby nebo soubory.</span><span class="sxs-lookup"><span data-stu-id="44f23-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="44f23-104">Témata v této části ukazují, jak provést tuto základní úlohu v Windows Communication Foundation (WCF) mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="44f23-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44f23-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="44f23-105">In This Section</span></span>  
 [<span data-ttu-id="44f23-106">Mechanismy řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="44f23-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="44f23-107">Poskytuje stručný přehled mechanismů autorizace ve službě WCF a navrhovaná použití.</span><span class="sxs-lookup"><span data-stu-id="44f23-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="44f23-108">Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="44f23-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="44f23-109">Zobrazuje proces omezení přístupu ke službě pomocí <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="44f23-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="44f23-110">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="44f23-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="44f23-111">Provede vás konfigurací služby, aby mohla používat funkci poskytovatele rolí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="44f23-111">Walks through the configuration of a service to enable it to use the role provider feature of ASP.NET.</span></span>  
  
 [<span data-ttu-id="44f23-112">Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="44f23-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 <span data-ttu-id="44f23-113">ASP.NET může pomocí Správce autorizací spravovat autorizaci webu.</span><span class="sxs-lookup"><span data-stu-id="44f23-113">ASP.NET can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="44f23-114">WCF může podobně využít kombinaci ASP.NET/Authorization Manageru pro autorizaci klientů.</span><span class="sxs-lookup"><span data-stu-id="44f23-114">WCF can similarly leverage the ASP.NET/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="44f23-115">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="44f23-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="44f23-116">Vysvětluje základy používání infrastruktury modelu identity pro autorizaci založenou na deklaracích.</span><span class="sxs-lookup"><span data-stu-id="44f23-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="44f23-117">Delegace a zosobnění</span><span class="sxs-lookup"><span data-stu-id="44f23-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="44f23-118">Vysvětluje rozdíl mezi delegováním a zosobněním.</span><span class="sxs-lookup"><span data-stu-id="44f23-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="44f23-119">Odkaz</span><span class="sxs-lookup"><span data-stu-id="44f23-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="44f23-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="44f23-120">Related Sections</span></span>  
 [<span data-ttu-id="44f23-121">Ověřování</span><span class="sxs-lookup"><span data-stu-id="44f23-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="44f23-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44f23-122">See also</span></span>

- [<span data-ttu-id="44f23-123">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="44f23-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="44f23-124">[Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="44f23-124">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
