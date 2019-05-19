---
title: 'Postupy: Používání poskytovatele členství ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 61324bbc5ea07dd19e23589bfc90f9ea44a6b331
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880189"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Postupy: Používání poskytovatele členství ASP.NET
Zprostředkovatel členství technologie ASP.NET je funkce, která umožňuje vývojářům vytvářet weby, které umožňují uživatelům vytvářet jedinečné uživatelské jméno a heslo kombinace technologie ASP.NET. S Azure může každý uživatel zřídit účet s lokalitou a přihlášení na exkluzivní přístup k webu a jeho služeb. To se liší od zabezpečení Windows, což vyžaduje, aby uživatelé mají účty v doméně Windows. Každý uživatel, který dodává své přihlašovací údaje (kombinaci uživatelského jména/hesla) můžete místo toho použijte webu a jeho služeb.  
  
 Ukázková aplikace, najdete v části [členství a poskytovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Informace o používání funkcí zprostředkovatele rolí ASP.NET najdete v tématu [jak: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
 Funkce členství vyžaduje použití databáze SQL serveru k ukládání informací o uživateli. Tato funkce zároveň metody pro výzvu s dotaz všechny uživatele, kteří zapomenou své heslo.  
  
 Windows Communication Foundation (WCF) vývojáři mohou využít těchto funkcí z bezpečnostních důvodů. Při integraci do aplikace WCF, uživatelé musí zadat uživatelské jméno/heslo kombinace do klientské aplikace WCF. Chcete-li přenést data do služby WCF, použijte vazbu, která podporuje uživatelské jméno/heslo přihlašovacích údajů, jako například <xref:System.ServiceModel.WSHttpBinding> (v konfiguraci [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) a nastavit typ přihlašovacích údajů k klienta`UserName`. Zabezpečení WCF na službu, ověřuje uživatele na základě uživatelského jména a hesla a také přiřadí roli určenou rolí technologie ASP.NET.  
  
> [!NOTE]
>  WCF neposkytuje metody k naplnění databáze pomocí kombinace uživatelské jméno/heslo nebo jiné informace o uživateli.  
  
### <a name="to-configure-the-membership-provider"></a>Konfigurace zprostředkovatele členství  
  
1. V souboru Web.config v části <`system.web`> element, vytvořit <`membership`> element.  
  
2. V části `<membership>` elementu, vytvořit `<providers>` elementu.  
  
3. Jako podřízené <`providers`> element, přidejte `<clear />` element vyprázdnit kolekce zprostředkovatelů.  
  
4. V části `<clear />` elementu, vytvoření <`add`> element s následujícími atributy nastaven na odpovídající hodnoty: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, a `passwordFormat`. `name` Atributu se použije v pozdější jako hodnotu v konfiguračním souboru. Následující příklad nastaví na `SqlMembershipProvider`.  
  
     Následující příklad ukazuje konfigurační oddíl.  
  
    ```xml  
    <!-- Configure the Sql Membership Provider -->  
    <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
      <providers>  
        <clear />  
          <add   
            name="SqlMembershipProvider"   
            type="System.Web.Security.SqlMembershipProvider"   
            connectionStringName="SqlConn"  
            applicationName="MembershipAndRoleProviderSample"  
            enablePasswordRetrieval="false"  
            enablePasswordReset="false"  
            requiresQuestionAndAnswer="false"  
            requiresUniqueEmail="true"  
            passwordFormat="Hashed" />  
      </providers>  
    </membership>  
    ```  
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Ke konfiguraci služby zabezpečení tak, aby přijímal kombinace uživatelského jména/hesla  
  
1. V konfiguračním souboru v části [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, přidejte [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.  
  
2. Přidat [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do části vazeb. Další informace o vytváření element vazby WCF najdete v tématu [jak: Zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
3. Nastavte `mode` atribut `<security>` elementu `Message`.  
  
4. Nastavte `clientCredentialType` atribut <`message`> element `UserName`. Určuje, že páru jméno/heslo uživatele se použije jako pověření klienta.  
  
     Následující příklad ukazuje kód konfigurace pro vazbu.  
  
    ```xml  
    <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
      <!-- Set up a binding that uses UserName as the client credential type -->  
        <binding name="MembershipBinding">  
          <security mode ="Message">  
            <message clientCredentialType ="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    </system.serviceModel>  
    ```  
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a>Ke konfiguraci služby pro používání poskytovatele členství  
  
1. Jako podřízené `<system.serviceModel>` elementu, přidejte [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) – element  
  
2. Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k <`behaviors`> element.  
  
3. Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) a nastavit `name` atribut na odpovídající hodnotu.  
  
4. Přidat [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) k <`behavior`> element.  
  
5. Přidat [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) k `<serviceCredentials>` elementu.  
  
6. Nastavte `userNamePasswordValidationMode` atribut `MembershipProvider`.  
  
    > [!IMPORTANT]
    >  Pokud `userNamePasswordValidationMode` hodnota není nastavená, WCF používá ověřování Windows namísto poskytovatele členství prostředí ASP.NET.  
  
7. Nastavte `membershipProviderName` atribut název zprostředkovatele (zadanými při přidávání zprostředkovatele v prvním postupu v tomto tématu). Následující příklad ukazuje `<serviceCredentials>` fragmentu do tohoto bodu.  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
          <behavior name="MyServiceBehavior">  
             <serviceCredentials>  
                <userNameAuthentication   
                userNamePasswordValidationMode="MembershipProvider"  
                membershipProviderName="SqlMembershipProvider" />  
             </serviceCredentials>  
          </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a>Příklad  
 Následující kód znázorňuje konfiguraci pro službu, která používá funkci ASP členství.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="MyServiceBehavior" name="Microsoft.Samples.GettingStarted.CalculatorService">  
        <endpoint address="http://microsoft.com/WCFservices/Calculator"  
          binding="wsHttpBinding" bindingConfiguration="MembershipBinding"  
          name="ASPmemberUserName" contract="Microsoft.Samples.GettingStarted.ICalculator" />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication   
              userNamePasswordValidationMode="MembershipProvider"  
              membershipProviderName="SqlMembershipProvider" />  
          </serviceCredentials>  
        </behavior>  
          </serviceBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MembershipBinding">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Členství a zprostředkovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
