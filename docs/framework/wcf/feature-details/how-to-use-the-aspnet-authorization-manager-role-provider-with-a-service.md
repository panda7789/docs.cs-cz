---
title: 'Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 009b96defdf27591ddb98afaa684745b5fcbe0d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184802"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou
Když ASP.NET hostitelem webové služby, můžete do aplikace integrovat Správce autorizací a poskytnout tak autorizaci služby. Správce autorizací umožňuje vývojáři aplikace definovat jednotlivé operace, které lze seskupit a vytvořit úkoly. Správce pak může povolit role k provádění konkrétních úkolů nebo jednotlivých operací. Nástroj Authorization Manager poskytuje nástroj pro správu jako modul snap-in konzoly MMC (MMC) pro správu rolí, úkolů, operací a uživatelů. Správci konfigurují úložiště zásad Správce autorizací v souboru XML, službě Active Directory nebo v úložišti služby AD (Active Directory).  
  
 Správce autorizací je integrován do aplikace konfigurací nástroje Správce autorizací ASP.NET zprostředkovatele rolí pro ASP.NET aplikaci, která je hostitelem webové služby. Stejně jako ostatní poskytovatelé rolí ASP.NET je zprostředkovatel `providers` role Správce autorizací ASP.NET konfigurován pomocí prvku <>.  
  
 Následující příklad kódu je část konfiguračního souboru pro webovou službu, která integruje Správce autorizací do aplikace.  
  
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
  
 Další informace o integraci zprostředkovatele rolí ASP.NET s aplikací WCF naleznete [v tématu How to: Use the ASP.NET role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Další informace o používání Správce autorizací s ASP.NET naleznete v [tématu How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).  
  
## <a name="see-also"></a>Viz také

- [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
