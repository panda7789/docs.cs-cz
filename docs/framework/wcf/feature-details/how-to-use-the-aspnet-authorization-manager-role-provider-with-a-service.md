---
title: "Postupy: použití zprostředkovatele rolí Správce autorizací ASP.NET se službou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ee51a2fa4a4ec3de04e21fdbc070cd7619b43c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]integrace [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, najdete v části [postup: použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pomocí Správce autorizací s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], najdete v části [postupy: použití Správce autorizací (AzMan) s prostředím ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
