---
title: 'Postupy: Použití zprostředkovatele rolí ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 20ffd1bb51bc2d6ac106927f805c7349c12059c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209083"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="70a2b-102">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="70a2b-102">How to: Use the ASP.NET Role Provider with a Service</span></span>
<span data-ttu-id="70a2b-103">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Zprostředkovatel rolí (ve spojení s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatel členství) je funkce, která umožňuje [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] vývojářům vytvářet weby, které uživatelům umožní vytvoření účtu s lokalitou a přiřadit role pro autorizaci účely.</span><span class="sxs-lookup"><span data-stu-id="70a2b-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider (in conjunction with the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider) is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="70a2b-104">Pomocí této funkce může každý uživatel zřídit účet s lokalitou a přihlaste pro výhradní přístup k webu a jeho služeb.</span><span class="sxs-lookup"><span data-stu-id="70a2b-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="70a2b-105">To se liší od zabezpečení Windows, což vyžaduje, aby uživatelé mají účty v doméně Windows.</span><span class="sxs-lookup"><span data-stu-id="70a2b-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="70a2b-106">Každý uživatel, který dodává své přihlašovací údaje (kombinaci uživatelského jména/hesla) můžete místo toho použijte webu a jeho služeb.</span><span class="sxs-lookup"><span data-stu-id="70a2b-106">Instead, any user who supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="70a2b-107">Ukázková aplikace, najdete v části [členství a poskytovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="70a2b-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="70a2b-108">Další informace o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkci zprostředkovatele členství, naleznete v tématu [jak: Používání poskytovatele členství ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="70a2b-108">For more information about the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
 <span data-ttu-id="70a2b-109">Funkce poskytovatele role používá databázi serveru SQL Server k ukládání informací o uživateli.</span><span class="sxs-lookup"><span data-stu-id="70a2b-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="70a2b-110">Windows Communication Foundation (WCF) vývojáři mohou využít těchto funkcí z bezpečnostních důvodů.</span><span class="sxs-lookup"><span data-stu-id="70a2b-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="70a2b-111">Při integraci do aplikace WCF, uživatelé musí zadat uživatelské jméno/heslo kombinace do klientské aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="70a2b-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="70a2b-112">Pokud chcete povolit WCF k použití databáze, musíte vytvořit instanci <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> třídy, nastavte jeho <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastnost <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>a přidat do kolekce vlastností pro instanci <xref:System.ServiceModel.ServiceHost> , který je hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="70a2b-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
### <a name="to-configure-the-role-provider"></a><span data-ttu-id="70a2b-113">Konfigurace zprostředkovatele rolí</span><span class="sxs-lookup"><span data-stu-id="70a2b-113">To configure the role provider</span></span>  
  
1.  <span data-ttu-id="70a2b-114">V souboru Web.config v části <`system.web`> element, přidat <`roleManager`> element a nastavte jeho `enabled` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="70a2b-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2.  <span data-ttu-id="70a2b-115">Nastavte `defaultProvider` atribut `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="70a2b-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3.  <span data-ttu-id="70a2b-116">Jako podřízené <`roleManager`> element, přidejte <`providers`> element.</span><span class="sxs-lookup"><span data-stu-id="70a2b-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4.  <span data-ttu-id="70a2b-117">Jako podřízené <`providers`> element, přidejte <`add`> element s následujícími atributy nastaven na odpovídající hodnoty: `name`, `type`, `connectionStringName`, a `applicationName`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="70a2b-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="70a2b-118">Postup konfigurace služby použití zprostředkovatele rolí</span><span class="sxs-lookup"><span data-stu-id="70a2b-118">To configure the service to use the role provider</span></span>  
  
1.  <span data-ttu-id="70a2b-119">V souboru Web.config, přidejte [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="70a2b-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="70a2b-120">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu <`system.ServiceModel`> element.</span><span class="sxs-lookup"><span data-stu-id="70a2b-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3.  <span data-ttu-id="70a2b-121">Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) k <`behaviors`> element.</span><span class="sxs-lookup"><span data-stu-id="70a2b-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4.  <span data-ttu-id="70a2b-122">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu a nastavte `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="70a2b-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5.  <span data-ttu-id="70a2b-123">Přidat [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) k <`behavior`> element.</span><span class="sxs-lookup"><span data-stu-id="70a2b-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6.  <span data-ttu-id="70a2b-124">Nastavte `principalPermissionMode` atribut `UseAspNetRoles`.</span><span class="sxs-lookup"><span data-stu-id="70a2b-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7.  <span data-ttu-id="70a2b-125">Nastavte `roleProviderName` atribut `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="70a2b-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="70a2b-126">Následující příklad ukazuje část konfigurace.</span><span class="sxs-lookup"><span data-stu-id="70a2b-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70a2b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70a2b-127">See also</span></span>

- [<span data-ttu-id="70a2b-128">Členství a poskytovatel rolí</span><span class="sxs-lookup"><span data-stu-id="70a2b-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [<span data-ttu-id="70a2b-129">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="70a2b-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
