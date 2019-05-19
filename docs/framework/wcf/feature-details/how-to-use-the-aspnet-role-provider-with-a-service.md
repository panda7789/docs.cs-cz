---
title: 'Postupy: Použití zprostředkovatele rolí ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: f989252c7dd9b2ccdce8331e7cdd987042230ded
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880232"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Postupy: Použití zprostředkovatele rolí ASP.NET se službou
Poskytovatele rolí prostředí ASP.NET (ve spojení s poskytovatele členství prostředí ASP.NET) je funkce, která umožňuje vývojářům vytvářet weby, které umožňují uživatelům k vytvoření účtu s lokalitou a má být přiřazena role pro autorizaci ASP.NET. Pomocí této funkce může každý uživatel zřídit účet s lokalitou a přihlaste pro výhradní přístup k webu a jeho služeb. To se liší od zabezpečení Windows, což vyžaduje, aby uživatelé mají účty v doméně Windows. Každý uživatel, který dodává své přihlašovací údaje (kombinaci uživatelského jména/hesla) můžete místo toho použijte webu a jeho služeb.  
  
 Ukázková aplikace, najdete v části [členství a poskytovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Další informace o funkci zprostředkovatele členství technologie ASP.NET, naleznete v tématu [jak: Používání poskytovatele členství ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
 Funkce poskytovatele role používá databázi serveru SQL Server k ukládání informací o uživateli. Windows Communication Foundation (WCF) vývojáři mohou využít těchto funkcí z bezpečnostních důvodů. Při integraci do aplikace WCF, uživatelé musí zadat uživatelské jméno/heslo kombinace do klientské aplikace WCF. Pokud chcete povolit WCF k použití databáze, musíte vytvořit instanci <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> třídy, nastavte jeho <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastnost <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>a přidat do kolekce vlastností pro instanci <xref:System.ServiceModel.ServiceHost> , který je hostitelem služby.  
  
### <a name="to-configure-the-role-provider"></a>Konfigurace zprostředkovatele rolí  
  
1. V souboru Web.config v části <`system.web`> element, přidat <`roleManager`> element a nastavte jeho `enabled` atribut `true`.  
  
2. Nastavte `defaultProvider` atribut `SqlRoleProvider`.  
  
3. Jako podřízené <`roleManager`> element, přidejte <`providers`> element.  
  
4. Jako podřízené <`providers`> element, přidejte <`add`> element s následujícími atributy nastaven na odpovídající hodnoty: `name`, `type`, `connectionStringName`, a `applicationName`, jak je znázorněno v následujícím příkladu.  
  
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
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a>Postup konfigurace služby použití zprostředkovatele rolí  
  
1. V souboru Web.config, přidejte [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.  
  
2. Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu <`system.ServiceModel`> element.  
  
3. Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k <`behaviors`> element.  
  
4. Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu a nastavte `name` atribut na odpovídající hodnotu.  
  
5. Přidat [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) k <`behavior`> element.  
  
6. Nastavte `principalPermissionMode` atribut `UseAspNetRoles`.  
  
7. Nastavte `roleProviderName` atribut `SqlRoleProvider`. Následující příklad ukazuje část konfigurace.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Členství a zprostředkovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [Postupy: Používání poskytovatele členství ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
