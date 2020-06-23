---
title: 'Postupy: Používání poskytovatele členství ASP.NET'
description: Přečtěte si, jak poskytovatel členství ASP.NET podporuje webové stránky, které uživatelům umožňují vytvořit uživatelské jméno a heslo pro přístup bez použití doménového účtu systému Windows.
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 6d527993dcf1fc5d5cd39bf22c3e772baf60e62f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246724"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Postupy: Používání poskytovatele členství ASP.NET

Poskytovatel členství ASP.NET je funkce, která vývojářům ASP.NET umožňuje vytvářet weby, které uživatelům umožňují vytvářet jedinečné kombinace uživatelského jména a hesla. U tohoto zařízení může každý uživatel vytvořit účet s webem a přihlásit se pro výhradní přístup k webu a jeho službám. To je na rozdíl od zabezpečení systému Windows, které vyžaduje, aby uživatelé měli účty v doméně systému Windows. Místo toho může web a jeho služby používat libovolný uživatel, který poskytuje své přihlašovací údaje (kombinace uživatelské jméno/heslo).

Ukázkovou aplikaci najdete v tématu věnovaném [členství a zprostředkovateli rolí](../samples/membership-and-role-provider.md). Informace o použití funkce poskytovatele rolí ASP.NET naleznete v tématu [How to: use the ASP.NET role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).

Funkce členství vyžaduje použití databáze SQL Server k uložení informací o uživateli. Tato funkce zahrnuje také metody pro dotazování s otázkou, které si uživatelé zapomněli heslo.

Vývojáři Windows Communication Foundation (WCF) můžou využít výhod těchto funkcí z hlediska zabezpečení. Při integraci do aplikace WCF musí uživatelé do klientské aplikace WCF dodat kombinaci uživatelského jména a hesla. Chcete-li přenést data do služby WCF, použijte vazbu, která podporuje přihlašovací údaje uživatelského jména a hesla, například <xref:System.ServiceModel.WSHttpBinding> (v konfiguraci [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ), a nastavte typ pověření klienta na `UserName` . Ve službě Služba WCF Security ověřuje uživatele na základě uživatelského jména a hesla a také přiřadí roli určenou rolí ASP.NET.

> [!NOTE]
> WCF neposkytuje metody pro naplnění databáze pomocí kombinace uživatelského jména a hesla nebo jiných informací o uživateli.

### <a name="to-configure-the-membership-provider"></a>Konfigurace poskytovatele členství

1. V souboru Web.config v rámci `system.web` elementu <> vytvořte `membership` prvek <>.

2. V rámci `<membership>` elementu vytvořte `<providers>` element.

3. Jako podřízený `providers` prvku <> přidejte `<clear />` prvek pro vyprázdnění kolekce zprostředkovatelů.

4. V rámci `<clear />` elementu vytvořte <`add`> prvek s následujícími atributy nastavenými na příslušné hodnoty: `name` , `type` , `connectionStringName` , `applicationName` , `enablePasswordRetrieval` , `enablePasswordReset` ,, a `requiresQuestionAndAnswer` `requiresUniqueEmail` `passwordFormat` . `name`Atribut je použit později jako hodnota v konfiguračním souboru. Následující příklad nastaví na `SqlMembershipProvider` .

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Konfigurace zabezpečení služby pro přijetí kombinace uživatelského jména a hesla

1. V konfiguračním souboru, pod [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) prvkem, přidejte [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.

2. Přidejte [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) do části Bindings (vazby). Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: zadat vazbu služby v konfiguraci](../how-to-specify-a-service-binding-in-configuration.md).

3. Nastavte `mode` atribut `<security>` elementu na `Message` .

4. Nastavte `clientCredentialType` atribut `message` prvku <> na `UserName` . Tím se určí, že se jako přihlašovací údaje klienta budou používat dvojice uživatelské jméno a heslo.

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

1. Jako podřízený `<system.serviceModel>` prvek elementu přidejte [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element

2. Přidejte [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do `behaviors` prvku <>.

3. Přidejte [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) a nastavte `name` atribut na odpovídající hodnotu.

4. Přidejte [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) do `behavior` prvku <>.

5. Přidejte [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) k `<serviceCredentials>` elementu.

6. Nastavte `userNamePasswordValidationMode` atribut na `MembershipProvider` .

    > [!IMPORTANT]
    > Pokud `userNamePasswordValidationMode` hodnota není nastavená, WCF místo poskytovatele členství v ASP.NET použije ověřování systému Windows.

7. Nastavte `membershipProviderName` atribut na název zprostředkovatele (zadaný při přidávání poskytovatele v prvním postupu v tomto tématu). Následující příklad ukazuje `<serviceCredentials>` fragment na tento bod.

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

Následující kód ukazuje konfiguraci služby, která používá funkci členství ASP.

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

- [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Členství a poskytovatel rolí](../samples/membership-and-role-provider.md)
