---
title: "Postupy: použití zprostředkovatele rolí Správce autorizací ASP.NET se službou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ee51a2fa4a4ec3de04e21fdbc070cd7619b43c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="d895b-102">Postupy: použití zprostředkovatele rolí Správce autorizací ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="d895b-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="d895b-103">Když [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hostuje webovou službu Správce autorizací můžete integrovat do aplikace umožňují ověření ke službě.</span><span class="sxs-lookup"><span data-stu-id="d895b-103">When [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="d895b-104">Správce autorizací umožňuje vývojář aplikací definovat jednotlivé operace, které je možné seskupit do formuláře úlohy.</span><span class="sxs-lookup"><span data-stu-id="d895b-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="d895b-105">Správce pak může autorizovat rolí k provedení konkrétní úlohy nebo jednotlivé operace.</span><span class="sxs-lookup"><span data-stu-id="d895b-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="d895b-106">Správce autorizací poskytuje nástroje pro správu jako modul snap-in konzoly Microsoft Management Console (MMC) ke správě rolí, úlohy, operace a uživatelů.</span><span class="sxs-lookup"><span data-stu-id="d895b-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="d895b-107">Správci nakonfigurovat úložiště zásad autorizace správce v souboru XML, služby Active Directory, nebo v úložišti režimu aplikace Active Directory (ADAM).</span><span class="sxs-lookup"><span data-stu-id="d895b-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="d895b-108">Správce autorizací je integrována do aplikace nakonfigurováním Správce autorizací [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace, který je hostitelem webové služby.</span><span class="sxs-lookup"><span data-stu-id="d895b-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider for the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is hosting the Web service.</span></span> <span data-ttu-id="d895b-109">Stejně jako jiné [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatelů rolí Správce autorizací [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí je konfigurován pomocí <`providers`> elementu.</span><span class="sxs-lookup"><span data-stu-id="d895b-109">Like other [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role providers, the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="d895b-110">Následující příklad kódu je část konfiguračního souboru pro webovou službu, která Správce autorizací je integraci do aplikace.</span><span class="sxs-lookup"><span data-stu-id="d895b-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d895b-111">integrace [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zprostředkovatele rolí s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, najdete v části [postup: použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="d895b-111"> integrating an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d895b-112">pomocí Správce autorizací s [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], najdete v části [postupy: použití Správce autorizací (AzMan) s prostředím ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=71303).</span><span class="sxs-lookup"><span data-stu-id="d895b-112"> using Authorization Manager with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=71303).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d895b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d895b-113">See Also</span></span>  
 [<span data-ttu-id="d895b-114">Postupy: Použití zprostředkovatele rolí ASP.NET se službou</span><span class="sxs-lookup"><span data-stu-id="d895b-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
