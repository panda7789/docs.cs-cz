---
title: 'Postupy: Používání poskytovatele členství ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 5b15d56c7150a8478bc32651538903778e3b877d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184798"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="7e33c-102">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7e33c-102">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="7e33c-103">Poskytovatel členství ASP.NET je funkce, která umožňuje vývojářům ASP.NET vytvářet weby, které uživatelům umožňují vytvářet jedinečné kombinace uživatelských jmen a hesel.</span><span class="sxs-lookup"><span data-stu-id="7e33c-103">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="7e33c-104">S tímto zařízením může každý uživatel vytvořit účet s webem a přihlásit se pro exkluzivní přístup k webu a jeho službám.</span><span class="sxs-lookup"><span data-stu-id="7e33c-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="7e33c-105">To je na rozdíl od zabezpečení systému Windows, který vyžaduje, aby uživatelé měli účty v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7e33c-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="7e33c-106">Místo toho může každý uživatel, který poskytuje svá pověření (kombinace uživatelského jména a hesla), používat web a jeho služby.</span><span class="sxs-lookup"><span data-stu-id="7e33c-106">Instead, any user that supplies their credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="7e33c-107">Ukázková aplikace naleznete v [tématu Členství a zprostředkovatel role](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="7e33c-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="7e33c-108">Informace o použití funkce zprostředkovatele role ASP.NET naleznete v [tématu Postup: Použití ASP.NET zprostředkovatele rolí se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="7e33c-108">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="7e33c-109">Funkce členství vyžaduje k uložení informací o uživateli použití databáze serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7e33c-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="7e33c-110">Tato funkce také obsahuje metody pro dotazování s dotazem, všichni uživatelé, kteří zapomněli své heslo.</span><span class="sxs-lookup"><span data-stu-id="7e33c-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="7e33c-111">Vývojáři Windows Communication Foundation (WCF) mohou tyto funkce využívat z bezpečnostních důvodů.</span><span class="sxs-lookup"><span data-stu-id="7e33c-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="7e33c-112">Při integraci do aplikace WCF, uživatelé musí zadat kombinaci uživatelského jména a hesla do klientské aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="7e33c-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="7e33c-113">Chcete-li přenést data do služby WCF, použijte vazbu, která <xref:System.ServiceModel.WSHttpBinding> podporuje pověření uživatelského jména a hesla, jako je `UserName`například (v konfiguraci [ \<wsHttpBinding>) ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)a nastavte typ pověření klienta na .</span><span class="sxs-lookup"><span data-stu-id="7e33c-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="7e33c-114">Ve službě zabezpečení WCF ověřuje uživatele na základě uživatelského jména a hesla a také přiřadí roli určenou ASP.NET role.</span><span class="sxs-lookup"><span data-stu-id="7e33c-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="7e33c-115">WCF neposkytuje metody k naplnění databáze s kombinacemi uživatelského jména a hesla nebo jiné informace o uživateli.</span><span class="sxs-lookup"><span data-stu-id="7e33c-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="7e33c-116">Konfigurace poskytovatele členství</span><span class="sxs-lookup"><span data-stu-id="7e33c-116">To configure the membership provider</span></span>

