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
ms.openlocfilehash: 030841330ff37cddb0c9e3e466a55a4be098e784
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088789"
---
# <a name="web-settings-schema"></a><span data-ttu-id="86c4c-102">Schéma nastavení webu</span><span class="sxs-lookup"><span data-stu-id="86c4c-102">Web Settings Schema</span></span>
<span data-ttu-id="86c4c-103">Webové nastavení určuje nastavení ASP.NET procesoru a na úrovni spuštění, které se vztahuje na chování v rámci procesu spravované vrstvou hostování ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="86c4c-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="86c4c-104">Tato nastavení se liší od nastavení aplikačního typu domény, které jsou uvedeny v souboru Web. config aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="86c4c-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
<span data-ttu-id="86c4c-105">Nastavení webu jsou obsažena v souborech ASPNET. config, které jsou umístěny v instalačních složkách pro verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86c4c-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="86c4c-106">Například soubor ASPNET. config pro .NET Framework 2,0 je v následující složce:</span><span class="sxs-lookup"><span data-stu-id="86c4c-106">For example, the Aspnet.config file for .NET Framework 2.0 is in the following folder:</span></span>  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
<span data-ttu-id="86c4c-107">Webové nastavení se nepoužívá v žádné jiné konfigurační soubory, jako je například soubor Machine. config, kořenový soubor Web. config nebo Web. config na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="86c4c-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  

<span data-ttu-id="86c4c-108">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="86c4c-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="86c4c-109">&nbsp;&nbsp;[ **\<System. web >** ](system-web-element-web-settings.md)</span><span class="sxs-lookup"><span data-stu-id="86c4c-109">&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)</span></span>\
<span data-ttu-id="86c4c-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<applicationPool >** ](applicationpool-element-web-settings.md)</span><span class="sxs-lookup"><span data-stu-id="86c4c-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<applicationPool>**](applicationpool-element-web-settings.md)</span></span>

|<span data-ttu-id="86c4c-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="86c4c-111">Element</span></span>|<span data-ttu-id="86c4c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="86c4c-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86c4c-113">\<System. Web ></span><span class="sxs-lookup"><span data-stu-id="86c4c-113">\<system.web></span></span>](system-web-element-web-settings.md)|<span data-ttu-id="86c4c-114">Obsahuje informace, které používá vrstva hostování ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="86c4c-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="86c4c-115">\<applicationPool ></span><span class="sxs-lookup"><span data-stu-id="86c4c-115">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="86c4c-116">Určuje nastavení ASP.NET CPU a na úrovni spuštění, která se vztahují na chování v rámci procesu spravované vrstvou hostování ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="86c4c-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86c4c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86c4c-117">See also</span></span>

- [<span data-ttu-id="86c4c-118">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="86c4c-118">Configuration File Schema</span></span>](../index.md)
