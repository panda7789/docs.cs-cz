---
title: 'Postupy: použití zprostředkovatele Role Správce autorizací ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: c21c1a80468bd81f2df69009afd2be86ee714250
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386703"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="85d86-102">Postupy: použití zprostředkovatele Role Správce autorizací ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="85d86-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="85d86-103">Když [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hostuje webovou službu, můžete začlenit do aplikace a poskytovalo autorizace ve službě Správce autorizací.</span><span class="sxs-lookup"><span data-stu-id="85d86-103">When [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="85d86-104">Správce autorizací umožňuje vývojář aplikace definovat jednotlivé operace, které mohou být seskupeny do formuláře úlohy.</span><span class="sxs-lookup"><span data-stu-id="85d86-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="85d86-105">Správce pak může autorizovat role provádět konkrétní úlohy nebo jednotlivé operace.</span><span class="sxs-lookup"><span data-stu-id="85d86-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="85d86-106">Správce autorizací poskytuje nástroje pro správu jako modul snap-in konzoly Microsoft Management Console (MMC) ke správě rolí, úloh, oddělení a uživatelů.</span><span class="sxs-lookup"><span data-stu-id="85d86-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="85d86-107">Správci konfigurovat úložiště Správce autorizací zásady v souboru XML, Active Directory, nebo v režimu aplikace Active Directory (ADAM) s aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="85d86-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="85d86-108">Správce autorizací je součástí aplikace tím, že nakonfigurujete Správce autorizací [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikaci, která je hostitelem webové služby.</span><span class="sxs-lookup"><span data-stu-id="85d86-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider for the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is hosting the Web service.</span></span> <span data-ttu-id="85d86-109">Stejně jako jiné [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatelů rolí Správce autorizací [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí je nakonfigurovaný nástrojem <`providers`> element.</span><span class="sxs-lookup"><span data-stu-id="85d86-109">Like other [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role providers, the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="85d86-110">Následující příklad kódu je část konfigurační soubor pro webovou službu, je integrace Správce autorizací do aplikace.</span><span class="sxs-lookup"><span data-stu-id="85d86-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"   
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="85d86-111">Další informace o integraci [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí s WCF aplikací, najdete v článku [postupy: použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="85d86-111">For more information about integrating an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="85d86-112">Další informace o používání Správce autorizací s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], naleznete v tématu [postupy: použití Správce autorizací (AzMan) s prostředím ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).</span><span class="sxs-lookup"><span data-stu-id="85d86-112">For more information about using Authorization Manager with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d86-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="85d86-113">See Also</span></span>  
 [<span data-ttu-id="85d86-114">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="85d86-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
