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
# <a name="authorization-in-wcf"></a>Autorizace ve WCF
Autorizace je proces řízení přístupu a oprávnění k prostředkům, jako jsou služby nebo soubory. Témata v této části ukazují, jak k provedení této základní úlohy ve Windows Communication Foundation (WCF) v mnoha různými způsoby.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mechanismy řízení přístupu](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 Poskytuje stručný přehled autorizačních mechanismů v WCF a navrhované používá.  
  
 [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 Omezení přístupu ke službě s procesem se zobrazí <xref:System.Security.Permissions.PrincipalPermissionAttribute>.  
  
 [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 Provede konfiguraci této služby, který umožňuje použít funkci zprostředkovatele rolí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
 [Postupy: Použití zprostředkovatele Role Správce autorizací ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Správce autorizací můžete použít ke správě autorizace pro webový server. Podobně můžou využít WCF [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]kombinaci /Authorization správce pro autorizaci klientů.  
  
 [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 Popisuje základní informace o používání infrastruktury modelu identit pro ověřování na základě deklarací identity.  
  
 [Delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 Vysvětluje rozdíl mezi delegace a zosobnění.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a>Související oddíly  
 [Ověřování](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a>Viz také:
- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
