---
title: 'Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 778af929b4cfc96ce0683d304be5f8fb87a0e47b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880204"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou
Při technologie ASP.NET je hostitelem webové služby, můžete začlenit do aplikace a poskytovalo autorizace ve službě Správce autorizací. Správce autorizací umožňuje vývojář aplikace definovat jednotlivé operace, které mohou být seskupeny do formuláře úlohy. Správce pak může autorizovat role provádět konkrétní úlohy nebo jednotlivé operace. Správce autorizací poskytuje nástroje pro správu jako modul snap-in konzoly Microsoft Management Console (MMC) ke správě rolí, úloh, oddělení a uživatelů. Správci konfigurovat úložiště Správce autorizací zásady v souboru XML, Active Directory, nebo v režimu aplikace Active Directory (ADAM) s aplikacemi.  
  
 Správce autorizací je integrovaná do aplikace podle konfigurace zprostředkovatele role Správce autorizací ASP.NET pro aplikaci ASP.NET, který je hostitelem webové služby. Stejně jako ostatní zprostředkovatelů rolí prostředí ASP.NET, je nakonfigurován pomocí zprostředkovatele role Správce autorizací ASP.NET <`providers`> element.  
  
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
  
 Další informace o integraci poskytovatele rolí prostředí ASP.NET se službou WCF aplikace najdete v tématu [jak: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Další informace o používání Správce autorizací pomocí technologie ASP.NET, naleznete v tématu [jak: Použití Správce autorizací (AzMan) s technologií ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
