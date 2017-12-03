---
title: "Postupy: Použití zprostředkovatele rolí ASP.NET se službou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb5adec17f834687038b729a475fbcc0e2311c01
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Postupy: Použití zprostředkovatele rolí ASP.NET se službou
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Zprostředkovatele rolí (ve spojení s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství) je funkce, která umožňuje [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] vývojářům vytvářet weby, které uživatelům umožní vytvořit účet s lokalitou a přiřadit role pro autorizaci pro účely. Pomocí této funkce můžete každý uživatel určit účet s lokalitou a přihlášení pro výhradní přístup k webu a jeho služeb. Tím se liší od zabezpečení systému Windows, která vyžaduje, aby uživatelé mají účty v doméně systému Windows. Každý uživatel, který poskytuje své přihlašovací údaje (kombinace uživatelského jména a hesla), můžete místo toho použijte webu a jeho služeb.  
  
 Ukázkovou aplikaci, najdete v části [členství a poskytovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcí zprostředkovatele členství, najdete v části [postupy: použití poskytovatele členství prostředí ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
 Zprostředkovatele funkce role používá databázi systému SQL Server uložit informace o uživateli. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Vývojáři mohou využít těchto funkcí z bezpečnostních důvodů. Při integraci do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, musí uživatelé zadat uživatelské jméno a heslo kombinaci k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientské aplikace. Chcete-li povolit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] k použití databáze, musíte vytvořit instanci <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> třídy, nastavte jeho <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastnost <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>a přidat do kolekce chování na instanci <xref:System.ServiceModel.ServiceHost> , který je hostitelem služby.  
  
### <a name="to-configure-the-role-provider"></a>Chcete-li konfigurovat role  
  
1.  V souboru Web.config v části <`system.web`> elementu, přidejte <`roleManager`> elementu a sadu jeho `enabled` atribut `true`.  
  
2.  Nastavte `defaultProvider` atribut `SqlRoleProvider`.  
  
3.  Jako podřízené <`roleManager`> elementu, přidejte <`providers`> elementu.  
  
4.  Jako podřízené <`providers`> elementu, přidejte <`add`> element s následujícími atributy nastaven na příslušné hodnoty: `name`, `type`, `connectionStringName`, a `applicationName`, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <!-- Configure the Sql Role Provider. -->  
    <roleManager enabled ="true"   
     defaultProvider ="SqlRoleProvider" >  
       <providers>  
         <add name ="SqlRoleProvider"   
           type="System.Web.Security.SqlRoleProvider"   
           connectionStringName="SqlConn"   
           applicationName="MembershipAndRoleProviderSample"/>  
       </providers>  
    </roleManager>  
    ```  
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a>Ke konfiguraci služby pro použití poskytovatele role  
  
1.  V souboru Web.config, přidejte [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.  
  
2.  Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu, který chcete <`system.ServiceModel`> elementu.  
  
3.  Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) na <`behaviors`> element.  
  
4.  Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu a sadu `name` atribut na odpovídající hodnotu.  
  
5.  Přidat [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) na <`behavior`> element.  
  
6.  Nastavte `principalPermissionMode` atribut `UseAspNetRoles`.  
  
7.  Nastavte `roleProviderName` atribut `SqlRoleProvider`. Následující příklad ukazuje fragment konfigurace.  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Členství a poskytovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)  
 [Postupy: použití poskytovatele členství prostředí ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
