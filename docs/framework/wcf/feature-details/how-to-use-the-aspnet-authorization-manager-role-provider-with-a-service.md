---
title: 'Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 009b96defdf27591ddb98afaa684745b5fcbe0d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184802"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="55cfd-102">Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="55cfd-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="55cfd-103">Když ASP.NET hostitelem webové služby, můžete do aplikace integrovat Správce autorizací a poskytnout tak autorizaci služby.</span><span class="sxs-lookup"><span data-stu-id="55cfd-103">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="55cfd-104">Správce autorizací umožňuje vývojáři aplikace definovat jednotlivé operace, které lze seskupit a vytvořit úkoly.</span><span class="sxs-lookup"><span data-stu-id="55cfd-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="55cfd-105">Správce pak může povolit role k provádění konkrétních úkolů nebo jednotlivých operací.</span><span class="sxs-lookup"><span data-stu-id="55cfd-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="55cfd-106">Nástroj Authorization Manager poskytuje nástroj pro správu jako modul snap-in konzoly MMC (MMC) pro správu rolí, úkolů, operací a uživatelů.</span><span class="sxs-lookup"><span data-stu-id="55cfd-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="55cfd-107">Správci konfigurují úložiště zásad Správce autorizací v souboru XML, službě Active Directory nebo v úložišti služby AD (Active Directory).</span><span class="sxs-lookup"><span data-stu-id="55cfd-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="55cfd-108">Správce autorizací je integrován do aplikace konfigurací nástroje Správce autorizací ASP.NET zprostředkovatele rolí pro ASP.NET aplikaci, která je hostitelem webové služby.</span><span class="sxs-lookup"><span data-stu-id="55cfd-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="55cfd-109">Stejně jako ostatní poskytovatelé rolí ASP.NET je zprostředkovatel `providers` role Správce autorizací ASP.NET konfigurován pomocí prvku <>.</span><span class="sxs-lookup"><span data-stu-id="55cfd-109">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="55cfd-110">Následující příklad kódu je část konfiguračního souboru pro webovou službu, která integruje Správce autorizací do aplikace.</span><span class="sxs-lookup"><span data-stu-id="55cfd-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
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
  
 <span data-ttu-id="55cfd-111">Další informace o integraci zprostředkovatele rolí ASP.NET s aplikací WCF naleznete [v tématu How to: Use the ASP.NET role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="55cfd-111">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="55cfd-112">Další informace o používání Správce autorizací s ASP.NET naleznete v [tématu How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="55cfd-112">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55cfd-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="55cfd-113">See also</span></span>

- [<span data-ttu-id="55cfd-114">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="55cfd-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
