---
title: Pomocí nástrojů Visual Studio pro Docker (Visual Studio v systému Windows)
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cbd4dea32b98e79e85302aa5d4a5c97b1b0fa556
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>Pomocí nástrojů Visual Studio pro Docker (Visual Studio v systému Windows)

Při použití nástroje sady Visual Studio pro Docker je pracovní postup podobně jako při použití Visual Studio Code a příkazového řádku Dockeru vývojáře pracovního postupu (ve skutečnosti pracuje na stejné příkazového řádku Dockeru), ale je snazší začít pracovat, zjednodušuje proces a poskytuje větší produktivitu pro sestavení, spustit a vytvořit úlohy. Je také možné ke spouštění a ladění kontejnerů prostřednictvím jednoduchého akce, jako je F5 a Ctrl + F5 ze sady Visual Studio. I další s Visual Studio 2017, kromě toho lze spustit a ladění jediný kontejner, můžete také spustit a ladění skupinu kontejnery (celé řešení) ve stejnou dobu, pokud jsou definovány v stejný soubor docker-compose.yml na úrovni řešení.

## <a name="configuring-your-local-environment"></a>Konfigurace místního prostředí

Nejnovější verze Docker pro systém Windows je jednodušší než někdy k vývoji aplikací Docker vzhledem k tomu, že instalační program je jasné, jak je popsáno v následující odkazy.

**Další informace:** Další informace o instalaci Docker pro systém Windows, přejděte na <https://docs.docker.com/docker-for-windows/>.

Pokud používáte Visual Studio 2015, musíte mít Update 3 nebo novější verze a sady Visual Studio Tools for Docker.

**Další informace:** pokyny k instalaci sady Visual Studio, přejděte na [ https://www.visualstudio.com/\ produkty/vs-2015produktu edice](https://www.visualstudio.com/products/vs-2015-product-editions).

Chcete-li zobrazit další informace o instalaci Visual Studio Tools for Docker, přejděte na <http://aka.ms/vstoolsfordocker> a <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.

Pokud používáte Visual Studio 2017, je už součástí sady Docker podpory.

## <a name="using-docker-tools-in-visual-studio-2015"></a>Pomocí nástroje Docker v sadě Visual Studio 2015

Visual Studio Tools for Docker zajišťuje konzistentní způsob pro vývoj a ověření místně kontejnerů Docker pro Linux v rámci Linux Docker hostitele nebo virtuálního počítače nebo kontejnerů Windows přímo v systému Windows.

Pokud používáte jediný kontejner, je první věcí, které potřebujete k zahájení zapnout podporu Docker do projektu .NET Core. K tomu, klikněte pravým tlačítkem na soubor projektu, jak ukazuje obrázek 4 – 25.

![https://i1.visualstudiogallery.msdn.s-msft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4/image/file/205468/1/add-docker-support.png](./media/image31.png)

Obrázek 4 – 25: zapnutí Docker podporu pro svůj projekt sady Visual Studio

## <a name="using-docker-tools-in-visual-studio-2017"></a>Pomocí nástroje Docker v Visual Studio 2017

Když přidáte podporu Docker do projektu služby ve vašem řešení (viz obrázek 4-26) a Visual Studio není soubor soubor Docker jen přidat do projektu, ho také je přidání oddílu služby vaše řešení docker-compose.yml soubory (nebo vytváření souborů, pokud jejich nebyla existují). Je snadný způsob, jak začít sestavování řešení multicontainer; pak můžete otevřít soubory docker-compose.yml a provede jejich aktualizaci s další funkce.

![](./media/image32.png)

Obrázek 4-26: zapnutí podpory Docker řešení v projektu Visual Studio 2017

Tato akce přidá do projektu není jenom soubor Docker, přidá také požadovanou konfiguraci řádky kódu do globální docker-compose.yml nastavit na úrovni řešení.

Také můžete zapnout podporu Docker při vytváření projektu ASP.NET Core v Visual Studio 2017, jak ukazuje obrázek 4-27.

![](./media/image33.png)

Obrázek 4-27: zapnutí podpory Docker při vytváření projektu

Po přidání podpory Docker do řešení v sadě Visual Studio, taky uvidíte novou větev uzlu v Průzkumníku řešení se soubory přidané docker-compose.yml znázorněný v obrázek 4-28.

![](./media/image34.PNG)

Obrázek 4-28: docker-compose.yml soubory nyní zobrazit v Průzkumníku řešení

Můžete nasadit multicontainer aplikace pomocí jednoho docker-compose.yml souboru při spuštění docker tvoří; však sady Visual Studio přidá skupinu z nich, takže můžete přepsat hodnoty v závislosti na prostředí (vývoj a produkční) a provádění typu (vydání a ladění). Tato funkce bude lépe popsané v dalších kapitolách.

**Další informace:** další podrobnosti o implementaci služby a použití nástroje sady Visual Studio pro Docker přečíst v následujících článcích:

Vytvoření, ladění, aktualizace a aktualizace aplikace v místním kontejner Docker: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Nasaďte kontejner ASP.NET se vzdáleným hostitelem Docker: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)


>[!div class="step-by-step"]
[Předchozí] (docker aplikace vnitřní smyčky workflow.md) [Další] (set-up-windows-containers-with-powershell.md)
