---
title: "Postup nasazení existující aplikace .NET do služby Azure App Service"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Postup nasazení existující aplikace .NET do služby Azure App Service"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: c83703c6f3dede0f92263e0d46bf48525c3eefaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-deploy-existing-net-apps-to-azure-app-service"></a>Postup nasazení existující aplikace .NET do služby Azure App Service 

Funkce Web Apps služby Azure App Service je plně spravovaná výpočetní platforma, která je optimalizována pro hostování webů a webových aplikací. Tato nabídka PaaS v Microsoft Azure umožňuje můžete soustředit na obchodní logiku, zatímco Azure zajistí infrastrukturu pro spouštění a škálování aplikací.

## <a name="validate-sites-and-migrate-to-app-service-with-azure-app-service-migration-assistant"></a>Ověření lokalit a migrovat do App Service pomocí pomocníka Azure App Service migrace

Když vytvoříte novou aplikaci v sadě Visual Studio, obvykle přesunutí aplikace do služby App Service je jednoduchá. Ale pokud máte v úmyslu migrovat existující aplikaci do služby App Service, nejprve potřebujete k vyhodnocení, zda všechny aplikace závislosti jsou kompatibilní s App Service. To zahrnuje závislosti, jako je server operačního systému a veškerý software třetích stran, který je nainstalován na serveru.

Můžete použít [Azure App Service migrace pomocníka](https://www.migratetoazure.net/) k analýze webů a je migraci ze systému Windows a Linux webové servery do služby App Service. Jako součást migrace nástroj vytvoří webové aplikace a databáze v Azure, podle potřeby publikuje obsah a publikuje vaše databáze.

Azure App Service migrace pomocníka podporuje migraci z IIS a běžící v systému Windows Server do cloudu. App Service podporuje Windows Server 2003 a novějších verzích.

> ![https://www.migratetoazure.NET/Images/ImageCanvas.PNG](./media/image5.png)
>
> **Obrázek 4 – 5.** Asistent migrace systému služby Azure App Service pomocí

Aplikace služby migrace pomocníka je nástroj, který své weby se přesouvají z webových serverů do cloudu Azure.

Po migraci webu do služby App Service, v této lokalitě je vše, co je nutné ho spustit bezpečně a efektivně. Lokality jsou nastavení a spustit automaticky ve službě Azure cloud PaaS (aplikační služby).

Nástroj pro migraci služby App Service můžete své weby analýza a tvorba sestav o jejich kompatibilitě pro přesun do služby App Service. Pokud budete spokojeni s analýzy, můžete je nechat aplikaci služby migrace pomocníka migraci obsahu, data a nastavení za vás. Pokud lokalitu není poměrně kompatibilní, nástroj pro migraci řekne, co je potřeba upravit ke spolupráci.

### <a name="additional-resources"></a>Další zdroje

-   **Asistent migrace systému služby Azure App Service**

    [https://www.migratetoazure.NET/](https://www.migratetoazure.net/)

>[!div class="step-by-step"]
[Předchozí](what-about-cloud-optimized-applications.md)
[další](deploy-existing-net-apps-as-windows-containers.md)
