---
title: 'Postupy: Používání poskytovatele členství ASP.NET'
description: Přečtěte si, jak poskytovatel členství ASP.NET podporuje webové stránky, které uživatelům umožňují vytvořit uživatelské jméno a heslo pro přístup bez použití doménového účtu systému Windows.
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 6d527993dcf1fc5d5cd39bf22c3e772baf60e62f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246724"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="0a3e5-103">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0a3e5-103">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="0a3e5-104">Poskytovatel členství ASP.NET je funkce, která vývojářům ASP.NET umožňuje vytvářet weby, které uživatelům umožňují vytvářet jedinečné kombinace uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-104">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="0a3e5-105">U tohoto zařízení může každý uživatel vytvořit účet s webem a přihlásit se pro výhradní přístup k webu a jeho službám.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-105">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="0a3e5-106">To je na rozdíl od zabezpečení systému Windows, které vyžaduje, aby uživatelé měli účty v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-106">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="0a3e5-107">Místo toho může web a jeho služby používat libovolný uživatel, který poskytuje své přihlašovací údaje (kombinace uživatelské jméno/heslo).</span><span class="sxs-lookup"><span data-stu-id="0a3e5-107">Instead, any user that supplies their credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="0a3e5-108">Ukázkovou aplikaci najdete v tématu věnovaném [členství a zprostředkovateli rolí](../samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="0a3e5-108">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="0a3e5-109">Informace o použití funkce poskytovatele rolí ASP.NET naleznete v tématu [How to: use the ASP.NET role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="0a3e5-109">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="0a3e5-110">Funkce členství vyžaduje použití databáze SQL Server k uložení informací o uživateli.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-110">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="0a3e5-111">Tato funkce zahrnuje také metody pro dotazování s otázkou, které si uživatelé zapomněli heslo.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-111">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="0a3e5-112">Vývojáři Windows Communication Foundation (WCF) můžou využít výhod těchto funkcí z hlediska zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-112">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="0a3e5-113">Při integraci do aplikace WCF musí uživatelé do klientské aplikace WCF dodat kombinaci uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-113">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="0a3e5-114">Chcete-li přenést data do služby WCF, použijte vazbu, která podporuje přihlašovací údaje uživatelského jména a hesla, například <xref:System.ServiceModel.WSHttpBinding> (v konfiguraci [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ), a nastavte typ pověření klienta na `UserName` .</span><span class="sxs-lookup"><span data-stu-id="0a3e5-114">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="0a3e5-115">Ve službě Služba WCF Security ověřuje uživatele na základě uživatelského jména a hesla a také přiřadí roli určenou rolí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-115">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="0a3e5-116">WCF neposkytuje metody pro naplnění databáze pomocí kombinace uživatelského jména a hesla nebo jiných informací o uživateli.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-116">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="0a3e5-117">Konfigurace poskytovatele členství</span><span class="sxs-lookup"><span data-stu-id="0a3e5-117">To configure the membership provider</span></span>

1. <span data-ttu-id="0a3e5-118">V souboru Web.config v rámci `system.web` elementu <> vytvořte `membership` prvek <>.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-118">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="0a3e5-119">V rámci `<membership>` elementu vytvořte `<providers>` element.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-119">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="0a3e5-120">Jako podřízený `providers` prvku <> přidejte `<clear />` prvek pro vyprázdnění kolekce zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-120">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="0a3e5-121">V rámci `<clear />` elementu vytvořte <`add`> prvek s následujícími atributy nastavenými na příslušné hodnoty: `name` , `type` , `connectionStringName` , `applicationName` , `enablePasswordRetrieval` , `enablePasswordReset` ,, a `requiresQuestionAndAnswer` `requiresUniqueEmail` `passwordFormat` .</span><span class="sxs-lookup"><span data-stu-id="0a3e5-121">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="0a3e5-122">`name`Atribut je použit později jako hodnota v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-122">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="0a3e5-123">Následující příklad nastaví na `SqlMembershipProvider` .</span><span class="sxs-lookup"><span data-stu-id="0a3e5-123">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="0a3e5-124">Následující příklad ukazuje konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-124">The following example shows the configuration section.</span></span>

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="0a3e5-125">Konfigurace zabezpečení služby pro přijetí kombinace uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="0a3e5-125">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="0a3e5-126">V konfiguračním souboru, pod [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) prvkem, přidejte [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-126">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="0a3e5-127">Přidejte [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) do části Bindings (vazby).</span><span class="sxs-lookup"><span data-stu-id="0a3e5-127">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="0a3e5-128">Další informace o vytvoření elementu vazby WCF naleznete v tématu [How to: zadat vazbu služby v konfiguraci](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="0a3e5-128">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="0a3e5-129">Nastavte `mode` atribut `<security>` elementu na `Message` .</span><span class="sxs-lookup"><span data-stu-id="0a3e5-129">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="0a3e5-130">Nastavte `clientCredentialType` atribut `message` prvku <> na `UserName` .</span><span class="sxs-lookup"><span data-stu-id="0a3e5-130">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="0a3e5-131">Tím se určí, že se jako přihlašovací údaje klienta budou používat dvojice uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-131">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="0a3e5-132">Následující příklad ukazuje konfigurační kód pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-132">The following example shows the configuration code for the binding.</span></span>

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="0a3e5-133">Konfigurace služby pro použití poskytovatele členství</span><span class="sxs-lookup"><span data-stu-id="0a3e5-133">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="0a3e5-134">Jako podřízený `<system.serviceModel>` prvek elementu přidejte [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element</span><span class="sxs-lookup"><span data-stu-id="0a3e5-134">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="0a3e5-135">Přidejte [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do `behaviors` prvku <>.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-135">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="0a3e5-136">Přidejte [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) a nastavte `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-136">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="0a3e5-137">Přidejte [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) do `behavior` prvku <>.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-137">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="0a3e5-138">Přidejte [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) k `<serviceCredentials>` elementu.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-138">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="0a3e5-139">Nastavte `userNamePasswordValidationMode` atribut na `MembershipProvider` .</span><span class="sxs-lookup"><span data-stu-id="0a3e5-139">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0a3e5-140">Pokud `userNamePasswordValidationMode` hodnota není nastavená, WCF místo poskytovatele členství v ASP.NET použije ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-140">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="0a3e5-141">Nastavte `membershipProviderName` atribut na název zprostředkovatele (zadaný při přidávání poskytovatele v prvním postupu v tomto tématu).</span><span class="sxs-lookup"><span data-stu-id="0a3e5-141">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="0a3e5-142">Následující příklad ukazuje `<serviceCredentials>` fragment na tento bod.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-142">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

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

## <a name="example"></a><span data-ttu-id="0a3e5-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a3e5-143">Example</span></span>

<span data-ttu-id="0a3e5-144">Následující kód ukazuje konfiguraci služby, která používá funkci členství ASP.</span><span class="sxs-lookup"><span data-stu-id="0a3e5-144">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0a3e5-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a3e5-145">See also</span></span>

- [<span data-ttu-id="0a3e5-146">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="0a3e5-146">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="0a3e5-147">Členství a poskytovatel rolí</span><span class="sxs-lookup"><span data-stu-id="0a3e5-147">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
