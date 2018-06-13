---
title: 'Postupy: použití zprostředkovatele rolí Správce autorizací ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 39103e86090ed57354efaf9c410a2733a58f06bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490867"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Postupy: použití zprostředkovatele rolí Správce autorizací ASP.NET se službou
Když [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hostuje webovou službu Správce autorizací můžete integrovat do aplikace umožňují ověření ke službě. Správce autorizací umožňuje vývojář aplikací definovat jednotlivé operace, které je možné seskupit do formuláře úlohy. Správce pak může autorizovat rolí k provedení konkrétní úlohy nebo jednotlivé operace. Správce autorizací poskytuje nástroje pro správu jako modul snap-in konzoly Microsoft Management Console (MMC) ke správě rolí, úlohy, operace a uživatelů. Správci nakonfigurovat úložiště zásad autorizace správce v souboru XML, služby Active Directory, nebo v úložišti režimu aplikace Active Directory (ADAM).  
  
 Správce autorizací je integrována do aplikace nakonfigurováním Správce autorizací [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace, který je hostitelem webové služby. Stejně jako jiné [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatelů rolí Správce autorizací [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí je konfigurován pomocí <`providers`> elementu.  
  
 Následující příklad kódu je část konfiguračního souboru pro webovou službu, která Správce autorizací je integraci do aplikace.  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"   
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 Další informace o integraci [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí s WCF aplikací, najdete v části [postupy: použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Další informace o používání Správce autorizací s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], najdete v části [postupy: použití Správce autorizací (AzMan) s prostředím ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
