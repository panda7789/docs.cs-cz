---
title: 'Postupy: Používání poskytovatele členství ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 8011b026e857dd6e5815ef7da00c1c33db8b5b4d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310353"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="d2396-102">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d2396-102">How to: Use the ASP.NET Membership Provider</span></span>
<span data-ttu-id="d2396-103">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Zprostředkovatele členství je funkce, která umožňuje [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] vývojářům vytvářet weby, které umožňují uživatelům vytvářet jedinečné uživatelské jméno a heslo kombinace.</span><span class="sxs-lookup"><span data-stu-id="d2396-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="d2396-104">S Azure může každý uživatel zřídit účet s lokalitou a přihlášení na exkluzivní přístup k webu a jeho služeb.</span><span class="sxs-lookup"><span data-stu-id="d2396-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="d2396-105">To se liší od zabezpečení Windows, což vyžaduje, aby uživatelé mají účty v doméně Windows.</span><span class="sxs-lookup"><span data-stu-id="d2396-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="d2396-106">Každý uživatel, který dodává své přihlašovací údaje (kombinaci uživatelského jména/hesla) můžete místo toho použijte webu a jeho služeb.</span><span class="sxs-lookup"><span data-stu-id="d2396-106">Instead, any user that supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="d2396-107">Ukázková aplikace, najdete v části [členství a poskytovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d2396-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="d2396-108">Informace o používání [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkci zprostředkovatele rolí, najdete v článku [jak: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="d2396-108">For information about using the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>  
  
 <span data-ttu-id="d2396-109">Funkce členství vyžaduje použití databáze SQL serveru k ukládání informací o uživateli.</span><span class="sxs-lookup"><span data-stu-id="d2396-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="d2396-110">Tato funkce zároveň metody pro výzvu s dotaz všechny uživatele, kteří zapomenou své heslo.</span><span class="sxs-lookup"><span data-stu-id="d2396-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>  
  
 <span data-ttu-id="d2396-111">Windows Communication Foundation (WCF) vývojáři mohou využít těchto funkcí z bezpečnostních důvodů.</span><span class="sxs-lookup"><span data-stu-id="d2396-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="d2396-112">Při integraci do aplikace WCF, uživatelé musí zadat uživatelské jméno/heslo kombinace do klientské aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="d2396-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="d2396-113">Chcete-li přenést data do služby WCF, použijte vazbu, která podporuje uživatelské jméno/heslo přihlašovacích údajů, jako například <xref:System.ServiceModel.WSHttpBinding> (v konfiguraci [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) a nastavit typ přihlašovacích údajů k klienta`UserName`.</span><span class="sxs-lookup"><span data-stu-id="d2396-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="d2396-114">Ve službě, zabezpečení WCF ověřuje uživatele na základě uživatelského jména a hesla a také přiřadí roli určeného [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role.</span><span class="sxs-lookup"><span data-stu-id="d2396-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2396-115">WCF neposkytuje metody k naplnění databáze pomocí kombinace uživatelské jméno/heslo nebo jiné informace o uživateli.</span><span class="sxs-lookup"><span data-stu-id="d2396-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>  
  
### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="d2396-116">Konfigurace zprostředkovatele členství</span><span class="sxs-lookup"><span data-stu-id="d2396-116">To configure the membership provider</span></span>  
  
1. <span data-ttu-id="d2396-117">V souboru Web.config v části <`system.web`> element, vytvořit <`membership`> element.</span><span class="sxs-lookup"><span data-stu-id="d2396-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>  
  
2. <span data-ttu-id="d2396-118">V části `<membership>` elementu, vytvořit `<providers>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d2396-118">Under the `<membership>` element, create a `<providers>` element.</span></span>  
  
3. <span data-ttu-id="d2396-119">Jako podřízené <`providers`> element, přidejte `<clear />` element vyprázdnit kolekce zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="d2396-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>  
  
4. <span data-ttu-id="d2396-120">V části `<clear />` elementu, vytvoření <`add`> element s následujícími atributy nastaven na odpovídající hodnoty: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, a `passwordFormat`.</span><span class="sxs-lookup"><span data-stu-id="d2396-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="d2396-121">`name` Atributu se použije v pozdější jako hodnotu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="d2396-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="d2396-122">Následující příklad nastaví na `SqlMembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="d2396-122">The following example sets it to `SqlMembershipProvider`.</span></span>  
  
     <span data-ttu-id="d2396-123">Následující příklad ukazuje konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="d2396-123">The following example shows the configuration section.</span></span>  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="d2396-124">Ke konfiguraci služby zabezpečení tak, aby přijímal kombinace uživatelského jména/hesla</span><span class="sxs-lookup"><span data-stu-id="d2396-124">To configure service security to accept the user name/password combination</span></span>  
  
1. <span data-ttu-id="d2396-125">V konfiguračním souboru v části [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, přidejte [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span><span class="sxs-lookup"><span data-stu-id="d2396-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
2. <span data-ttu-id="d2396-126">Přidat [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do části vazeb.</span><span class="sxs-lookup"><span data-stu-id="d2396-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="d2396-127">Další informace o vytváření element vazby WCF najdete v tématu [jak: Zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d2396-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
3. <span data-ttu-id="d2396-128">Nastavte `mode` atribut `<security>` elementu `Message`.</span><span class="sxs-lookup"><span data-stu-id="d2396-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>  
  
4. <span data-ttu-id="d2396-129">Nastavte `clientCredentialType` atribut <`message`> element `UserName`.</span><span class="sxs-lookup"><span data-stu-id="d2396-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="d2396-130">Určuje, že páru jméno/heslo uživatele se použije jako pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="d2396-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>  
  
     <span data-ttu-id="d2396-131">Následující příklad ukazuje kód konfigurace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="d2396-131">The following example shows the configuration code for the binding.</span></span>  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="d2396-132">Ke konfiguraci služby pro používání poskytovatele členství</span><span class="sxs-lookup"><span data-stu-id="d2396-132">To configure a service to use the membership provider</span></span>  
  
1. <span data-ttu-id="d2396-133">Jako podřízené `<system.serviceModel>` elementu, přidejte [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) – element</span><span class="sxs-lookup"><span data-stu-id="d2396-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>  
  
2. <span data-ttu-id="d2396-134">Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k <`behaviors`> element.</span><span class="sxs-lookup"><span data-stu-id="d2396-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
3. <span data-ttu-id="d2396-135">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) a nastavit `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d2396-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="d2396-136">Přidat [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) k <`behavior`> element.</span><span class="sxs-lookup"><span data-stu-id="d2396-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>  
  
5. <span data-ttu-id="d2396-137">Přidat [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) k `<serviceCredentials>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d2396-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>  
  
6. <span data-ttu-id="d2396-138">Nastavte `userNamePasswordValidationMode` atribut `MembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="d2396-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d2396-139">Pokud `userNamePasswordValidationMode` hodnota není nastavená, WCF používá ověřování Windows namísto [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství.</span><span class="sxs-lookup"><span data-stu-id="d2396-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider.</span></span>  
  
7. <span data-ttu-id="d2396-140">Nastavte `membershipProviderName` atribut název zprostředkovatele (zadanými při přidávání zprostředkovatele v prvním postupu v tomto tématu).</span><span class="sxs-lookup"><span data-stu-id="d2396-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="d2396-141">Následující příklad ukazuje `<serviceCredentials>` fragmentu do tohoto bodu.</span><span class="sxs-lookup"><span data-stu-id="d2396-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="d2396-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2396-142">Example</span></span>  
 <span data-ttu-id="d2396-143">Následující kód znázorňuje konfiguraci pro službu, která používá funkci ASP členství.</span><span class="sxs-lookup"><span data-stu-id="d2396-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d2396-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2396-144">See also</span></span>

- [<span data-ttu-id="d2396-145">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="d2396-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="d2396-146">Členství a poskytovatel rolí</span><span class="sxs-lookup"><span data-stu-id="d2396-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
