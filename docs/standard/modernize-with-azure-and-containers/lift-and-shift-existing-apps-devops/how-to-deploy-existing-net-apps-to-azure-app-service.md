---
title: "Postup nasazení existující aplikace .NET do služby Azure App Service"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Postup nasazení existující aplikace .NET do služby Azure App Service"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aefcd79574cbbf6b3759bfa6cc0f9e46a58244ce
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-deploy-existing-net-apps-to-azure-app-service"></a><span data-ttu-id="56cad-103">Postup nasazení existující aplikace .NET do služby Azure App Service</span><span class="sxs-lookup"><span data-stu-id="56cad-103">How to deploy existing .NET apps to Azure App Service</span></span> 

<span data-ttu-id="56cad-104">Funkce Web Apps služby Azure App Service je plně spravovaná výpočetní platforma, která je optimalizována pro hostování webů a webových aplikací.</span><span class="sxs-lookup"><span data-stu-id="56cad-104">The Web Apps feature of Azure App Service is a fully managed compute platform that is optimized for hosting websites and web apps.</span></span> <span data-ttu-id="56cad-105">Tato nabídka PaaS v Microsoft Azure umožňuje můžete soustředit na obchodní logiku, zatímco Azure zajistí infrastrukturu pro spouštění a škálování aplikací.</span><span class="sxs-lookup"><span data-stu-id="56cad-105">This PaaS offering in Microsoft Azure lets you focus on your business logic, while Azure takes care of the infrastructure to run and scale your apps.</span></span>

## <a name="validate-sites-and-migrate-to-app-service-with-azure-app-service-migration-assistant"></a><span data-ttu-id="56cad-106">Ověření lokalit a migrovat do App Service pomocí pomocníka Azure App Service migrace</span><span class="sxs-lookup"><span data-stu-id="56cad-106">Validate sites and migrate to App Service with Azure App Service Migration Assistant</span></span>

<span data-ttu-id="56cad-107">Když vytvoříte novou aplikaci v sadě Visual Studio, obvykle přesunutí aplikace do služby App Service je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="56cad-107">When you create a new application in Visual Studio, moving the app to App Service usually is straightforward.</span></span> <span data-ttu-id="56cad-108">Ale pokud máte v úmyslu migrovat existující aplikaci do služby App Service, nejprve potřebujete k vyhodnocení, zda všechny aplikace závislosti jsou kompatibilní s App Service.</span><span class="sxs-lookup"><span data-stu-id="56cad-108">However, if you are planning to migrate an existing application to App Service, first you need to evaluate whether all your application's dependencies are compatible with App Service.</span></span> <span data-ttu-id="56cad-109">To zahrnuje závislosti, jako je server operačního systému a veškerý software třetích stran, který je nainstalován na serveru.</span><span class="sxs-lookup"><span data-stu-id="56cad-109">This includes dependencies like server OS and any third-party software that's installed on the server.</span></span>

<span data-ttu-id="56cad-110">Můžete použít [Azure App Service migrace pomocníka](https://www.migratetoazure.net/) k analýze webů a je migraci ze systému Windows a Linux webové servery do služby App Service.</span><span class="sxs-lookup"><span data-stu-id="56cad-110">You can use [Azure App Service Migration Assistant](https://www.migratetoazure.net/) to analyze sites and then migrate them from Windows and Linux web servers to App Service.</span></span> <span data-ttu-id="56cad-111">Jako součást migrace nástroj vytvoří webové aplikace a databáze v Azure, podle potřeby publikuje obsah a publikuje vaše databáze.</span><span class="sxs-lookup"><span data-stu-id="56cad-111">As part of the migration, the tool creates web apps and databases on Azure as needed, publishes content, and publishes your database.</span></span>

<span data-ttu-id="56cad-112">Azure App Service migrace pomocníka podporuje migraci z IIS a běžící v systému Windows Server do cloudu.</span><span class="sxs-lookup"><span data-stu-id="56cad-112">Azure App Service Migration Assistant supports migrating from IIS running on Windows Server to the cloud.</span></span> <span data-ttu-id="56cad-113">App Service podporuje Windows Server 2003 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="56cad-113">App Service supports Windows Server 2003 and later versions.</span></span>

> ![https://www.migratetoazure.net/Images/ImageCanvas.png](./media/image5.png)
>
> <span data-ttu-id="56cad-115">**Obrázek 4 – 5.**</span><span class="sxs-lookup"><span data-stu-id="56cad-115">**Figure 4-5.**</span></span> <span data-ttu-id="56cad-116">Asistent migrace systému služby Azure App Service pomocí</span><span class="sxs-lookup"><span data-stu-id="56cad-116">Using Azure App Service Migration Assistant</span></span>

<span data-ttu-id="56cad-117">Aplikace služby migrace pomocníka je nástroj, který své weby se přesouvají z webových serverů do cloudu Azure.</span><span class="sxs-lookup"><span data-stu-id="56cad-117">App Service Migration Assistant is a tool that moves your websites from your web servers to the Azure cloud.</span></span>

<span data-ttu-id="56cad-118">Po migraci webu do služby App Service, v této lokalitě je vše, co je nutné ho spustit bezpečně a efektivně.</span><span class="sxs-lookup"><span data-stu-id="56cad-118">After a website is migrated to App Service, the site has everything it needs to run safely and efficiently.</span></span> <span data-ttu-id="56cad-119">Lokality jsou nastavení a spustit automaticky ve službě Azure cloud PaaS (aplikační služby).</span><span class="sxs-lookup"><span data-stu-id="56cad-119">Sites are set up and run automatically in the Azure cloud PaaS service (App Service).</span></span>

<span data-ttu-id="56cad-120">Nástroj pro migraci služby App Service můžete své weby analýza a tvorba sestav o jejich kompatibilitě pro přesun do služby App Service.</span><span class="sxs-lookup"><span data-stu-id="56cad-120">The App Service migration tool can analyze your websites and report on their compatibility for moving to App Service.</span></span> <span data-ttu-id="56cad-121">Pokud budete spokojeni s analýzy, můžete je nechat aplikaci služby migrace pomocníka migraci obsahu, data a nastavení za vás.</span><span class="sxs-lookup"><span data-stu-id="56cad-121">If you're happy with the analysis, you can let App Service Migration Assistant migrate content, data, and settings for you.</span></span> <span data-ttu-id="56cad-122">Pokud lokalitu není poměrně kompatibilní, nástroj pro migraci řekne, co je potřeba upravit ke spolupráci.</span><span class="sxs-lookup"><span data-stu-id="56cad-122">If a site is not quite compatible, the migration tool tells you what you need to adjust to make it work.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="56cad-123">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="56cad-123">Additional resources</span></span>

- <span data-ttu-id="56cad-124">**Asistent migrace systému služby Azure App Service**</span><span class="sxs-lookup"><span data-stu-id="56cad-124">**Azure App Service Migration Assistant**</span></span>

    [<span data-ttu-id="56cad-125">https://www.migratetoazure.net/</span><span class="sxs-lookup"><span data-stu-id="56cad-125">https://www.migratetoazure.net/</span></span>](https://www.migratetoazure.net/)

>[!div class="step-by-step"]
<span data-ttu-id="56cad-126">[Předchozí](what-about-cloud-optimized-applications.md)
[další](deploy-existing-net-apps-as-windows-containers.md)</span><span class="sxs-lookup"><span data-stu-id="56cad-126">[Previous](what-about-cloud-optimized-applications.md)
[Next](deploy-existing-net-apps-as-windows-containers.md)</span></span>
