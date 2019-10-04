---
title: 'Postupy: Použití validátoru vlastního uživatelského jména a hesla'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 98ffad7e717aac949509fa701c77d8ba2b80a695
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834697"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Postupy: Použití validátoru vlastního uživatelského jména a hesla

Ve výchozím nastavení platí, že když se pro ověřování používá uživatelské jméno a heslo, Windows Communication Foundation (WCF) použije Windows k ověření uživatelského jména a hesla. WCF však umožňuje vlastní uživatelské jméno a ověřovací schémata hesla, označované také jako *validátory*. Chcete-li začlenit vlastní validátor uživatelského jména a hesla, vytvořte třídu, která je odvozena z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> a pak ji nakonfigurujte.

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

    Pokud používáte zabezpečení zpráv, přidejte jednu z systémových vazeb, například [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), nebo [> \<customBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , který podporuje zabezpečení zpráv a typ přihlašovacích údajů `UserName`.

    Pokud používáte zabezpečení na úrovni přenosu přes protokol HTTP (S), přidejte [\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) nebo [\<basicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md), @no__t > [5NetTcpBinding @no__t](../../configure-apps/file-schema/wcf/nettcpbinding.md) nebo [>-7CustomBinding](../../configure-apps/file-schema/wcf/custombinding.md) , který používá HTTP (S) a schéma ověřování `Basic`.

    > [!NOTE]
    > Pokud se používá [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] nebo novější, můžete použít vlastní validátor uživatelského jména a hesla se zabezpečením zpráv a přenosů. Pomocí WinFX se vlastní validátor uživatelského jména a hesla dá použít jenom se zabezpečením zpráv.

    > [!TIP]
    > Další informace o použití \<netTcpBinding > v tomto kontextu najdete v [> \<security](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).

    1. V konfiguračním souboru pod prvkem [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) přidejte [> prvek \<bindings](../../configure-apps/file-schema/wcf/bindings.md) .

    2. Do oddílu Bindings přidejte > element [\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) nebo [\<basicHttpBinding](../../configure-apps/file-schema/wcf/basichttpbinding.md) . Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: zadat vazbu služby v konfiguraci](../how-to-specify-a-service-binding-in-configuration.md).

    3. Nastavte atribut `mode` [\<security >](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) nebo [\<security >](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) na `Message`, `Transport` nebo `TransportWithMessageCredential`.

    4. Nastavte atribut `clientCredentialType` [\<message >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) nebo [\<transport >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).

        Pokud používáte zabezpečení zprávy, nastavte atribut `clientCredentialType` [\<message >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) na `UserName`.

        Při použití zabezpečení na úrovni přenosu přes HTTP (S) nastavte atribut `clientCredentialType` [\<transport >](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) nebo [\<transport >](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) na `Basic`.

        > [!NOTE]
        > Když je služba WCF hostovaná ve službě Internetová informační služba (IIS) pomocí zabezpečení na úrovni přenosu a vlastnost <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> je nastavená na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, vlastní schéma ověřování používá podmnožinu ověřování systému Windows. To znamená, že v tomto scénáři provede služba IIS ověřování systému Windows předtím, než WCF vyvolá vlastní ověřovatel.

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

2. Nakonfigurujte chování, které určuje, že se k ověření párů uživatelského jména a hesla pro příchozí tokeny zabezpečení <xref:System.IdentityModel.Tokens.UserNameSecurityToken> používá vlastní validátor uživatelského jména a hesla.

    1. Jako podřízený prvku [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) přidejte [> prvek \<behaviors](../../configure-apps/file-schema/wcf/behaviors.md) .

    2. Přidejte [> \<serviceBehaviors](../../configure-apps/file-schema/wcf/servicebehaviors.md) do prvku [> \<behaviors](../../configure-apps/file-schema/wcf/behaviors.md) .

    3. Přidejte prvek [> \<behavior](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) a nastavte atribut `name` na odpovídající hodnotu.

    4. Přidejte [> \<serviceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md) do prvku [> \<behavior](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) .

    5. Do [> \<serviceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md)přidejte [\<userNameAuthentication >](../../configure-apps/file-schema/wcf/usernameauthentication.md) .

    6. Nastavte `userNamePasswordValidationMode` na `Custom`.

        > [!IMPORTANT]
        > Pokud není nastavená hodnota `userNamePasswordValidationMode`, používá WCF místo vlastního uživatelského jména a validátoru hesla ověřování systému Windows.

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
