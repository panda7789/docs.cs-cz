---
title: 'Postupy: Použití zprostředkovatele rolí ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: ddfedeb2491998f64ab241ceba303d50d0714351
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184773"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Postupy: Použití zprostředkovatele rolí ASP.NET se službou

Poskytovatel rolí ASP.NET (ve spojení s poskytovatelem členství ASP.NET) je funkce, která umožňuje vývojářům ASP.NET vytvářet weby, které uživatelům umožňují vytvořit účet s webem a přiřadit role pro účely autorizace. Pomocí této funkce může každý uživatel vytvořit účet s webem a přihlásit se pro výhradní přístup k webu a jeho službám. To je na rozdíl od zabezpečení systému Windows, který vyžaduje, aby uživatelé měli účty v doméně systému Windows. Místo toho může web a jeho služby používat každý uživatel, který zadá svá pověření (kombinace uživatelského jména a hesla).  
  
Ukázková aplikace naleznete v [tématu Členství a zprostředkovatel role](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Další informace o funkci ASP.NET poskytovatele členství naleznete v [tématu How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
Funkce zprostředkovatele rolí používá k ukládání informací o uživateli databázi serveru SQL Server. Vývojáři Windows Communication Foundation (WCF) mohou tyto funkce využívat z bezpečnostních důvodů. Při integraci do aplikace WCF musí uživatelé zadat kombinaci uživatelského jména a hesla do klientské aplikace WCF. Chcete-li povolit WCF používat databázi, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> musíte vytvořit <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> instanci třídy, nastavit její vlastnost <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>a <xref:System.ServiceModel.ServiceHost> přidat instanci do kolekce chování, která je hostitelem služby.  
  
## <a name="configure-the-role-provider"></a>Konfigurace zprostředkovatele rolí  
  
1. V souboru Web.config pod `system.web` elementem <`roleManager`> přidejte `enabled` element `true`<> a nastavte jeho atribut na .  
  
2. Nastavte `defaultProvider` atribut `SqlRoleProvider`na .  
  
3. Jako podřízený prvek `roleManager` <> přidejte prvek> <. `providers`  
  
4. Jako podřízený prvek `providers` <> přidejte `add` prvek <> s následujícími `name` `type`atributy nastavenými na příslušné hodnoty: , , `connectionStringName`a `applicationName`, jak je znázorněno v následujícím příkladu.  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a>Konfigurace služby tak, aby používala zprostředkovatele rolí  
  
1. Do souboru Web.config přidejte prvek [ \<system.serviceModel>.](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
2. Přidejte [ \<prvek chování>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) `system.ServiceModel` prvku <>.  
  
3. Přidejte [ \<>serviceBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) `behaviors` do prvku <>.  
  
4. Přidejte [ \<prvek>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) chování `name` a nastavte atribut na příslušnou hodnotu.  
  
5. Přidejte [ \<>serviceAuthorization](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) `behavior` do prvku <>.  
  
6. Nastavte `principalPermissionMode` atribut `UseAspNetRoles`na .  
  
7. Nastavte `roleProviderName` atribut `SqlRoleProvider`na . Následující příklad ukazuje fragment konfigurace.  
  
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

- [Členství a zprostředkovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [Postupy: Používání poskytovatele členství ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
