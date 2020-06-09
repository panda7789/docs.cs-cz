---
title: Autorizace ve WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: d67d64dcf0003de28775ac947f8b5f72d7c2ba2a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597628"
---
# <a name="authorization-in-wcf"></a>Autorizace ve WCF
Autorizace je proces řízení přístupu a práv k prostředkům, jako jsou služby nebo soubory. Témata v této části ukazují, jak provést tuto základní úlohu v Windows Communication Foundation (WCF) mnoha různými způsoby.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mechanismy řízení přístupu](access-control-mechanisms.md)  
 Poskytuje stručný přehled mechanismů autorizace ve službě WCF a navrhovaná použití.  
  
 [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 Zobrazuje proces omezení přístupu ke službě pomocí <xref:System.Security.Permissions.PrincipalPermissionAttribute> .  
  
 [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](how-to-use-the-aspnet-role-provider-with-a-service.md)  
 Provede vás konfigurací služby, aby mohla používat funkci poskytovatele rolí ASP.NET.  
  
 [Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou](how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 ASP.NET může pomocí Správce autorizací spravovat autorizaci webu. WCF může podobně využít kombinaci ASP.NET/Authorization Manageru pro autorizaci klientů.  
  
 [Správa deklarací a autorizace s modelem identity](managing-claims-and-authorization-with-the-identity-model.md)  
 Vysvětluje základy používání infrastruktury modelu identity pro autorizaci založenou na deklaracích.  
  
 [Delegace a zosobnění](delegation-and-impersonation-with-wcf.md)  
 Vysvětluje rozdíl mezi delegováním a zosobněním.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a>Související oddíly  
 [Authentication](authentication-in-wcf.md)  
  
## <a name="see-also"></a>Viz také

- [Přehled zabezpečení](security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
