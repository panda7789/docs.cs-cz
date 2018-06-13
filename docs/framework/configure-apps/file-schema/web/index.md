---
title: Schéma nastavení webu
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 93d0d2ea5cf3b0329d9b1a03a233cff2d8133072
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767476"
---
# <a name="web-settings-schema"></a><span data-ttu-id="8ed4d-102">Schéma nastavení webu</span><span class="sxs-lookup"><span data-stu-id="8ed4d-102">Web Settings Schema</span></span>
<span data-ttu-id="8ed4d-103">Nastavení webové zadejte procesoru a úroveň spuštění ASP.NET nastavení, které platí pro procesy chování spravované technologií ASP.NET, který je hostitelem vrstvy.</span><span class="sxs-lookup"><span data-stu-id="8ed4d-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="8ed4d-104">Tato nastavení se liší od nastavení typ domény aplikace, které jsou určené v souboru Web.config aplikace technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8ed4d-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="8ed4d-105">Nastavení webové jsou obsažené v Aspnet.config soubory, které jsou umístěny v instalačních složkách verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ed4d-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="8ed4d-106">Například soubor Aspnet.config pro [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] je v následující složce:</span><span class="sxs-lookup"><span data-stu-id="8ed4d-106">For example, the Aspnet.config file for [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="8ed4d-107">Nastavení webové nepoužívají v další konfigurační soubory například souboru machine.config, kořenový soubor Web.config nebo souborů Web.config úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="8ed4d-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="8ed4d-108">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="8ed4d-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="8ed4d-109">\<System.Web > elementu (webové nastavení)</span><span class="sxs-lookup"><span data-stu-id="8ed4d-109">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [<span data-ttu-id="8ed4d-110">\<applicationPool > – Element (webové nastavení)</span><span class="sxs-lookup"><span data-stu-id="8ed4d-110">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|<span data-ttu-id="8ed4d-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="8ed4d-111">Element</span></span>|<span data-ttu-id="8ed4d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8ed4d-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ed4d-113">\<system.web></span><span class="sxs-lookup"><span data-stu-id="8ed4d-113">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="8ed4d-114">Obsahuje informace, které používá ASP.NET hostování vrstvy.</span><span class="sxs-lookup"><span data-stu-id="8ed4d-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="8ed4d-115">\<ApplicationPool ></span><span class="sxs-lookup"><span data-stu-id="8ed4d-115">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="8ed4d-116">Určuje procesoru a nastavení ASP.NET úroveň spuštění, které platí pro procesy chování spravované technologií ASP.NET, který je hostitelem vrstvy.</span><span class="sxs-lookup"><span data-stu-id="8ed4d-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ed4d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ed4d-117">See Also</span></span>  
 [<span data-ttu-id="8ed4d-118">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="8ed4d-118">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