1. <span data-ttu-id="7e33c-117">V souboru Web.config pod `system.web` elementem <`membership`> vytvořte prvek <>.</span><span class="sxs-lookup"><span data-stu-id="7e33c-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="7e33c-118">Pod `<membership>` elementem vytvořte `<providers>` prvek.</span><span class="sxs-lookup"><span data-stu-id="7e33c-118">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="7e33c-119">Jako podřízený prvek `providers` <> `<clear />` přidejte prvek pro vyprázdnění kolekce zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="7e33c-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="7e33c-120">Pod `<clear />` elementem vytvořte `add` prvek <> s následujícími `name`atributy nastavenými na příslušné hodnoty: `type`, `connectionStringName`, `applicationName` `enablePasswordRetrieval`, , `enablePasswordReset` `requiresQuestionAndAnswer`, `requiresUniqueEmail`, a `passwordFormat`.</span><span class="sxs-lookup"><span data-stu-id="7e33c-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="7e33c-121">Atribut `name` se později použije jako hodnota v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="7e33c-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="7e33c-122">Následující příklad jej `SqlMembershipProvider`nastaví na .</span><span class="sxs-lookup"><span data-stu-id="7e33c-122">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="7e33c-123">Následující příklad ukazuje konfigurační část.</span><span class="sxs-lookup"><span data-stu-id="7e33c-123">The following example shows the configuration section.</span></span>

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="7e33c-124">Konfigurace zabezpečení služby tak, aby přijímala kombinaci uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="7e33c-124">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="7e33c-125">V konfiguračním souboru pod elementem [ \<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) přidejte [ \<element>vazby.](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7e33c-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="7e33c-126">Přidejte [ \<>wsHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do oddílu vazby.</span><span class="sxs-lookup"><span data-stu-id="7e33c-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="7e33c-127">Další informace o vytvoření elementu vazby WCF naleznete v [tématu How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="7e33c-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="7e33c-128">Nastavte `mode` atribut prvku `<security>` na `Message`.</span><span class="sxs-lookup"><span data-stu-id="7e33c-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="7e33c-129">Nastavte `clientCredentialType` atribut prvku `message` <> `UserName`na .</span><span class="sxs-lookup"><span data-stu-id="7e33c-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="7e33c-130">To určuje, že dvojice uživatelského jména a hesla bude použita jako pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="7e33c-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="7e33c-131">Následující příklad ukazuje konfigurační kód pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="7e33c-131">The following example shows the configuration code for the binding.</span></span>

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="7e33c-132">Konfigurace služby pro použití poskytovatele členství</span><span class="sxs-lookup"><span data-stu-id="7e33c-132">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="7e33c-133">Jako podřízený `<system.serviceModel>` prvek přidejte [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) prvku chování.</span><span class="sxs-lookup"><span data-stu-id="7e33c-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="7e33c-134">Přidejte [ \<>serviceBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) `behaviors` do prvku <>.</span><span class="sxs-lookup"><span data-stu-id="7e33c-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="7e33c-135">Přidejte [ \<>chování](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) `name` a nastavte atribut na příslušnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7e33c-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="7e33c-136">Přidejte [ \<>serviceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) `behavior` do prvku <>.</span><span class="sxs-lookup"><span data-stu-id="7e33c-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="7e33c-137">Přidejte do `<serviceCredentials>` prvku>[ \<userNameAuthentication.](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)</span><span class="sxs-lookup"><span data-stu-id="7e33c-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="7e33c-138">Nastavte `userNamePasswordValidationMode` atribut `MembershipProvider`na .</span><span class="sxs-lookup"><span data-stu-id="7e33c-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7e33c-139">Pokud `userNamePasswordValidationMode` hodnota není nastavena, WCF používá ověřování systému Windows namísto poskytovatele členství ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7e33c-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="7e33c-140">Nastavte `membershipProviderName` atribut na název zprostředkovatele (zadaný při přidání zprostředkovatele v prvním postupu v tomto tématu).</span><span class="sxs-lookup"><span data-stu-id="7e33c-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="7e33c-141">Následující příklad ukazuje `<serviceCredentials>` fragment do tohoto bodu.</span><span class="sxs-lookup"><span data-stu-id="7e33c-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

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

## <a name="example"></a><span data-ttu-id="7e33c-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e33c-142">Example</span></span>

<span data-ttu-id="7e33c-143">Následující kód ukazuje konfiguraci služby, která používá funkci členství asp.</span><span class="sxs-lookup"><span data-stu-id="7e33c-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7e33c-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e33c-144">See also</span></span>

- [<span data-ttu-id="7e33c-145">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="7e33c-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="7e33c-146">Členství a zprostředkovatel rolí</span><span class="sxs-lookup"><span data-stu-id="7e33c-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
