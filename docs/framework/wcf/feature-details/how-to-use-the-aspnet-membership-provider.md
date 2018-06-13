---
title: 'Postupy: Používání poskytovatele členství ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: d71e3679f4bf395b240c330fc573d6f613d1be07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495291"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="aab10-102">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="aab10-102">How to: Use the ASP.NET Membership Provider</span></span>
<span data-ttu-id="aab10-103">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Zprostředkovatele členství je funkce, která umožňuje [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] vývojářům vytvářet weby, které umožňuje uživatelům vytvářet jedinečná uživatelská jména a hesla kombinace.</span><span class="sxs-lookup"><span data-stu-id="aab10-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="aab10-104">S Pokud tuto funkci můžete každý uživatel zřídit účet s lokalitou a přihlášení výhradní přístup k webu a jeho služeb.</span><span class="sxs-lookup"><span data-stu-id="aab10-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="aab10-105">Tím se liší od zabezpečení systému Windows, která vyžaduje, aby uživatelé mají účty v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="aab10-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="aab10-106">Každý uživatel, který poskytuje své přihlašovací údaje (kombinace uživatelského jména a hesla), můžete místo toho použijte webu a jeho služeb.</span><span class="sxs-lookup"><span data-stu-id="aab10-106">Instead, any user that supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="aab10-107">Ukázkovou aplikaci, najdete v části [členství a poskytovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="aab10-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="aab10-108">Informace o používání [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role zprostředkovatele funkce, najdete v části [postupy: použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="aab10-108">For information about using the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>  
  
 <span data-ttu-id="aab10-109">Funkce členství vyžaduje použití databáze systému SQL Server k ukládání informací o uživateli.</span><span class="sxs-lookup"><span data-stu-id="aab10-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="aab10-110">Tato funkce také obsahuje metody pro dotazování s dotaz uživatelé, kteří zapomenou své heslo.</span><span class="sxs-lookup"><span data-stu-id="aab10-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>  
  
 <span data-ttu-id="aab10-111">Windows Communication Foundation (WCF) vývojáři mohou využít těchto funkcí z bezpečnostních důvodů.</span><span class="sxs-lookup"><span data-stu-id="aab10-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="aab10-112">Při integraci do aplikace WCF, musí uživatelé zadají uživatelské jméno a heslo kombinaci aplikaci klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="aab10-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="aab10-113">K přenosu dat na službu WCF, použijte vazbu, která podporuje pověření jména a hesla uživatele, například <xref:System.ServiceModel.WSHttpBinding> (v konfiguraci [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) a typ přihlašovacích údajů k pronastaveníklienta`UserName`.</span><span class="sxs-lookup"><span data-stu-id="aab10-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="aab10-114">Ve službě, zabezpečení WCF ověřuje uživatele na základě uživatelské jméno a heslo a také přiřadí roli určeného [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role.</span><span class="sxs-lookup"><span data-stu-id="aab10-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aab10-115">WCF neposkytuje metody k naplnění databáze s kombinací uživatelské jméno a heslo nebo Další informace o uživateli.</span><span class="sxs-lookup"><span data-stu-id="aab10-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>  
  
### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="aab10-116">Chcete-li konfigurovat členství</span><span class="sxs-lookup"><span data-stu-id="aab10-116">To configure the membership provider</span></span>  
  
1.  <span data-ttu-id="aab10-117">V souboru Web.config v části <`system.web`> elementu, vytvoření <`membership`> elementu.</span><span class="sxs-lookup"><span data-stu-id="aab10-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>  
  
2.  <span data-ttu-id="aab10-118">V části `<membership>` elementu, vytvoření `<providers>` elementu.</span><span class="sxs-lookup"><span data-stu-id="aab10-118">Under the `<membership>` element, create a `<providers>` element.</span></span>  
  
3.  <span data-ttu-id="aab10-119">Jako podřízené <`providers`> elementu, přidejte `<clear />` elementu, který chcete vyprázdnit kolekce zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="aab10-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>  
  
4.  <span data-ttu-id="aab10-120">V části `<clear />` elementu, vytvořit <`add`> element s následujícími atributy nastaven na příslušné hodnoty: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, a `passwordFormat`.</span><span class="sxs-lookup"><span data-stu-id="aab10-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="aab10-121">`name` Atribut se později používá jako hodnotu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="aab10-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="aab10-122">Následující příklad ji nastaví na `SqlMembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="aab10-122">The following example sets it to `SqlMembershipProvider`.</span></span>  
  
     <span data-ttu-id="aab10-123">Následující příklad ukazuje konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="aab10-123">The following example shows the configuration section.</span></span>  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="aab10-124">Konfigurace zabezpečení služby tak, aby přijímal kombinace uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="aab10-124">To configure service security to accept the user name/password combination</span></span>  
  
1.  <span data-ttu-id="aab10-125">V konfiguračním souboru v části [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, přidejte [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span><span class="sxs-lookup"><span data-stu-id="aab10-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
2.  <span data-ttu-id="aab10-126">Přidat [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do části vazby.</span><span class="sxs-lookup"><span data-stu-id="aab10-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="aab10-127">Další informace o vytváření element vazby WCF najdete v tématu [postupy: zadání vazby služby v konfiguraci](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="aab10-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
3.  <span data-ttu-id="aab10-128">Nastavte `mode` atribut `<security>` element `Message`.</span><span class="sxs-lookup"><span data-stu-id="aab10-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>  
  
4.  <span data-ttu-id="aab10-129">Nastavte `clientCredentialType` atribut <`message`> elementu, který chcete `UserName`.</span><span class="sxs-lookup"><span data-stu-id="aab10-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="aab10-130">Určuje, že pár uživatelské jméno a heslo bude použit jako pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="aab10-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>  
  
     <span data-ttu-id="aab10-131">Následující příklad ukazuje kód konfigurace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="aab10-131">The following example shows the configuration code for the binding.</span></span>  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="aab10-132">Pro konfiguraci služby pro použití poskytovatele členství</span><span class="sxs-lookup"><span data-stu-id="aab10-132">To configure a service to use the membership provider</span></span>  
  
1.  <span data-ttu-id="aab10-133">Jako podřízené `<system.serviceModel>` elementu, přidejte [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) – element</span><span class="sxs-lookup"><span data-stu-id="aab10-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>  
  
2.  <span data-ttu-id="aab10-134">Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) na <`behaviors`> element.</span><span class="sxs-lookup"><span data-stu-id="aab10-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
3.  <span data-ttu-id="aab10-135">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) a nastavte `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="aab10-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="aab10-136">Přidat [ \<– serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) na <`behavior`> element.</span><span class="sxs-lookup"><span data-stu-id="aab10-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>  
  
5.  <span data-ttu-id="aab10-137">Přidat [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) k `<serviceCredentials>` elementu.</span><span class="sxs-lookup"><span data-stu-id="aab10-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>  
  
6.  <span data-ttu-id="aab10-138">Nastavte `userNamePasswordValidationMode` atribut `MembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="aab10-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="aab10-139">Pokud `userNamePasswordValidationMode` hodnota není nastavená, WCF používá ověřování systému Windows místo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství.</span><span class="sxs-lookup"><span data-stu-id="aab10-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider.</span></span>  
  
7.  <span data-ttu-id="aab10-140">Nastavte `membershipProviderName` atribut název zprostředkovatele (zadaný při přidávání zprostředkovatele v prvním postupu v tomto tématu).</span><span class="sxs-lookup"><span data-stu-id="aab10-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="aab10-141">Následující příklad ukazuje `<serviceCredentials>` fragment k tomuto bodu.</span><span class="sxs-lookup"><span data-stu-id="aab10-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="aab10-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="aab10-142">Example</span></span>  
 <span data-ttu-id="aab10-143">Následující kód ukazuje konfiguraci pro službu, která používá funkci ASP členství.</span><span class="sxs-lookup"><span data-stu-id="aab10-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aab10-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="aab10-144">See Also</span></span>  
 [<span data-ttu-id="aab10-145">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="aab10-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [<span data-ttu-id="aab10-146">Členství a zprostředkovatel rolí</span><span class="sxs-lookup"><span data-stu-id="aab10-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
