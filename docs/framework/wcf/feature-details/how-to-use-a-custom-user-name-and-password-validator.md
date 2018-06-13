---
title: 'Postupy: Použití validátoru vlastního uživatelského jména a hesla'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 8580219181af8fd28bcc99c60bd1e681ffbdad54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496809"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Postupy: Použití validátoru vlastního uživatelského jména a hesla
Ve výchozím nastavení Pokud uživatelské jméno a heslo slouží k ověřování, Windows Communication Foundation (WCF) používá Windows k ověření uživatelského jména a hesla. Ale WCF umožňuje vlastní uživatelské jméno a heslo schémat ověřování, také známé jako *validátory*. Zahrnout validátor vlastní uživatelské jméno a heslo, vytvořte třídu, která je odvozena z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> a potom jej nakonfigurovat.  
  
 Ukázkovou aplikaci, najdete v části [validátor hesel pro uživatele název](../../../../docs/framework/wcf/samples/user-name-password-validator.md).  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a>Chcete-li vytvořit validátor vlastní uživatelské jméno a heslo  
  
1.  Vytvořte třídu, která je odvozena z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  Implementace vlastního ověřování schématu přepsáním <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metoda.  
  
     Nepoužívejte kód v následujícím příkladu, který přepíše <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metoda v produkčním prostředí. Nahraďte kód vaše vlastní uživatelské jméno a heslo schéma ověřování, které mohou zahrnovat načítání dvojice název a heslo uživatele z databáze.  
  
     Pokud chcete vrátit zpátky chybám při ověřování klienta, throw <xref:System.ServiceModel.FaultException> v <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metoda.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Nakonfigurujte službu používat validátor vlastní uživatelské jméno a heslo  
  
1.  Nakonfigurujte vazbu, která používá zabezpečení zpráv přes všechny přenos nebo zabezpečení na úrovni přenosu přes protokol HTTP (S).  
  
     Při použití zabezpečení zpráv, přidejte jedno z vazby poskytované systémem, jako například [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), nebo [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) zabezpečení podporuje zpráv a `UserName` typ přihlašovacích údajů.  
  
     Při použití zabezpečení na úrovni přenosu přes protokol HTTP (S), přidejte buď [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) nebo [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) nebo [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , který používá protokol HTTP (S) a `Basic` schéma ověřování.  
  
    > [!NOTE]
    >  Když [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] nebo novějším, je použít, můžete použít vlastní validátor uživatelské jméno a heslo s zabezpečení zprávy a přenos. S [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], vlastní validátor uživatelské jméno a heslo lze použít pouze s zabezpečení zpráv.  
  
    > [!TIP]
    >  Další informace o používání \<netTcpBinding > v tomto kontextu, najdete v části [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
  
    1.  V konfiguračním souboru v části [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, přidejte [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.  
  
    2.  Přidat [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) nebo [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element do části vazby. Další informace o vytváření element vazby WCF najdete v tématu [postupy: zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
    3.  Nastavte `mode` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) nebo [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) k `Message`, `Transport`, `or``TransportWithMessageCredential`.  
  
    4.  Nastavte `clientCredentialType` atribut [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) nebo [ \<přenosu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).  
  
         Při použití zabezpečení zpráv, `clientCredentialType` atribut [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) k `UserName`.  
  
         Při použití zabezpečení na úrovni přenosu přes protokol HTTP (S), `clientCredentialType` atribut [ \<přenosu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) nebo [ \<přenosu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) k `Basic`.  
  
        > [!NOTE]
        >  Když je služba WCF hostované v Internetové informační služby (IIS) pomocí zabezpečení na úrovni přenosu a <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> je nastavena na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, schéma vlastní ověřování používá podmnožinu ověřování systému Windows. Je to způsobeno v tomto scénáři služba IIS provede ověřování systému Windows před vyvolání vlastní ověřovací WCF.  
  
     Další informace o vytváření element vazby WCF najdete v tématu [postupy: zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
     Následující příklad ukazuje kód konfigurace pro vazbu.  
  
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
  
2.  Konfigurace chování, která určuje, zda validátor vlastní uživatelské jméno a heslo slouží k ověření uživatele dvojice název a heslo pro příchozí <xref:System.IdentityModel.Tokens.UserNameSecurityToken> tokeny zabezpečení.  
  
    1.  Jako podřízené [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, přidejte [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.  
  
    2.  Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.  
  
    3.  Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu a sadu `name` atribut na odpovídající hodnotu.  
  
    4.  Přidat [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) k [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.  
  
    5.  Přidat [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) k [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
    6.  Nastavte `userNamePasswordValidationMode` k `Custom`.  
  
        > [!IMPORTANT]
        >  Pokud `userNamePasswordValidationMode` hodnota není nastavená, WCF používá ověřování systému Windows místo validátoru vlastního uživatelského jména a hesla.  
  
    7.  Nastavte `customUserNamePasswordValidatorType` typu, který představuje validátor vaše vlastní uživatelské jméno a heslo.  
  
     Následující příklad ukazuje `<serviceCredentials>` fragment k tomuto bodu.  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit vlastní uživatelská jména a hesla validátoru. Nepoužívejte kód, který přepíše <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metoda v produkčním prostředí. Nahraďte kód vaše vlastní uživatelské jméno a heslo schéma ověřování, které mohou zahrnovat načítání dvojice název a heslo uživatele z databáze.  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [Postupy: Používání poskytovatele členství ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [Ověřování](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
