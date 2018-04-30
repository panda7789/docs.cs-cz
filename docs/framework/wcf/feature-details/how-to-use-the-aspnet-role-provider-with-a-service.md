---
title: 'Postupy: Použití zprostředkovatele rolí ASP.NET se službou'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9180ebe687d61315a66160a6fc95569a0e6b8e72
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="c7340-102">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="c7340-102">How to: Use the ASP.NET Role Provider with a Service</span></span>
<span data-ttu-id="c7340-103">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Zprostředkovatele rolí (ve spojení s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele členství) je funkce, která umožňuje [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] vývojářům vytvářet weby, které uživatelům umožní vytvořit účet s lokalitou a přiřadit role pro autorizaci pro účely.</span><span class="sxs-lookup"><span data-stu-id="c7340-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider (in conjunction with the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider) is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="c7340-104">Pomocí této funkce můžete každý uživatel určit účet s lokalitou a přihlášení pro výhradní přístup k webu a jeho služeb.</span><span class="sxs-lookup"><span data-stu-id="c7340-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="c7340-105">Tím se liší od zabezpečení systému Windows, která vyžaduje, aby uživatelé mají účty v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c7340-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="c7340-106">Každý uživatel, který poskytuje své přihlašovací údaje (kombinace uživatelského jména a hesla), můžete místo toho použijte webu a jeho služeb.</span><span class="sxs-lookup"><span data-stu-id="c7340-106">Instead, any user who supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="c7340-107">Ukázkovou aplikaci, najdete v části [členství a poskytovatel rolí](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="c7340-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="c7340-108">Další informace o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcí zprostředkovatele členství, najdete v části [postupy: použití poskytovatele členství prostředí ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="c7340-108">For more information about the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
 <span data-ttu-id="c7340-109">Zprostředkovatele funkce role používá databázi systému SQL Server uložit informace o uživateli.</span><span class="sxs-lookup"><span data-stu-id="c7340-109">The role provider feature uses a SQL Server database to store user information.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="c7340-110"> Vývojáři mohou využít těchto funkcí z bezpečnostních důvodů.</span><span class="sxs-lookup"><span data-stu-id="c7340-110"> developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="c7340-111">Při integraci do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, musí uživatelé zadat uživatelské jméno a heslo kombinaci k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7340-111">When integrated into a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, users must supply a user name/password combination to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application.</span></span> <span data-ttu-id="c7340-112">Chcete-li povolit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] k použití databáze, musíte vytvořit instanci <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> třídy, nastavte jeho <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastnost <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>a přidat do kolekce chování na instanci <xref:System.ServiceModel.ServiceHost> , který je hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="c7340-112">To enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
### <a name="to-configure-the-role-provider"></a><span data-ttu-id="c7340-113">Chcete-li konfigurovat role</span><span class="sxs-lookup"><span data-stu-id="c7340-113">To configure the role provider</span></span>  
  
1.  <span data-ttu-id="c7340-114">V souboru Web.config v části <`system.web`> elementu, přidejte <`roleManager`> elementu a sadu jeho `enabled` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="c7340-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2.  <span data-ttu-id="c7340-115">Nastavte `defaultProvider` atribut `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="c7340-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3.  <span data-ttu-id="c7340-116">Jako podřízené <`roleManager`> elementu, přidejte <`providers`> elementu.</span><span class="sxs-lookup"><span data-stu-id="c7340-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4.  <span data-ttu-id="c7340-117">Jako podřízené <`providers`> elementu, přidejte <`add`> element s následujícími atributy nastaven na příslušné hodnoty: `name`, `type`, `connectionStringName`, a `applicationName`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c7340-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="c7340-118">Ke konfiguraci služby pro použití poskytovatele role</span><span class="sxs-lookup"><span data-stu-id="c7340-118">To configure the service to use the role provider</span></span>  
  
1.  <span data-ttu-id="c7340-119">V souboru Web.config, přidejte [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span><span class="sxs-lookup"><span data-stu-id="c7340-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="c7340-120">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu, který chcete <`system.ServiceModel`> elementu.</span><span class="sxs-lookup"><span data-stu-id="c7340-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3.  <span data-ttu-id="c7340-121">Přidat [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) na <`behaviors`> element.</span><span class="sxs-lookup"><span data-stu-id="c7340-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4.  <span data-ttu-id="c7340-122">Přidat [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu a sadu `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c7340-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5.  <span data-ttu-id="c7340-123">Přidat [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) na <`behavior`> element.</span><span class="sxs-lookup"><span data-stu-id="c7340-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6.  <span data-ttu-id="c7340-124">Nastavte `principalPermissionMode` atribut `UseAspNetRoles`.</span><span class="sxs-lookup"><span data-stu-id="c7340-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7.  <span data-ttu-id="c7340-125">Nastavte `roleProviderName` atribut `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="c7340-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="c7340-126">Následující příklad ukazuje fragment konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c7340-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c7340-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7340-127">See Also</span></span>  
 [<span data-ttu-id="c7340-128">Členství a zprostředkovatel rolí</span><span class="sxs-lookup"><span data-stu-id="c7340-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)  
 [<span data-ttu-id="c7340-129">Postupy: Používání poskytovatele členství ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c7340-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
