---
title: 'Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 778af929b4cfc96ce0683d304be5f8fb87a0e47b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880204"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="ae2b1-102">Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="ae2b1-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="ae2b1-103">Při technologie ASP.NET je hostitelem webové služby, můžete začlenit do aplikace a poskytovalo autorizace ve službě Správce autorizací.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-103">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="ae2b1-104">Správce autorizací umožňuje vývojář aplikace definovat jednotlivé operace, které mohou být seskupeny do formuláře úlohy.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="ae2b1-105">Správce pak může autorizovat role provádět konkrétní úlohy nebo jednotlivé operace.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="ae2b1-106">Správce autorizací poskytuje nástroje pro správu jako modul snap-in konzoly Microsoft Management Console (MMC) ke správě rolí, úloh, oddělení a uživatelů.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="ae2b1-107">Správci konfigurovat úložiště Správce autorizací zásady v souboru XML, Active Directory, nebo v režimu aplikace Active Directory (ADAM) s aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="ae2b1-108">Správce autorizací je integrovaná do aplikace podle konfigurace zprostředkovatele role Správce autorizací ASP.NET pro aplikaci ASP.NET, který je hostitelem webové služby.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="ae2b1-109">Stejně jako ostatní zprostředkovatelů rolí prostředí ASP.NET, je nakonfigurován pomocí zprostředkovatele role Správce autorizací ASP.NET <`providers`> element.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-109">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="ae2b1-110">Následující příklad kódu je část konfigurační soubor pro webovou službu, je integrace Správce autorizací do aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae2b1-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
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
  
 <span data-ttu-id="ae2b1-111">Další informace o integraci poskytovatele rolí prostředí ASP.NET se službou WCF aplikace najdete v tématu [jak: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="ae2b1-111">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="ae2b1-112">Další informace o používání Správce autorizací pomocí technologie ASP.NET, naleznete v tématu [jak: Použití Správce autorizací (AzMan) s technologií ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).</span><span class="sxs-lookup"><span data-stu-id="ae2b1-112">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae2b1-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae2b1-113">See also</span></span>

- [<span data-ttu-id="ae2b1-114">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="ae2b1-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
