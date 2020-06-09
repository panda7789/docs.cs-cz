---
title: 'Postupy: Použití validátoru vlastního uživatelského jména a hesla'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 5ada34ca2d0d757ea333fed60aef179d6578356c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601176"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Postupy: Použití validátoru vlastního uživatelského jména a hesla

Ve výchozím nastavení platí, že když se pro ověřování používá uživatelské jméno a heslo, Windows Communication Foundation (WCF) použije Windows k ověření uživatelského jména a hesla. WCF však umožňuje vlastní uživatelské jméno a ověřovací schémata hesla, označované také jako *validátory*. Chcete-li začlenit vlastní validátor uživatelského jména a hesla, vytvořte třídu, která je odvozena z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> a poté ji nakonfigurujte.

Ukázkovou aplikaci najdete v tématu [validátor hesla uživatelského jména](../samples/user-name-password-validator.md).

### <a name="to-create-a-custom-user-name-and-password-validator"></a>Vytvoření vlastního validátoru uživatelského jména a hesla

1. Vytvořte třídu, která je odvozena z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> .

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. Implementujte vlastní schéma ověřování přepsáním <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.

    Nepoužívejte kód v následujícím příkladu, který Přepisuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodu v produkčním prostředí. Nahraďte kód vlastním uživatelským jménem a schématem ověřování hesla, která by mohla zahrnovat načtení párů uživatelských jmen a hesel z databáze.

    Chcete-li vrátit chyby ověřování zpět do klienta, vyvolejte <xref:System.ServiceModel.FaultException> v <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodě.

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Konfigurace služby tak, aby používala vlastní validátor uživatelského jména a hesla

1. Nakonfigurujte vazbu, která používá zabezpečení zpráv prostřednictvím jakéhokoli přenosu nebo zabezpečení na úrovni přenosu přes HTTP (S).

    Pokud používáte zabezpečení zpráv, přidejte jednu z systémových vazeb, jako je například [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) nebo, [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) která podporuje zabezpečení zprávy a `UserName` typ přihlašovacích údajů.

    Pokud používáte zabezpečení na úrovni přenosu přes protokol HTTP (S), přidejte buď [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) nebo [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) , a, [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) který používá protokol HTTP, a `Basic` schéma ověřování.

    > [!NOTE]
    > Při použití .NET Framework 3,5 nebo novějších verzí můžete používat vlastní validátor uživatelského jména a hesla se zabezpečením zpráv a přenosů. Pomocí WinFX se vlastní validátor uživatelského jména a hesla dá použít jenom se zabezpečením zpráv.

    > [!TIP]
    > Další informace o použití \<netTcpBinding> v tomto kontextu naleznete v tématu [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md) .

    1. V konfiguračním souboru, pod [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) prvkem, přidejte [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.

    2. Přidejte [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) element or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) do oddílu Bindings. Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: zadat vazbu služby v konfiguraci](../how-to-specify-a-service-binding-in-configuration.md).

    3. Nastavte `mode` atribut [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) nebo [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) na `Message` , `Transport` nebo `TransportWithMessageCredential` .

    4. Nastavte `clientCredentialType` atribut [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) nebo [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) .

        Pokud používáte zabezpečení zprávy, nastavte `clientCredentialType` atribut na [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) `UserName` .

        Při použití zabezpečení na úrovni přenosu přes HTTP (S) nastavte `clientCredentialType` atribut [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) nebo [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) na `Basic` .

        > [!NOTE]
        > Když je služba WCF hostovaná ve službě Internetová informační služba (IIS) pomocí zabezpečení na úrovni přenosu a <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> vlastnost je nastavená na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom> , používá vlastní schéma ověřování podmnožinu ověřování systému Windows. To znamená, že v tomto scénáři provede služba IIS ověřování systému Windows předtím, než WCF vyvolá vlastní ověřovatel.

    Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: zadat vazbu služby v konfiguraci](../how-to-specify-a-service-binding-in-configuration.md).

    Následující příklad ukazuje konfigurační kód pro vazbu:

    ```xml
    <system.serviceModel>
      <bindings>
      <wsHttpBinding>
          <binding name="Binding1">
            <security mode="Message">
              <message clientCredentialType="UserName" />
            </security>
          </binding>
        </wsHttpBinding>
      </bindings>
    </system.serviceModel>
    ```

2. Nakonfigurujte chování, které určuje, že se k ověření párů uživatelského jména a hesla pro příchozí tokeny zabezpečení používá vlastní validátor uživatelského jména a hesla <xref:System.IdentityModel.Tokens.UserNameSecurityToken> .

    1. Jako podřízený [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) prvek elementu přidejte [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.

    2. Přidejte [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) k [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elementu.

    3. Přidejte [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element a nastavte `name` atribut na odpovídající hodnotu.

    4. Přidejte [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) k [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu.

    5. Přidejte [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) do [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .

    6. Nastavte na `userNamePasswordValidationMode` `Custom` .

        > [!IMPORTANT]
        > Pokud `userNamePasswordValidationMode` hodnota není nastavená, WCF místo vlastního uživatelského jména a validátoru hesla použije ověřování systému Windows.

    7. Nastavte na `customUserNamePasswordValidatorType` typ, který představuje vaše vlastní uživatelské jméno a Validátor hesel.

    Následující příklad ukazuje `<serviceCredentials>` fragment do tohoto bodu:

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak vytvořit vlastní validátor uživatelského jména a hesla. Nepoužívejte kód, který Přepisuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodu v produkčním prostředí. Nahraďte kód vlastním uživatelským jménem a schématem ověřování hesla, která by mohla zahrnovat načtení párů uživatelských jmen a hesel z databáze.

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [Postupy: Používání poskytovatele členství ASP.NET](how-to-use-the-aspnet-membership-provider.md)
- [Authentication](authentication-in-wcf.md)
