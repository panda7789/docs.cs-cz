---
title: 'Postupy: Používání poskytovatele členství ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 840e4a5d365f2adbaf335c1061a580665a39824d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595320"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="9cf9f-102">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9cf9f-102">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="9cf9f-103">Poskytovatel členství ASP.NET je funkce, která vývojářům ASP.NET umožňuje vytvářet weby, které uživatelům umožňují vytvářet jedinečné kombinace uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-103">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="9cf9f-104">U tohoto zařízení může každý uživatel vytvořit účet s webem a přihlásit se pro výhradní přístup k webu a jeho službám.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="9cf9f-105">To je na rozdíl od zabezpečení systému Windows, které vyžaduje, aby uživatelé měli účty v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="9cf9f-106">Místo toho může web a jeho služby používat libovolný uživatel, který poskytuje své přihlašovací údaje (kombinace uživatelské jméno/heslo).</span><span class="sxs-lookup"><span data-stu-id="9cf9f-106">Instead, any user that supplies their credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="9cf9f-107">Ukázkovou aplikaci najdete v tématu věnovaném [členství a zprostředkovateli rolí](../samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="9cf9f-107">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="9cf9f-108">Informace o použití funkce poskytovatele rolí ASP.NET naleznete v tématu [How to: use the ASP.NET role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="9cf9f-108">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="9cf9f-109">Funkce členství vyžaduje použití databáze SQL Server k uložení informací o uživateli.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="9cf9f-110">Tato funkce zahrnuje také metody pro dotazování s otázkou, které si uživatelé zapomněli heslo.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="9cf9f-111">Vývojáři Windows Communication Foundation (WCF) můžou využít výhod těchto funkcí z hlediska zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="9cf9f-112">Při integraci do aplikace WCF musí uživatelé do klientské aplikace WCF dodat kombinaci uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="9cf9f-113">Chcete-li přenést data do služby WCF, použijte vazbu, která podporuje přihlašovací údaje uživatelského jména a hesla, například <xref:System.ServiceModel.WSHttpBinding> (v konfiguraci [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ), a nastavte typ pověření klienta na `UserName` .</span><span class="sxs-lookup"><span data-stu-id="9cf9f-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="9cf9f-114">Ve službě Služba WCF Security ověřuje uživatele na základě uživatelského jména a hesla a také přiřadí roli určenou rolí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="9cf9f-115">WCF neposkytuje metody pro naplnění databáze pomocí kombinace uživatelského jména a hesla nebo jiných informací o uživateli.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="9cf9f-116">Konfigurace poskytovatele členství</span><span class="sxs-lookup"><span data-stu-id="9cf9f-116">To configure the membership provider</span></span>

1. <span data-ttu-id="9cf9f-117">V souboru Web. config v rámci `system.web` prvku < > vytvořte < `membership` > element.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="9cf9f-118">V rámci `<membership>` elementu vytvořte `<providers>` element.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-118">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="9cf9f-119">Jako podřízený `providers` prvku <> přidejte `<clear />` prvek pro vyprázdnění kolekce zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="9cf9f-120">V rámci `<clear />` elementu vytvořte <`add`> prvek s následujícími atributy nastavenými na příslušné hodnoty: `name` , `type` , `connectionStringName` , `applicationName` , `enablePasswordRetrieval` , `enablePasswordReset` ,, a `requiresQuestionAndAnswer` `requiresUniqueEmail` `passwordFormat` .</span><span class="sxs-lookup"><span data-stu-id="9cf9f-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="9cf9f-121">`name`Atribut je použit později jako hodnota v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="9cf9f-122">Následující příklad nastaví na `SqlMembershipProvider` .</span><span class="sxs-lookup"><span data-stu-id="9cf9f-122">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="9cf9f-123">Následující příklad ukazuje konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-123">The following example shows the configuration section.</span></span>

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="9cf9f-124">Konfigurace zabezpečení služby pro přijetí kombinace uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="9cf9f-124">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="9cf9f-125">V konfiguračním souboru, pod [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) prvkem, přidejte [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-125">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="9cf9f-126">Přidejte [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) do části Bindings (vazby).</span><span class="sxs-lookup"><span data-stu-id="9cf9f-126">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="9cf9f-127">Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: zadat vazbu služby v konfiguraci](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="9cf9f-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="9cf9f-128">Nastavte `mode` atribut `<security>` elementu na `Message` .</span><span class="sxs-lookup"><span data-stu-id="9cf9f-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="9cf9f-129">Nastavte `clientCredentialType` atribut `message` prvku <> na `UserName` .</span><span class="sxs-lookup"><span data-stu-id="9cf9f-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="9cf9f-130">Tím se určí, že se jako přihlašovací údaje klienta budou používat dvojice uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="9cf9f-131">Následující příklad ukazuje konfigurační kód pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-131">The following example shows the configuration code for the binding.</span></span>

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="9cf9f-132">Konfigurace služby pro použití poskytovatele členství</span><span class="sxs-lookup"><span data-stu-id="9cf9f-132">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="9cf9f-133">Jako podřízený `<system.serviceModel>` prvek elementu přidejte [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element</span><span class="sxs-lookup"><span data-stu-id="9cf9f-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="9cf9f-134">Přidejte [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do `behaviors` prvku <>.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-134">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="9cf9f-135">Přidejte [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) a nastavte `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-135">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="9cf9f-136">Přidejte [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) do `behavior` prvku <>.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-136">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="9cf9f-137">Přidejte [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) k `<serviceCredentials>` elementu.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-137">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="9cf9f-138">Nastavte `userNamePasswordValidationMode` atribut na `MembershipProvider` .</span><span class="sxs-lookup"><span data-stu-id="9cf9f-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="9cf9f-139">Pokud `userNamePasswordValidationMode` hodnota není nastavená, WCF místo poskytovatele členství v ASP.NET použije ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="9cf9f-140">Nastavte `membershipProviderName` atribut na název zprostředkovatele (zadaný při přidávání poskytovatele v prvním postupu v tomto tématu).</span><span class="sxs-lookup"><span data-stu-id="9cf9f-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="9cf9f-141">Následující příklad ukazuje `<serviceCredentials>` fragment na tento bod.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

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

## <a name="example"></a><span data-ttu-id="9cf9f-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="9cf9f-142">Example</span></span>

<span data-ttu-id="9cf9f-143">Následující kód ukazuje konfiguraci služby, která používá funkci členství ASP.</span><span class="sxs-lookup"><span data-stu-id="9cf9f-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9cf9f-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cf9f-144">See also</span></span>

- [<span data-ttu-id="9cf9f-145">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="9cf9f-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="9cf9f-146">Členství a poskytovatel rolí</span><span class="sxs-lookup"><span data-stu-id="9cf9f-146">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
