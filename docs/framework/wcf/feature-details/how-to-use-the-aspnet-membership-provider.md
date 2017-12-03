---
title: "Postupy: Používání poskytovatele členství ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 950e748ae8ea883ac3e8d5257ef9ab07dffc4acc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Postupy: Používání poskytovatele členství ASP.NET
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Zprostředkovatele členství je funkce, která umožňuje [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] vývojářům vytvářet weby, které umožňuje uživatelům vytvářet jedinečná uživatelská jména a hesla kombinace. S Pokud tuto funkci můžete každý uživatel zřídit účet s lokalitou a přihlášení výhradní přístup k webu a jeho služeb. Tím se liší od zabezpečení systému Windows, která vyžaduje, aby uživatelé mají účty v doméně systému Windows. Každý uživatel, který poskytuje své přihlašovací údaje (kombinace uživatelského jména a hesla), můžete místo toho použijte webu a jeho služeb.  
  
 Ukázkovou aplikaci, najdete v části [členství a poskytovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Informace o používání [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role zprostředkovatele funkce, najdete v části [postupy: použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
 Funkce členství vyžaduje použití databáze systému SQL Server k ukládání informací o uživateli. Tato funkce také obsahuje metody pro dotazování s dotaz uživatelé, kteří zapomenou své heslo.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Vývojáři mohou využít těchto funkcí z bezpečnostních důvodů. Při integraci do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, musí uživatelé zadat uživatelské jméno a heslo kombinaci k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientské aplikace. K přenosu dat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, použijte vazbu, která podporuje pověření jména a hesla uživatele, například <xref:System.ServiceModel.WSHttpBinding> (v konfiguraci [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) a nastavit pověření klienta typ, který má `UserName`. Ve službě [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení ověřuje uživatele na základě uživatelské jméno a heslo a také přiřazuje role určeného [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role.  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]neposkytuje metody k naplnění databáze s kombinací uživatelské jméno a heslo nebo Další informace o uživateli.  
  
### <a name="to-configure-the-membership-provider"></a>Chcete-li konfigurovat členství  
  
1.  V souboru Web.config v části <`system.web`> elementu, vytvoření <`membership`> elementu.  
  
2.  V části `<membership>` elementu, vytvoření `<providers>` elementu.  
  
3.  Jako podřízené <`providers`> elementu, přidejte `<clear />` elementu, který chcete vyprázdnit kolekce zprostředkovatelů.  
  
4.  V části `<clear />` elementu, vytvořit <`add`> element s následujícími atributy nastaven na příslušné hodnoty: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, a `passwordFormat`. `name` Atribut se později používá jako hodnotu v konfiguračním souboru. Následující příklad ji nastaví na `SqlMembershipProvider`.  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Konfigurace zabezpečení služby tak, aby přijímal kombinace uživatelského jména a hesla  
  
1.  V konfiguračním souboru v části [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, přidejte [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.  
  
2.  Přidat [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do části vazby. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]vytvoření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vazby elementu, najdete v části [postupy: zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
3.  Nastavte `mode` atribut `<security>` element `Message`.  
  
4.  Nastavte `clientCredentialType` atribut <`message`> elementu, který chcete `UserName`. Určuje, že pár uživatelské jméno a heslo bude použit jako pověření klienta.  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a>Pro konfiguraci služby pro použití poskytovatele členství  
  
1.  Jako podřízené `<system.serviceModel>` elementu, přidejte [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) – element  
  
2.  Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) na <`behaviors`> element.  
  
3.  Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) a nastavte `name` atribut na odpovídající hodnotu.  
  
4.  Přidat [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) na <`behavior`> element.  
  
5.  Přidat [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) k `<serviceCredentials>` elementu.  
  
6.  Nastavte `userNamePasswordValidationMode` atribut `MembershipProvider`.  
  
    > [!IMPORTANT]
    >  Pokud `userNamePasswordValidationMode` hodnota není nastavena, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá ověřování systému Windows místo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství.  
  
7.  Nastavte `membershipProviderName` atribut název zprostředkovatele (zadaný při přidávání zprostředkovatele v prvním postupu v tomto tématu). Následující příklad ukazuje `<serviceCredentials>` fragment k tomuto bodu.  
  
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
 Následující kód ukazuje konfiguraci pro službu, která používá funkci ASP členství.  
  
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
 [Postupy: použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Členství a poskytovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
