---
title: 'Postupy: Používání poskytovatele členství ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 5b15d56c7150a8478bc32651538903778e3b877d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184798"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Postupy: Používání poskytovatele členství ASP.NET

Poskytovatel členství ASP.NET je funkce, která umožňuje vývojářům ASP.NET vytvářet weby, které uživatelům umožňují vytvářet jedinečné kombinace uživatelských jmen a hesel. S tímto zařízením může každý uživatel vytvořit účet s webem a přihlásit se pro exkluzivní přístup k webu a jeho službám. To je na rozdíl od zabezpečení systému Windows, který vyžaduje, aby uživatelé měli účty v doméně systému Windows. Místo toho může každý uživatel, který poskytuje svá pověření (kombinace uživatelského jména a hesla), používat web a jeho služby.

Ukázková aplikace naleznete v [tématu Členství a zprostředkovatel role](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Informace o použití funkce zprostředkovatele role ASP.NET naleznete v [tématu Postup: Použití ASP.NET zprostředkovatele rolí se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).

Funkce členství vyžaduje k uložení informací o uživateli použití databáze serveru SQL Server. Tato funkce také obsahuje metody pro dotazování s dotazem, všichni uživatelé, kteří zapomněli své heslo.

Vývojáři Windows Communication Foundation (WCF) mohou tyto funkce využívat z bezpečnostních důvodů. Při integraci do aplikace WCF, uživatelé musí zadat kombinaci uživatelského jména a hesla do klientské aplikace WCF. Chcete-li přenést data do služby WCF, použijte vazbu, která <xref:System.ServiceModel.WSHttpBinding> podporuje pověření uživatelského jména a hesla, jako je `UserName`například (v konfiguraci [ \<wsHttpBinding>) ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)a nastavte typ pověření klienta na . Ve službě zabezpečení WCF ověřuje uživatele na základě uživatelského jména a hesla a také přiřadí roli určenou ASP.NET role.

> [!NOTE]
> WCF neposkytuje metody k naplnění databáze s kombinacemi uživatelského jména a hesla nebo jiné informace o uživateli.

### <a name="to-configure-the-membership-provider"></a>Konfigurace poskytovatele členství

1. V souboru Web.config pod `system.web` elementem <`membership`> vytvořte prvek <>.

2. Pod `<membership>` elementem vytvořte `<providers>` prvek.

3. Jako podřízený prvek `providers` <> `<clear />` přidejte prvek pro vyprázdnění kolekce zprostředkovatelů.

4. Pod `<clear />` elementem vytvořte `add` prvek <> s následujícími `name`atributy nastavenými na příslušné hodnoty: `type`, `connectionStringName`, `applicationName` `enablePasswordRetrieval`, , `enablePasswordReset` `requiresQuestionAndAnswer`, `requiresUniqueEmail`, a `passwordFormat`. Atribut `name` se později použije jako hodnota v konfiguračním souboru. Následující příklad jej `SqlMembershipProvider`nastaví na .

    Následující příklad ukazuje konfigurační část.

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Konfigurace zabezpečení služby tak, aby přijímala kombinaci uživatelského jména a hesla

1. V konfiguračním souboru pod elementem [ \<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) přidejte [ \<element>vazby.](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

2. Přidejte [ \<>wsHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do oddílu vazby. Další informace o vytvoření elementu vazby WCF naleznete v [tématu How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

3. Nastavte `mode` atribut prvku `<security>` na `Message`.

4. Nastavte `clientCredentialType` atribut prvku `message` <> `UserName`na . To určuje, že dvojice uživatelského jména a hesla bude použita jako pověření klienta.

    Následující příklad ukazuje konfigurační kód pro vazbu.

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a>Konfigurace služby pro použití poskytovatele členství

1. Jako podřízený `<system.serviceModel>` prvek přidejte [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) prvku chování.

2. Přidejte [ \<>serviceBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) `behaviors` do prvku <>.

3. Přidejte [ \<>chování](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) `name` a nastavte atribut na příslušnou hodnotu.

4. Přidejte [ \<>serviceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) `behavior` do prvku <>.

5. Přidejte do `<serviceCredentials>` prvku>[ \<userNameAuthentication.](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)

6. Nastavte `userNamePasswordValidationMode` atribut `MembershipProvider`na .

    > [!IMPORTANT]
    > Pokud `userNamePasswordValidationMode` hodnota není nastavena, WCF používá ověřování systému Windows namísto poskytovatele členství ASP.NET.

7. Nastavte `membershipProviderName` atribut na název zprostředkovatele (zadaný při přidání zprostředkovatele v prvním postupu v tomto tématu). Následující příklad ukazuje `<serviceCredentials>` fragment do tohoto bodu.

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

Následující kód ukazuje konfiguraci služby, která používá funkci členství asp.

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

## <a name="see-also"></a>Viz také

- [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Členství a zprostředkovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
