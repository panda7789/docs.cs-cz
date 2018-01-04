---
title: "Postupy: vytvoření vlastní objekt Identity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 393bc7a33a522f483dc4daf1531c23afe421c261
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-principal-identity"></a><span data-ttu-id="467ad-102">Postupy: vytvoření vlastní objekt Identity</span><span class="sxs-lookup"><span data-stu-id="467ad-102">How to: Create a Custom Principal Identity</span></span>
<span data-ttu-id="467ad-103"><xref:System.Security.Permissions.PrincipalPermissionAttribute> Je deklarativní způsob řízení přístupu metod služby.</span><span class="sxs-lookup"><span data-stu-id="467ad-103">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is a declarative means of controlling access to service methods.</span></span> <span data-ttu-id="467ad-104">Při použití tohoto atributu <xref:System.ServiceModel.Description.PrincipalPermissionMode> výčet Určuje režim pro provedení kontroly autorizace.</span><span class="sxs-lookup"><span data-stu-id="467ad-104">When using this attribute, the <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeration specifies the mode for performing authorization checks.</span></span> <span data-ttu-id="467ad-105">Když tento režim je nastaven na <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, umožní uživateli zadat vlastní <xref:System.Security.Principal.IPrincipal> třída vrácený <xref:System.Threading.Thread.CurrentPrincipal%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="467ad-105">When this mode is set to <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, it enables the user to specify a custom <xref:System.Security.Principal.IPrincipal> class returned by the <xref:System.Threading.Thread.CurrentPrincipal%2A> property.</span></span> <span data-ttu-id="467ad-106">Toto téma ukazuje scénář při <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> se používá v kombinaci s vlastní zásady autorizace a vlastní objekt.</span><span class="sxs-lookup"><span data-stu-id="467ad-106">This topic illustrates the scenario when <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> is used in combination with a custom authorization policy and a custom principal.</span></span>  
  
 <span data-ttu-id="467ad-107">Další informace o používání <xref:System.Security.Permissions.PrincipalPermissionAttribute>, najdete v části [postupy: omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="467ad-107">For more information about using the <xref:System.Security.Permissions.PrincipalPermissionAttribute>, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="467ad-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="467ad-108">Example</span></span>  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="467ad-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="467ad-109">Compiling the Code</span></span>  
 <span data-ttu-id="467ad-110">Odkazy na následující obory názvů jsou potřeba pro kompilaci kódu:</span><span class="sxs-lookup"><span data-stu-id="467ad-110">References to the following namespaces are needed to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.Collections.Generic>  
  
-   <xref:System.Security.Permissions>  
  
-   <xref:System.Security.Principal>  
  
-   <xref:System.Threading>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Description>  
  
-   <xref:System.IdentityModel.Claims>  
  
-   <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a><span data-ttu-id="467ad-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="467ad-111">See Also</span></span>  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [<span data-ttu-id="467ad-112">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="467ad-112">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [<span data-ttu-id="467ad-113">Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="467ad-113">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
