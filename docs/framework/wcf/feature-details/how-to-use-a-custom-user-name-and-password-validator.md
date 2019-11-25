---
title: 'Postupy: Použití validátoru vlastního uživatelského jména a hesla'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 3d01a29671f42e80fdb7ca45223007aa60273ba9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283260"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Postupy: Použití validátoru vlastního uživatelského jména a hesla

Ve výchozím nastavení platí, že když se pro ověřování používá uživatelské jméno a heslo, Windows Communication Foundation (WCF) použije Windows k ověření uživatelského jména a hesla. WCF však umožňuje vlastní uživatelské jméno a ověřovací schémata hesla, označované také jako *validátory*. Chcete-li začlenit vlastní validátor uživatelského jména a hesla, vytvořte třídu, která je odvozena z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> a poté ji nakonfigurujte.

Ukázkovou aplikaci najdete v tématu [validátor hesla uživatelského jména](../samples/user-name-password-validator.md).

### <a name="to-create-a-custom-user-name-and-password-validator"></a>Vytvoření vlastního validátoru uživatelského jména a hesla

1. Vytvořte třídu, která je odvozena z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. Implementujte vlastní schéma ověřování přepsáním metody <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.

    Nepoužívejte kód v následujícím příkladu, který přepisuje metodu <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> v produkčním prostředí. Nahraďte kód vlastním uživatelským jménem a schématem ověřování hesla, která by mohla zahrnovat načtení párů uživatelských jmen a hesel z databáze.

    Chcete-li vrátit chyby ověřování zpět klientovi, vyvolejte <xref:System.ServiceModel.FaultException> v metodě <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Konfigurace služby tak, aby používala vlastní validátor uživatelského jména a hesla

1. Nakonfigurujte vazbu, která používá zabezpečení zpráv prostřednictvím jakéhokoli přenosu nebo zabezpečení na úrovni přenosu přes HTTP (S).

    Pokud používáte zabezpečení zpráv, přidejte jednu z systémových vazeb, například [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)nebo [>\<CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , která podporuje zabezpečení zpráv a typ přihlašovacích údajů `UserName`.

    Pokud používáte zabezpečení na úrovni přenosu přes protokol HTTP, přidejte buď [\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) nebo [\<basicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md), [\<netTcpBinding >](../../configure-apps/file-schema/wcf/nettcpbinding.md) nebo [\<CustomBinding >](../../configure-apps/file-schema/wcf/custombinding.md) , který používá protokol HTTP a `Basic` schéma ověřování.

    > [!NOTE]
    > Při použití .NET Framework 3,5 nebo novějších verzí můžete používat vlastní validátor uživatelského jména a hesla se zabezpečením zpráv a přenosů. Pomocí WinFX se vlastní validátor uživatelského jména a hesla dá použít jenom se zabezpečením zpráv.

    > [!TIP]
    > Další informace o použití \<netTcpBinding > v tomto kontextu najdete v tématu [\<zabezpečení >](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).

    1. V konfiguračním souboru pod prvkem [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) přidejte [\<vazby >](../../configure-apps/file-schema/wcf/bindings.md) element.

    2. Do oddílu Bindings přidejte [\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) nebo [\<prvek >u BasicHttpBinding](../../configure-apps/file-schema/wcf/basichttpbinding.md) . Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: zadat vazbu služby v konfiguraci](../how-to-specify-a-service-binding-in-configuration.md).

    3. Nastavte atribut `mode` [\<> zabezpečení](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) nebo [\<zabezpečení >](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) na `Message`, `Transport`nebo `TransportWithMessageCredential`.

    4. Nastavte atribut `clientCredentialType` [\<zprávy >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) nebo [\<přenosu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).

        Pokud používáte zabezpečení zprávy, nastavte atribut `clientCredentialType` [\<zprávy >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) na `UserName`.

        Při použití zabezpečení na úrovni přenosu přes HTTP (S) nastavte atribut `clientCredentialType` [\<přenosů >](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) nebo [\<přenosových >](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) na `Basic`.

        > [!NOTE]
        > Když je služba WCF hostovaná ve službě Internetová informační služba (IIS) pomocí zabezpečení na úrovni přenosu a vlastnost <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> je nastavená na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, používá vlastní schéma ověřování podmnožinu ověřování systému Windows. To znamená, že v tomto scénáři provede služba IIS ověřování systému Windows předtím, než WCF vyvolá vlastní ověřovatel.

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

2. Nakonfigurujte chování, které určuje, že se k ověření párů uživatelského jména a hesla pro příchozí <xref:System.IdentityModel.Tokens.UserNameSecurityToken> tokeny zabezpečení používá vlastní validátor uživatelského jména a hesla.

    1. Jako podřízený prvku [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) přidejte [\<chování >](../../configure-apps/file-schema/wcf/behaviors.md) elementu.

    2. Přidejte [\<serviceBehaviors >](../../configure-apps/file-schema/wcf/servicebehaviors.md) do [chování\<>](../../configure-apps/file-schema/wcf/behaviors.md) elementu.

    3. Přidejte [> prvek chování\<](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) a nastavte atribut `name` na odpovídající hodnotu.

    4. Přidejte [\<serviceCredentials >](../../configure-apps/file-schema/wcf/servicecredentials.md) do [\<chování >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu.

    5. Do [>\<ServiceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md)přidejte [\<UserNameAuthentication >](../../configure-apps/file-schema/wcf/usernameauthentication.md) .

    6. Nastavte `userNamePasswordValidationMode` na `Custom`.

        > [!IMPORTANT]
        > Pokud hodnota `userNamePasswordValidationMode` není nastavená, WCF místo vlastního uživatelského jména a validátoru hesla použije ověřování systému Windows.

    7. Nastavte `customUserNamePasswordValidatorType` na typ, který představuje vaše vlastní validátor uživatelského jména a hesla.

    Následující příklad ukazuje fragment `<serviceCredentials>` do tohoto bodu:

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak vytvořit vlastní validátor uživatelského jména a hesla. Nepoužívejte kód, který přepisuje metodu <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> v produkčním prostředí. Nahraďte kód vlastním uživatelským jménem a schématem ověřování hesla, která by mohla zahrnovat načtení párů uživatelských jmen a hesel z databáze.

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [Postupy: Používání poskytovatele členství ASP.NET](how-to-use-the-aspnet-membership-provider.md)
- [Ověřování](authentication-in-wcf.md)
