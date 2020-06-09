---
title: 'Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 7c1076671512b33f115950cad684fba0b514abe9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595333"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="8cf41-102">Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="8cf41-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="8cf41-103">Pokud ASP.NET hostuje webovou službu, můžete do aplikace integrovat Správce autorizací a poskytnout službě autorizaci.</span><span class="sxs-lookup"><span data-stu-id="8cf41-103">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="8cf41-104">Správce autorizací umožňuje vývojářům aplikací definovat jednotlivé operace, které mohou být seskupeny do úloh formuláře.</span><span class="sxs-lookup"><span data-stu-id="8cf41-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="8cf41-105">Správce pak může autorizovat role k provádění konkrétních úkolů nebo jednotlivých operací.</span><span class="sxs-lookup"><span data-stu-id="8cf41-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="8cf41-106">Správce autorizací poskytuje nástroj pro správu jako modul snap-in konzoly MMC (Microsoft Management Console) ke správě rolí, úloh, operací a uživatelů.</span><span class="sxs-lookup"><span data-stu-id="8cf41-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="8cf41-107">Správci konfigurují úložiště zásad Správce autorizací v souboru XML, ve službě Active Directory nebo v úložišti ADAM (Active Directory Application Mode).</span><span class="sxs-lookup"><span data-stu-id="8cf41-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="8cf41-108">Správce autorizací je do aplikace integrován konfigurací zprostředkovatele rolí ASP.NET Správce autorizací pro aplikaci ASP.NET, která je hostitelem webové služby.</span><span class="sxs-lookup"><span data-stu-id="8cf41-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="8cf41-109">Stejně jako jiní poskytovatelé rolí ASP.NET je zprostředkovatel rolí ASP.NET Správce autorizací nakonfigurovaný pomocí `providers` elementu <>.</span><span class="sxs-lookup"><span data-stu-id="8cf41-109">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="8cf41-110">Následující příklad kódu je část konfiguračního souboru pro webovou službu, která integruje Správce autorizací do aplikace.</span><span class="sxs-lookup"><span data-stu-id="8cf41-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
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
  
 <span data-ttu-id="8cf41-111">Další informace o integraci zprostředkovatele rolí ASP.NET s aplikací WCF najdete v tématu [How to: use the ASP.NET provider role with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="8cf41-111">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="8cf41-112">Další informace o používání Správce autorizací s ASP.NET najdete v tématu [How to: use Authorization Manager (AzMan) with ASP.NET 2,0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="8cf41-112">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cf41-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="8cf41-113">See also</span></span>

- [<span data-ttu-id="8cf41-114">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="8cf41-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
