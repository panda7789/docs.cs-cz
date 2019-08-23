---
title: 'Postupy: Použití validátoru vlastního uživatelského jména a hesla'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 57bd650caef831f3ee886c0422e13cc4149d3416
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968812"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Postupy: Použití validátoru vlastního uživatelského jména a hesla
Ve výchozím nastavení platí, že když se pro ověřování používá uživatelské jméno a heslo, Windows Communication Foundation (WCF) použije Windows k ověření uživatelského jména a hesla. WCF však umožňuje vlastní uživatelské jméno a ověřovací schémata hesla, označované také jako *validátory*. Chcete-li začlenit vlastní validátor uživatelského jména a hesla, vytvořte třídu, která <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> je odvozena z a poté ji nakonfigurujte.  
  
 Ukázkovou aplikaci najdete v tématu [validátor hesla uživatelského jména](../../../../docs/framework/wcf/samples/user-name-password-validator.md).  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a>Vytvoření vlastního validátoru uživatelského jména a hesla  
  
1. Vytvořte třídu, která je odvozena <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>z.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2. Implementujte vlastní schéma ověřování přepsáním <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.  
  
     Nepoužívejte kód v následujícím příkladu, který Přepisuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodu v produkčním prostředí. Nahraďte kód vlastním uživatelským jménem a schématem ověřování hesla, která by mohla zahrnovat načtení párů uživatelských jmen a hesel z databáze.  
  
     Chcete-li vrátit chyby ověřování zpět do klienta, vyvolejte <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> v metodě.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Konfigurace služby tak, aby používala vlastní validátor uživatelského jména a hesla  
  
1. Nakonfigurujte vazbu, která používá zabezpečení zpráv prostřednictvím jakéhokoli přenosu nebo zabezpečení na úrovni přenosu přes HTTP (S).  
  
     Pokud používáte zabezpečení zpráv, přidejte jednu z systémových vazeb, jako je [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), nebo `UserName` [ \<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , která podporuje zabezpečení zpráv a typ přihlašovacích údajů.  
  
     Pokud používáte zabezpečení na úrovni přenosu přes HTTP (S), přidejte buď [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) nebo [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) [ \<BasicHttpBinding >, NetTcpBinding > nebo CustomBinding > ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)který používá protokol HTTP (S) a `Basic` schéma ověřování.  
  
    > [!NOTE]
    > Když [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] použijete nebo později, můžete použít vlastní validátor uživatelského jména a hesla se zabezpečením zpráv a přenosů. Pomocí WinFX se vlastní validátor uživatelského jména a hesla dá použít jenom se zabezpečením zpráv.  
  
    > [!TIP]
    >  Další informace o použití \<> NetTcpBinding v tomto kontextu najdete v tématu [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
  
    1. V konfiguračním souboru v rámci [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<prvku System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) přidejte vazby > elementu.  
  
    2. Do části Bindings přidejte prvek [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) [> WSHttpBindingneboBasicHttpBinding.\<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: Zadejte vazbu služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
    3. `mode` Nastavte atribut `Message` [ >zabezpečenínebo\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) [> zabezpečenína,nebo.\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `Transport` `TransportWithMessageCredential`  
  
    4. `clientCredentialType` Nastavte atribut [ >zprávynebo>přenosu.\<](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)  
  
         Pokud používáte zabezpečení zprávy, nastavte `clientCredentialType` atribut [ \<> zprávy](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) na. `UserName`  
  
         Při použití zabezpečení na úrovni přenosu přes HTTP ( `clientCredentialType` S) nastavte atribut [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) `Basic`Transport > nebo [ \<> přenosu](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) .  
  
        > [!NOTE]
        >  Když je služba WCF hostovaná ve službě Internetová informační služba (IIS) pomocí zabezpečení na úrovni přenosu a <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> vlastnost je nastavená <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>na, používá vlastní schéma ověřování podmnožinu ověřování systému Windows. To znamená, že v tomto scénáři provede služba IIS ověřování systému Windows předtím, než WCF vyvolá vlastní ověřovatel.  
  
     Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: Zadejte vazbu služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
     Následující příklad ukazuje konfigurační kód pro vazbu.  
  
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
  
    1. Jako podřízený [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) [ prvkuSystem.ServiceModel>přidejteprvek>chování.\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
    2. Do prvku [> \<chování](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) přidejte [> serviceBehaviors.\<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)  
  
    3. Přidejte >`name` prvek [chování a nastavte atribut na odpovídající hodnotu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
    4. Přidejte [> ServiceCredentials k chování > elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
    5. Přidejte [> UserNameAuthentication do > ServiceCredentials. \<](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)  
  
    6. `userNamePasswordValidationMode` Nastavte`Custom`na.  
  
        > [!IMPORTANT]
        >  `userNamePasswordValidationMode` Pokud hodnota není nastavená, WCF místo vlastního uživatelského jména a validátoru hesla použije ověřování systému Windows.  
  
    7. `customUserNamePasswordValidatorType` Nastavte na typ, který představuje vaše vlastní uživatelské jméno a Validátor hesel.  
  
     Následující příklad ukazuje `<serviceCredentials>` fragment na tento bod.  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit vlastní validátor uživatelského jména a hesla. Nepoužívejte kód, který Přepisuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodu v produkčním prostředí. Nahraďte kód vlastním uživatelským jménem a schématem ověřování hesla, která by mohla zahrnovat načtení párů uživatelských jmen a hesel z databáze.  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [Postupy: Použití poskytovatele členství ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
- [Ověřování](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
