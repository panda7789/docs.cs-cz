---
title: 'Postupy: Použití validátoru vlastního uživatelského jména a hesla'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: a7573e14d224e2ec861b301816d6d886fd147180
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085011"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Postupy: Použití validátoru vlastního uživatelského jména a hesla
Ve výchozím nastavení Pokud uživatelské jméno a heslo se používá k ověřování, Windows Communication Foundation (WCF) používá Windows k ověření uživatelského jména a hesla. Ale WCF umožňuje vlastního uživatelského jména a hesla metody ověřování, označované také jako *validátory*. Začlenit vlastní uživatelské jméno a heslo validátoru, vytvořte třídu, která je odvozena z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> a potom ho nakonfigurovat.  
  
 Ukázková aplikace, najdete v části [validátor hesel pro uživatelská jména](../../../../docs/framework/wcf/samples/user-name-password-validator.md).  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a>Chcete-li vytvořit validátor vlastního uživatelského jména a hesla  
  
1.  Vytvořte třídu, která je odvozena z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  Implementovat vlastní ověřování schéma tak, že přepíšete <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.  
  
     Nepoužívejte kód v následujícím příkladu, který přepíše <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metoda v produkčním prostředí. Nahraďte kód vašeho vlastního uživatelského jména a hesla schéma ověřování, což může znamenat načtení dvojice název a heslo uživatele z databáze.  
  
     Pokud chcete vrátit chyby s ověřováním zpátky do klienta, throw <xref:System.ServiceModel.FaultException> v <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Nakonfigurujte službu používat validátor vlastního uživatelského jména a hesla  
  
1.  Konfigurace vazby, který používá zabezpečení zprávy přes všechny přenosu nebo zabezpečení na úrovni přenosu přes HTTP (S).  
  
     Při použití zabezpečení zpráv, přidejte jeden z vazeb poskytovaných systémem, například [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), nebo [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) zabezpečení podporuje zpráv a `UserName` typ přihlašovacích údajů.  
  
     Při použití zabezpečení na úrovni přenosu přes HTTP (S), přidat buď [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) nebo [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) nebo [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , který používá protokol HTTP (S) a `Basic` schéma ověřování.  
  
    > [!NOTE]
    >  Když [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] nebo novějším, je použít, můžete použít vlastní validátor uživatelské jméno a heslo s zabezpečení zpráv a přenosu. S [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], vlastního validátoru uživatelského jména a hesla jde použít jenom s zabezpečení zpráv.  
  
    > [!TIP]
    >  Další informace o používání \<netTcpBinding > v tomto kontextu, najdete v článku [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
  
    1.  V konfiguračním souboru v části [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, přidejte [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.  
  
    2.  Přidat [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) nebo [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) prvek do části vazeb. Další informace o vytváření element vazby WCF najdete v tématu [postupy: zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
    3.  Nastavte `mode` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) nebo [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) k `Message`, `Transport`, nebo `TransportWithMessageCredential`.  
  
    4.  Nastavte `clientCredentialType` atribut [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) nebo [ \<přenosu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).  
  
         Při použití zabezpečení zprávy, nastavte `clientCredentialType` atribut [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) k `UserName`.  
  
         Při použití zabezpečení na úrovni přenosu přes HTTP (S), nastavte `clientCredentialType` atribut [ \<přenosu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) nebo [ \<přenosu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) k `Basic`.  
  
        > [!NOTE]
        >  Když je služba WCF hostované v Internetové informační služby (IIS) pomocí zabezpečení na úrovni přenosu a <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> je nastavena na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, schéma vlastní ověřování používá podmnožinu ověřování Windows. Důvodem je skutečnost, že v tomto scénáři služba IIS provede ověřování Windows před WCF volání vlastní ověřovací data.  
  
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
  
2.  Konfigurace chování, které určuje, zda validátor vlastní uživatelské jméno a heslo slouží k ověření dvojice název a heslo uživatele pro příchozí <xref:System.IdentityModel.Tokens.UserNameSecurityToken> tokeny zabezpečení.  
  
    1.  Jako podřízené [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, přidejte [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.  
  
    2.  Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.  
  
    3.  Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu a nastavte `name` atribut na odpovídající hodnotu.  
  
    4.  Přidat [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) k [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu.  
  
    5.  Přidat [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) k [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
    6.  Nastavte `userNamePasswordValidationMode` k `Custom`.  
  
        > [!IMPORTANT]
        >  Pokud `userNamePasswordValidationMode` hodnota není nastavená, WCF používá ověřování Windows namísto validátoru vlastního uživatelského jména a hesla.  
  
    7.  Nastavte `customUserNamePasswordValidatorType` na typ, který představuje validátor vaše vlastní uživatelské jméno a heslo.  
  
     Následující příklad ukazuje `<serviceCredentials>` fragmentu do tohoto bodu.  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit vlastní uživatelská jména a hesla validátor. Nepoužívejte kód, který přepíše <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metoda v produkčním prostředí. Nahraďte kód vašeho vlastního uživatelského jména a hesla schéma ověřování, což může znamenat načtení dvojice název a heslo uživatele z databáze.  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [Postupy: Používání poskytovatele členství ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [Ověřování](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
