---
title: 'Postupy: Použití zprostředkovatele rolí ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 45eeda046e877b4379d7d0e5edd90fac305f5e44
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595294"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="c0354-102">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="c0354-102">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="c0354-103">Poskytovatel rolí ASP.NET (ve spojení se zprostředkovatelem členství ASP.NET) je funkce, která umožňuje vývojářům ASP.NET vytvářet weby, které uživatelům umožňují vytvořit účet s lokalitou a přiřadit k nim role pro účely autorizace.</span><span class="sxs-lookup"><span data-stu-id="c0354-103">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="c0354-104">Pomocí této funkce může každý uživatel vytvořit účet s webem a přihlásit se pro výhradní přístup k webu a jeho službám.</span><span class="sxs-lookup"><span data-stu-id="c0354-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="c0354-105">To je na rozdíl od zabezpečení systému Windows, které vyžaduje, aby uživatelé měli účty v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c0354-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="c0354-106">Místo toho může web a jeho služby používat libovolný uživatel, který poskytuje své přihlašovací údaje (kombinace uživatelské jméno/heslo).</span><span class="sxs-lookup"><span data-stu-id="c0354-106">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="c0354-107">Ukázkovou aplikaci najdete v tématu věnovaném [členství a zprostředkovateli rolí](../samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="c0354-107">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="c0354-108">Další informace o funkci poskytovatele členství v ASP.NET najdete v tématu [How to: use the ASP.NET Membership Provider](how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="c0354-108">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="c0354-109">Funkce poskytovatele rolí používá k ukládání informací o uživateli databázi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c0354-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="c0354-110">Vývojáři Windows Communication Foundation (WCF) můžou využít výhod těchto funkcí z hlediska zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c0354-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="c0354-111">Při integraci do aplikace WCF musí uživatelé do klientské aplikace WCF dodat kombinaci uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="c0354-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="c0354-112">Chcete-li povolit, aby služba WCF používala databázi, je nutné vytvořit instanci <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> třídy, nastavit její <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastnost na a <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> přidat instanci do kolekce chování <xref:System.ServiceModel.ServiceHost> , která je hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="c0354-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="c0354-113">Konfigurace poskytovatele rolí</span><span class="sxs-lookup"><span data-stu-id="c0354-113">Configure the role provider</span></span>  
  
1. <span data-ttu-id="c0354-114">V souboru Web. config v rámci `system.web` prvku < > přidejte `roleManager` prvek < > a nastavte jeho `enabled` atribut na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="c0354-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="c0354-115">Nastavte `defaultProvider` atribut na `SqlRoleProvider` .</span><span class="sxs-lookup"><span data-stu-id="c0354-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="c0354-116">Jako podřízený `roleManager` prvku <> přidejte `providers` prvek <>.</span><span class="sxs-lookup"><span data-stu-id="c0354-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="c0354-117">Jako podřízený `providers` prvku <> přidejte `add` prvek <> s následujícími atributy nastavenými na příslušné hodnoty: `name` , `type` , `connectionStringName` a `applicationName` , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c0354-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="c0354-118">Nakonfigurujte službu tak, aby používala poskytovatele rolí.</span><span class="sxs-lookup"><span data-stu-id="c0354-118">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="c0354-119">V souboru Web. config přidejte [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span><span class="sxs-lookup"><span data-stu-id="c0354-119">In the Web.config file, add a [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="c0354-120">Přidejte [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) prvek do `system.ServiceModel` prvku <>.</span><span class="sxs-lookup"><span data-stu-id="c0354-120">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="c0354-121">Přidejte [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do `behaviors` prvku <>.</span><span class="sxs-lookup"><span data-stu-id="c0354-121">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="c0354-122">Přidejte [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element a nastavte `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c0354-122">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="c0354-123">Přidejte [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) do `behavior` prvku <>.</span><span class="sxs-lookup"><span data-stu-id="c0354-123">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="c0354-124">Nastavte `principalPermissionMode` atribut na `UseAspNetRoles` .</span><span class="sxs-lookup"><span data-stu-id="c0354-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="c0354-125">Nastavte `roleProviderName` atribut na `SqlRoleProvider` .</span><span class="sxs-lookup"><span data-stu-id="c0354-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="c0354-126">Následující příklad ukazuje fragment konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c0354-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0354-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0354-127">See also</span></span>

- [<span data-ttu-id="c0354-128">Členství a poskytovatel rolí</span><span class="sxs-lookup"><span data-stu-id="c0354-128">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
- [<span data-ttu-id="c0354-129">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c0354-129">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
