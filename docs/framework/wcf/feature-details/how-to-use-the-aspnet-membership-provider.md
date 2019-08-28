---
title: 'Postupy: Používání poskytovatele členství ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: b86287440b2265349b853265f12a2f6e48b4cff3
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045274"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="f3448-102">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f3448-102">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="f3448-103">Poskytovatel členství ASP.NET je funkce, která vývojářům ASP.NET umožňuje vytvářet weby, které uživatelům umožňují vytvářet jedinečné kombinace uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="f3448-103">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="f3448-104">U tohoto zařízení může každý uživatel vytvořit účet s webem a přihlásit se pro výhradní přístup k webu a jeho službám.</span><span class="sxs-lookup"><span data-stu-id="f3448-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="f3448-105">To je na rozdíl od zabezpečení systému Windows, které vyžaduje, aby uživatelé měli účty v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f3448-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="f3448-106">Místo toho může web a jeho služby používat libovolný uživatel, který poskytuje své přihlašovací údaje (kombinace uživatelské jméno/heslo).</span><span class="sxs-lookup"><span data-stu-id="f3448-106">Instead, any user that supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="f3448-107">Ukázkovou aplikaci najdete v tématu věnovaném [členství a zprostředkovateli rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="f3448-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="f3448-108">Informace o použití funkce poskytovatele rolí ASP.NET naleznete v tématu [How to: Použijte poskytovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="f3448-108">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="f3448-109">Funkce členství vyžaduje použití databáze SQL Server k uložení informací o uživateli.</span><span class="sxs-lookup"><span data-stu-id="f3448-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="f3448-110">Tato funkce zahrnuje také metody pro dotazování s otázkou, které si uživatelé zapomněli heslo.</span><span class="sxs-lookup"><span data-stu-id="f3448-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="f3448-111">Vývojáři Windows Communication Foundation (WCF) můžou využít výhod těchto funkcí z hlediska zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f3448-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="f3448-112">Při integraci do aplikace WCF musí uživatelé do klientské aplikace WCF dodat kombinaci uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="f3448-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="f3448-113">Pro přenos dat do služby WCF použijte vazbu, která podporuje přihlašovací údaje uživatelského jména a hesla, například <xref:System.ServiceModel.WSHttpBinding> (v konfiguraci `UserName` [ \<, WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) a nastavte typ přihlašovacích údajů klienta na.</span><span class="sxs-lookup"><span data-stu-id="f3448-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="f3448-114">Ve službě Služba WCF Security ověřuje uživatele na základě uživatelského jména a hesla a také přiřadí roli určenou rolí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f3448-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="f3448-115">WCF neposkytuje metody pro naplnění databáze pomocí kombinace uživatelského jména a hesla nebo jiných informací o uživateli.</span><span class="sxs-lookup"><span data-stu-id="f3448-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="f3448-116">Konfigurace poskytovatele členství</span><span class="sxs-lookup"><span data-stu-id="f3448-116">To configure the membership provider</span></span>

1. <span data-ttu-id="f3448-117">V souboru Web. config v rámci prvku <`system.web`> vytvořte <`membership`> element.</span><span class="sxs-lookup"><span data-stu-id="f3448-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="f3448-118">V rámci `<providers>` elementu vytvořte element. `<membership>`</span><span class="sxs-lookup"><span data-stu-id="f3448-118">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="f3448-119">Jako podřízený prvku <`providers`> `<clear />` přidejte prvek pro vyprázdnění kolekce zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="f3448-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="f3448-120">`type` `name``add` `connectionStringName` `enablePasswordReset` `applicationName` `requiresQuestionAndAnswer` `enablePasswordRetrieval`V rámci elementuvytvořte<>elementsnásledujícímiatributynastavenýminapříslušnéhodnoty:,,,,,,`<clear />` , `requiresUniqueEmail`a .`passwordFormat`</span><span class="sxs-lookup"><span data-stu-id="f3448-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="f3448-121">`name` Atribut je použit později jako hodnota v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="f3448-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="f3448-122">Následující příklad nastaví na `SqlMembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="f3448-122">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="f3448-123">Následující příklad ukazuje konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="f3448-123">The following example shows the configuration section.</span></span>

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="f3448-124">Konfigurace zabezpečení služby pro přijetí kombinace uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="f3448-124">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="f3448-125">V konfiguračním souboru v rámci [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<prvku System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) přidejte vazby > elementu.</span><span class="sxs-lookup"><span data-stu-id="f3448-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="f3448-126">Přidejte > WSHttpBinding do oddílu Bindings. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="f3448-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="f3448-127">Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: Zadejte vazbu služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="f3448-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="f3448-128">Nastavte `mode` atribut `<security>` elementu `Message`.</span><span class="sxs-lookup"><span data-stu-id="f3448-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="f3448-129">Nastavte atribut prvku <`message`> na `UserName`. `clientCredentialType`</span><span class="sxs-lookup"><span data-stu-id="f3448-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="f3448-130">Tím se určí, že se jako přihlašovací údaje klienta budou používat dvojice uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="f3448-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="f3448-131">Následující příklad ukazuje konfigurační kód pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="f3448-131">The following example shows the configuration code for the binding.</span></span>

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="f3448-132">Konfigurace služby pro použití poskytovatele členství</span><span class="sxs-lookup"><span data-stu-id="f3448-132">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="f3448-133">Jako podřízený `<system.serviceModel>` prvek elementu [ \<přidejte chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f3448-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="f3448-134">Přidejte >`behaviors`serviceBehaviors do elementu < >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f3448-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="f3448-135">Přidejte > `name` chování a nastavte atribut na odpovídající hodnotu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f3448-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="f3448-136">Přidejte >`behavior`ServiceCredentials do elementu < >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="f3448-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="f3448-137">Přidejte [> UserNameAuthentication k elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) `<serviceCredentials>`</span><span class="sxs-lookup"><span data-stu-id="f3448-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="f3448-138">Nastavte atribut na `MembershipProvider`. `userNamePasswordValidationMode`</span><span class="sxs-lookup"><span data-stu-id="f3448-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="f3448-139">`userNamePasswordValidationMode` Pokud hodnota není nastavená, WCF místo poskytovatele členství v ASP.NET použije ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f3448-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="f3448-140">`membershipProviderName` Nastavte atribut na název zprostředkovatele (zadaný při přidávání poskytovatele v prvním postupu v tomto tématu).</span><span class="sxs-lookup"><span data-stu-id="f3448-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="f3448-141">Následující příklad ukazuje `<serviceCredentials>` fragment na tento bod.</span><span class="sxs-lookup"><span data-stu-id="f3448-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

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

## <a name="example"></a><span data-ttu-id="f3448-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3448-142">Example</span></span>

<span data-ttu-id="f3448-143">Následující kód ukazuje konfiguraci služby, která používá funkci členství ASP.</span><span class="sxs-lookup"><span data-stu-id="f3448-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f3448-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3448-144">See also</span></span>

- [<span data-ttu-id="f3448-145">Postupy: Použití poskytovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="f3448-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="f3448-146">Členství a zprostředkovatel rolí</span><span class="sxs-lookup"><span data-stu-id="f3448-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
