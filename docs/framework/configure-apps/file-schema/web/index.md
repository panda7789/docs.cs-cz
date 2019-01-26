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
ms.openlocfilehash: 4bde008661e78fc85c428fa5100f81483936b460
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083597"
---
# <a name="web-settings-schema"></a><span data-ttu-id="266b8-102">Schéma nastavení webu</span><span class="sxs-lookup"><span data-stu-id="266b8-102">Web Settings Schema</span></span>
<span data-ttu-id="266b8-103">Nastavení webu zadejte procesoru a úroveň spuštění ASP.NET nastavení platná pro celého procesu chování spravuje hostování vrstvy technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="266b8-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="266b8-104">Tato nastavení se liší od nastavení typ domény aplikace, která jsou uvedeny v souboru Web.config aplikace technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="266b8-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="266b8-105">Nastavení webu jsou obsaženy v souborech Aspnet.config, které jsou umístěné ve složce instalace pro verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="266b8-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="266b8-106">Například soubor Aspnet.config pro [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] je v následující složce:</span><span class="sxs-lookup"><span data-stu-id="266b8-106">For example, the Aspnet.config file for [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="266b8-107">Webové nastavení nepoužívají v žádné další konfigurační soubory, například souboru machine.config, kořenový soubor Web.config nebo souborech Web.config na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="266b8-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="266b8-108">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="266b8-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="266b8-109">\<System.Web > – Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="266b8-109">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [<span data-ttu-id="266b8-110">\<applicationPool > – Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="266b8-110">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|<span data-ttu-id="266b8-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="266b8-111">Element</span></span>|<span data-ttu-id="266b8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="266b8-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="266b8-113">\<system.web></span><span class="sxs-lookup"><span data-stu-id="266b8-113">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="266b8-114">Obsahuje informace, které používá vrstvy hostování technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="266b8-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="266b8-115">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="266b8-115">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="266b8-116">Určuje procesoru a úroveň spuštění ASP.NET nastavení platná pro celého procesu chování spravuje hostování vrstvy technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="266b8-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="266b8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="266b8-117">See also</span></span>
- [<span data-ttu-id="266b8-118">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="266b8-118">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
