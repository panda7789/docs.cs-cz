---
title: 'Postupy: Použití zprostředkovatele rolí ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 45eeda046e877b4379d7d0e5edd90fac305f5e44
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595294"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Postupy: Použití zprostředkovatele rolí ASP.NET se službou

Poskytovatel rolí ASP.NET (ve spojení se zprostředkovatelem členství ASP.NET) je funkce, která umožňuje vývojářům ASP.NET vytvářet weby, které uživatelům umožňují vytvořit účet s lokalitou a přiřadit k nim role pro účely autorizace. Pomocí této funkce může každý uživatel vytvořit účet s webem a přihlásit se pro výhradní přístup k webu a jeho službám. To je na rozdíl od zabezpečení systému Windows, které vyžaduje, aby uživatelé měli účty v doméně systému Windows. Místo toho může web a jeho služby používat libovolný uživatel, který poskytuje své přihlašovací údaje (kombinace uživatelské jméno/heslo).  
  
Ukázkovou aplikaci najdete v tématu věnovaném [členství a zprostředkovateli rolí](../samples/membership-and-role-provider.md). Další informace o funkci poskytovatele členství v ASP.NET najdete v tématu [How to: use the ASP.NET Membership Provider](how-to-use-the-aspnet-membership-provider.md).  
  
Funkce poskytovatele rolí používá k ukládání informací o uživateli databázi SQL Server. Vývojáři Windows Communication Foundation (WCF) můžou využít výhod těchto funkcí z hlediska zabezpečení. Při integraci do aplikace WCF musí uživatelé do klientské aplikace WCF dodat kombinaci uživatelského jména a hesla. Chcete-li povolit, aby služba WCF používala databázi, je nutné vytvořit instanci <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> třídy, nastavit její <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastnost na a <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> přidat instanci do kolekce chování <xref:System.ServiceModel.ServiceHost> , která je hostitelem služby.  
  
## <a name="configure-the-role-provider"></a>Konfigurace poskytovatele rolí  
  
1. V souboru Web. config v rámci `system.web` prvku < > přidejte `roleManager` prvek < > a nastavte jeho `enabled` atribut na hodnotu `true` .  
  
2. Nastavte `defaultProvider` atribut na `SqlRoleProvider` .  
  
3. Jako podřízený `roleManager` prvku <> přidejte `providers` prvek <>.  
  
4. Jako podřízený `providers` prvku <> přidejte `add` prvek <> s následujícími atributy nastavenými na příslušné hodnoty: `name` , `type` , `connectionStringName` a `applicationName` , jak je znázorněno v následujícím příkladu.  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a>Nakonfigurujte službu tak, aby používala poskytovatele rolí.  
  
1. V souboru Web. config přidejte [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.  
  
2. Přidejte [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) prvek do `system.ServiceModel` prvku <>.  
  
3. Přidejte [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do `behaviors` prvku <>.  
  
4. Přidejte [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element a nastavte `name` atribut na odpovídající hodnotu.  
  
5. Přidejte [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) do `behavior` prvku <>.  
  
6. Nastavte `principalPermissionMode` atribut na `UseAspNetRoles` .  
  
7. Nastavte `roleProviderName` atribut na `SqlRoleProvider` . Následující příklad ukazuje fragment konfigurace.  
  
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

- [Členství a poskytovatel rolí](../samples/membership-and-role-provider.md)
- [Postupy: Používání poskytovatele členství ASP.NET](how-to-use-the-aspnet-membership-provider.md)
