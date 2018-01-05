---
title: Autorizace ve WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac43b2185048287d0edd4cb20561a936bce2f58b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="authorization-in-wcf"></a>Autorizace ve WCF
Autorizace je proces řízení přístupu a oprávnění k prostředkům, jako jsou služby nebo soubory. Témata v této části popisují, jak to provést základní v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mnoha různými způsoby.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mechanismy řízení přístupu](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 Poskytuje stručný obrys mechanismy ověřování ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]a navrhované používá.  
  
 [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 Proces omezení přístupu ke službě se zobrazuje <xref:System.Security.Permissions.PrincipalPermissionAttribute>.  
  
 [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 Provede konfiguraci této služby ji používat funkci poskytovatele role zapnout [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
 [Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Správce autorizací můžete použít ke správě ověřování pro webovou stránku. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Podobně můžete využít [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/Authorization správce kombinaci pro ověřování klientů.  
  
 [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 Vysvětluje základy používání infrastruktury modelu Identity pro ověřování založené na deklaracích identity.  
  
 [Delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 Vysvětluje rozdíl mezi delegace a zosobnění.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a>Související oddíly  
 [Ověřování](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a>Viz také  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
