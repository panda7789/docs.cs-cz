---
title: 'Postupy: použití zprostředkovatele rolí ASP.NET Authorization Manager se službou'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 20955578ce4d344c2057036c0944557edf737389
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212226"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="83885-102">Postupy: použití zprostředkovatele rolí ASP.NET Authorization Manager se službou</span><span class="sxs-lookup"><span data-stu-id="83885-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="83885-103">Pokud ASP.NET hostuje webovou službu, můžete do aplikace integrovat Správce autorizací a poskytnout službě autorizaci.</span><span class="sxs-lookup"><span data-stu-id="83885-103">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="83885-104">Správce autorizací umožňuje vývojářům aplikací definovat jednotlivé operace, které mohou být seskupeny do úloh formuláře.</span><span class="sxs-lookup"><span data-stu-id="83885-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="83885-105">Správce pak může autorizovat role k provádění konkrétních úkolů nebo jednotlivých operací.</span><span class="sxs-lookup"><span data-stu-id="83885-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="83885-106">Správce autorizací poskytuje nástroj pro správu jako modul snap-in konzoly MMC (Microsoft Management Console) ke správě rolí, úloh, operací a uživatelů.</span><span class="sxs-lookup"><span data-stu-id="83885-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="83885-107">Správci konfigurují úložiště zásad Správce autorizací v souboru XML, ve službě Active Directory nebo v úložišti ADAM (Active Directory Application Mode).</span><span class="sxs-lookup"><span data-stu-id="83885-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="83885-108">Správce autorizací je do aplikace integrován konfigurací zprostředkovatele rolí ASP.NET Správce autorizací pro aplikaci ASP.NET, která je hostitelem webové služby.</span><span class="sxs-lookup"><span data-stu-id="83885-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="83885-109">Stejně jako jiní poskytovatelé rolí ASP.NET je zprostředkovatel rolí ASP.NET Správce autorizací nakonfigurovaný pomocí elementu <`providers`>.</span><span class="sxs-lookup"><span data-stu-id="83885-109">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="83885-110">Následující příklad kódu je část konfiguračního souboru pro webovou službu, která integruje Správce autorizací do aplikace.</span><span class="sxs-lookup"><span data-stu-id="83885-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
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
  
 <span data-ttu-id="83885-111">Další informace o integraci zprostředkovatele rolí ASP.NET s aplikací WCF najdete v tématu [How to: use the ASP.NET provider role with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="83885-111">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="83885-112">Další informace o používání Správce autorizací s ASP.NET najdete v tématu [How to: use Authorization Manager (AzMan) with ASP.NET 2,0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="83885-112">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83885-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83885-113">See also</span></span>

- [<span data-ttu-id="83885-114">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="83885-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
