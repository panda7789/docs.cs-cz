---
title: 'Postupy: Používání poskytovatele členství ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: c2567b6abd42ae725b4786eb111e411f7328154e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939791"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Postupy: Používání poskytovatele členství ASP.NET
Poskytovatel členství ASP.NET je funkce, která vývojářům ASP.NET umožňuje vytvářet weby, které uživatelům umožňují vytvářet jedinečné kombinace uživatelského jména a hesla. U tohoto zařízení může každý uživatel vytvořit účet s webem a přihlásit se pro výhradní přístup k webu a jeho službám. To je na rozdíl od zabezpečení systému Windows, které vyžaduje, aby uživatelé měli účty v doméně systému Windows. Místo toho může web a jeho služby používat libovolný uživatel, který poskytuje své přihlašovací údaje (kombinace uživatelské jméno/heslo).  
  
 Ukázkovou aplikaci najdete v tématu věnovaném [členství a zprostředkovateli rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Informace o použití funkce poskytovatele rolí ASP.NET naleznete v tématu [How to: Použijte poskytovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
 Funkce členství vyžaduje použití databáze SQL Server k uložení informací o uživateli. Tato funkce zahrnuje také metody pro dotazování s otázkou, které si uživatelé zapomněli heslo.  
  
 Vývojáři Windows Communication Foundation (WCF) můžou využít výhod těchto funkcí z hlediska zabezpečení. Při integraci do aplikace WCF musí uživatelé do klientské aplikace WCF dodat kombinaci uživatelského jména a hesla. Pro přenos dat do služby WCF použijte vazbu, která podporuje přihlašovací údaje uživatelského jména a hesla, například <xref:System.ServiceModel.WSHttpBinding> (v konfiguraci `UserName` [ \<, WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) a nastavte typ přihlašovacích údajů klienta na. Ve službě Služba WCF Security ověřuje uživatele na základě uživatelského jména a hesla a také přiřadí roli určenou rolí ASP.NET.  
  
> [!NOTE]
> WCF neposkytuje metody pro naplnění databáze pomocí kombinace uživatelského jména a hesla nebo jiných informací o uživateli.  
  
### <a name="to-configure-the-membership-provider"></a>Konfigurace poskytovatele členství  
  
1. V souboru Web. config v rámci prvku <`system.web`> vytvořte <`membership`> element.  
  
2. V rámci `<providers>` elementu vytvořte element. `<membership>`  
  
3. Jako podřízený prvku <`providers`> `<clear />` přidejte prvek pro vyprázdnění kolekce zprostředkovatelů.  
  
4. `type` `name``add` `connectionStringName` `enablePasswordReset` `applicationName` `requiresQuestionAndAnswer` `enablePasswordRetrieval`V rámci elementuvytvořte<>elementsnásledujícímiatributynastavenýminapříslušnéhodnoty:,,,,,,`<clear />` , `requiresUniqueEmail`a .`passwordFormat` `name` Atribut je použit později jako hodnota v konfiguračním souboru. Následující příklad nastaví na `SqlMembershipProvider`.  
  
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
  
1. V konfiguračním souboru v rámci [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<prvku System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) přidejte vazby > elementu.  
  
2. Přidejte > WSHttpBinding do oddílu Bindings. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: Zadejte vazbu služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
3. Nastavte `mode` atribut `<security>` elementu `Message`.  
  
4. Nastavte atribut prvku <`message`> na `UserName`. `clientCredentialType` Tím se určí, že se jako přihlašovací údaje klienta budou používat dvojice uživatelské jméno a heslo.  
  
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
  
1. Jako podřízený `<system.serviceModel>` prvek elementu [ \<přidejte chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.  
  
2. Přidejte >`behaviors`serviceBehaviors do elementu < >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)  
  
3. Přidejte > `name` chování a nastavte atribut na odpovídající hodnotu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)  
  
4. Přidejte >`behavior`ServiceCredentials do elementu < >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)  
  
5. Přidejte [> UserNameAuthentication k elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) `<serviceCredentials>`  
  
6. Nastavte atribut na `MembershipProvider`. `userNamePasswordValidationMode`  
  
    > [!IMPORTANT]
    >  `userNamePasswordValidationMode` Pokud hodnota není nastavená, WCF místo poskytovatele členství v ASP.NET použije ověřování systému Windows.  
  
7. `membershipProviderName` Nastavte atribut na název zprostředkovatele (zadaný při přidávání poskytovatele v prvním postupu v tomto tématu). Následující příklad ukazuje `<serviceCredentials>` fragment na tento bod.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Postupy: Použití poskytovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Členství a zprostředkovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
