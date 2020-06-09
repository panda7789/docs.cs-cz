---
title: 'Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 7c1076671512b33f115950cad684fba0b514abe9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595333"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou
Pokud ASP.NET hostuje webovou službu, můžete do aplikace integrovat Správce autorizací a poskytnout službě autorizaci. Správce autorizací umožňuje vývojářům aplikací definovat jednotlivé operace, které mohou být seskupeny do úloh formuláře. Správce pak může autorizovat role k provádění konkrétních úkolů nebo jednotlivých operací. Správce autorizací poskytuje nástroj pro správu jako modul snap-in konzoly MMC (Microsoft Management Console) ke správě rolí, úloh, operací a uživatelů. Správci konfigurují úložiště zásad Správce autorizací v souboru XML, ve službě Active Directory nebo v úložišti ADAM (Active Directory Application Mode).  
  
 Správce autorizací je do aplikace integrován konfigurací zprostředkovatele rolí ASP.NET Správce autorizací pro aplikaci ASP.NET, která je hostitelem webové služby. Stejně jako jiní poskytovatelé rolí ASP.NET je zprostředkovatel rolí ASP.NET Správce autorizací nakonfigurovaný pomocí `providers` elementu <>.  
  
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
  
 Další informace o integraci zprostředkovatele rolí ASP.NET s aplikací WCF najdete v tématu [How to: use the ASP.NET provider role with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md). Další informace o používání Správce autorizací s ASP.NET najdete v tématu [How to: use Authorization Manager (AzMan) with ASP.NET 2,0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).  
  
## <a name="see-also"></a>Viz také

- [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](how-to-use-the-aspnet-role-provider-with-a-service.md)
