---
title: 'Postupy: Použití zprostředkovatele rolí ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: ddfedeb2491998f64ab241ceba303d50d0714351
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184773"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="a4c03-102">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="a4c03-102">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="a4c03-103">Poskytovatel rolí ASP.NET (ve spojení s poskytovatelem členství ASP.NET) je funkce, která umožňuje vývojářům ASP.NET vytvářet weby, které uživatelům umožňují vytvořit účet s webem a přiřadit role pro účely autorizace.</span><span class="sxs-lookup"><span data-stu-id="a4c03-103">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="a4c03-104">Pomocí této funkce může každý uživatel vytvořit účet s webem a přihlásit se pro výhradní přístup k webu a jeho službám.</span><span class="sxs-lookup"><span data-stu-id="a4c03-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="a4c03-105">To je na rozdíl od zabezpečení systému Windows, který vyžaduje, aby uživatelé měli účty v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a4c03-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="a4c03-106">Místo toho může web a jeho služby používat každý uživatel, který zadá svá pověření (kombinace uživatelského jména a hesla).</span><span class="sxs-lookup"><span data-stu-id="a4c03-106">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="a4c03-107">Ukázková aplikace naleznete v [tématu Členství a zprostředkovatel role](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="a4c03-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="a4c03-108">Další informace o funkci ASP.NET poskytovatele členství naleznete v [tématu How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="a4c03-108">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="a4c03-109">Funkce zprostředkovatele rolí používá k ukládání informací o uživateli databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a4c03-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="a4c03-110">Vývojáři Windows Communication Foundation (WCF) mohou tyto funkce využívat z bezpečnostních důvodů.</span><span class="sxs-lookup"><span data-stu-id="a4c03-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="a4c03-111">Při integraci do aplikace WCF musí uživatelé zadat kombinaci uživatelského jména a hesla do klientské aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="a4c03-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="a4c03-112">Chcete-li povolit WCF používat databázi, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> musíte vytvořit <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> instanci třídy, nastavit její vlastnost <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>a <xref:System.ServiceModel.ServiceHost> přidat instanci do kolekce chování, která je hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="a4c03-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="a4c03-113">Konfigurace zprostředkovatele rolí</span><span class="sxs-lookup"><span data-stu-id="a4c03-113">Configure the role provider</span></span>  
  
1. <span data-ttu-id="a4c03-114">V souboru Web.config pod `system.web` elementem <`roleManager`> přidejte `enabled` element `true`<> a nastavte jeho atribut na .</span><span class="sxs-lookup"><span data-stu-id="a4c03-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="a4c03-115">Nastavte `defaultProvider` atribut `SqlRoleProvider`na .</span><span class="sxs-lookup"><span data-stu-id="a4c03-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="a4c03-116">Jako podřízený prvek `roleManager` <> přidejte prvek> <. `providers`</span><span class="sxs-lookup"><span data-stu-id="a4c03-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="a4c03-117">Jako podřízený prvek `providers` <> přidejte `add` prvek <> s následujícími `name` `type`atributy nastavenými na příslušné hodnoty: , , `connectionStringName`a `applicationName`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a4c03-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
    ```xml  
    <!-- Configure the Sql Role Provider. -->  
    <roleManager enabled ="true"
     defaultProvider ="SqlRoleProvider" >  
       <providers>  
         <add name ="SqlRoleProvider"
           type="System.Web.Security.SqlRoleProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipAndRoleProviderSample"/>  
       </providers>  
    </roleManager>  
    ```  
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="a4c03-118">Konfigurace služby tak, aby používala zprostředkovatele rolí</span><span class="sxs-lookup"><span data-stu-id="a4c03-118">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="a4c03-119">Do souboru Web.config přidejte prvek [ \<system.serviceModel>.](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a4c03-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="a4c03-120">Přidejte [ \<prvek chování>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) `system.ServiceModel` prvku <>.</span><span class="sxs-lookup"><span data-stu-id="a4c03-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="a4c03-121">Přidejte [ \<>serviceBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) `behaviors` do prvku <>.</span><span class="sxs-lookup"><span data-stu-id="a4c03-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="a4c03-122">Přidejte [ \<prvek>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) chování `name` a nastavte atribut na příslušnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a4c03-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="a4c03-123">Přidejte [ \<>serviceAuthorization](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) `behavior` do prvku <>.</span><span class="sxs-lookup"><span data-stu-id="a4c03-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="a4c03-124">Nastavte `principalPermissionMode` atribut `UseAspNetRoles`na .</span><span class="sxs-lookup"><span data-stu-id="a4c03-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="a4c03-125">Nastavte `roleProviderName` atribut `SqlRoleProvider`na .</span><span class="sxs-lookup"><span data-stu-id="a4c03-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="a4c03-126">Následující příklad ukazuje fragment konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a4c03-126">The following example shows a fragment of the configuration.</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a4c03-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4c03-127">See also</span></span>

- [<span data-ttu-id="a4c03-128">Členství a zprostředkovatel rolí</span><span class="sxs-lookup"><span data-stu-id="a4c03-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [<span data-ttu-id="a4c03-129">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a4c03-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
