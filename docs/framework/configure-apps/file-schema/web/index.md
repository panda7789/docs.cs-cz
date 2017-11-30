---
title: "Schéma nastavení webu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: efdfba94bd2d2a64b3434c97f30a035f210fda9a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="web-settings-schema"></a><span data-ttu-id="9b012-102">Schéma nastavení webu</span><span class="sxs-lookup"><span data-stu-id="9b012-102">Web Settings Schema</span></span>
<span data-ttu-id="9b012-103">Nastavení webové zadejte procesoru a úroveň spuštění ASP.NET nastavení, které platí pro procesy chování spravované technologií ASP.NET, který je hostitelem vrstvy.</span><span class="sxs-lookup"><span data-stu-id="9b012-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="9b012-104">Tato nastavení se liší od nastavení typ domény aplikace, které jsou určené v souboru Web.config aplikace technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9b012-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="9b012-105">Nastavení webové jsou obsažené v Aspnet.config soubory, které jsou umístěny v instalačních složkách verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b012-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="9b012-106">Například soubor Aspnet.config pro [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] je v následující složce:</span><span class="sxs-lookup"><span data-stu-id="9b012-106">For example, the Aspnet.config file for [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="9b012-107">Nastavení webové nepoužívají v další konfigurační soubory například souboru machine.config, kořenový soubor Web.config nebo souborů Web.config úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b012-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="9b012-108">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="9b012-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="9b012-109">\<System.Web > elementu (webové nastavení)</span><span class="sxs-lookup"><span data-stu-id="9b012-109">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [<span data-ttu-id="9b012-110">\<applicationPool > – Element (webové nastavení)</span><span class="sxs-lookup"><span data-stu-id="9b012-110">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|<span data-ttu-id="9b012-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="9b012-111">Element</span></span>|<span data-ttu-id="9b012-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9b012-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b012-113">\<System.Web ></span><span class="sxs-lookup"><span data-stu-id="9b012-113">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="9b012-114">Obsahuje informace, které používá ASP.NET hostování vrstvy.</span><span class="sxs-lookup"><span data-stu-id="9b012-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="9b012-115">\<applicationPool ></span><span class="sxs-lookup"><span data-stu-id="9b012-115">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="9b012-116">Určuje procesoru a nastavení ASP.NET úroveň spuštění, které platí pro procesy chování spravované technologií ASP.NET, který je hostitelem vrstvy.</span><span class="sxs-lookup"><span data-stu-id="9b012-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b012-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b012-117">See Also</span></span>  
 [<span data-ttu-id="9b012-118">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="9b012-118">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
