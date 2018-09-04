---
title: 'Postupy: použití zprostředkovatele Role Správce autorizací ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: c21c1a80468bd81f2df69009afd2be86ee714250
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516705"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Postupy: použití zprostředkovatele Role Správce autorizací ASP.NET se službou
Když [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hostuje webovou službu, můžete začlenit do aplikace a poskytovalo autorizace ve službě Správce autorizací. Správce autorizací umožňuje vývojář aplikace definovat jednotlivé operace, které mohou být seskupeny do formuláře úlohy. Správce pak může autorizovat role provádět konkrétní úlohy nebo jednotlivé operace. Správce autorizací poskytuje nástroje pro správu jako modul snap-in konzoly Microsoft Management Console (MMC) ke správě rolí, úloh, oddělení a uživatelů. Správci konfigurovat úložiště Správce autorizací zásady v souboru XML, Active Directory, nebo v režimu aplikace Active Directory (ADAM) s aplikacemi.  
  
 Správce autorizací je součástí aplikace tím, že nakonfigurujete Správce autorizací [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikaci, která je hostitelem webové služby. Stejně jako jiné [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatelů rolí Správce autorizací [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí je nakonfigurovaný nástrojem <`providers`> element.  
  
 Následující příklad kódu je část konfigurační soubor pro webovou službu, je integrace Správce autorizací do aplikace.  
  
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
  
 Další informace o integraci [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí s WCF aplikací, najdete v článku [postupy: použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Další informace o používání Správce autorizací s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], naleznete v tématu [postupy: použití Správce autorizací (AzMan) s prostředím ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
