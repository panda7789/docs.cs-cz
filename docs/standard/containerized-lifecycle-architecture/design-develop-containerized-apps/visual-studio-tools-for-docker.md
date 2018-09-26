---
title: Visual Studio Tools for Docker ve Windows
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: cd140c12ef4a0187cce096e013937d5c98cd4b39
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170792"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>Pomocí sady Visual Studio Tools for Docker (Visual Studio na Windows)

Visual Studio Tools for Docker pracovní postup pro vývojáře je podobný používání Visual Studio Code a rozhraní příkazového řádku Dockeru (je založená na stejné rozhraní příkazového řádku Dockeru). Visual Studio Tools pro Docker díky ještě jednodušší, abyste mohli začít, zjednodušuje a poskytuje větší produktivitu pro sestavení, spouštět a vytvořte úkoly. Spustit a ladit své kontejnery prostřednictvím jednoduché akce, jako je **F5** a **Ctrl**+**F5**.

> [!NOTE]
> Tento článek se týká sady Visual Studio ve Windows a ne Visual Studio pro Mac.

## <a name="configure-your-local-environment"></a>Konfigurace vašeho místního prostředí

S nejnovější verzí Docker pro Windows ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), nastavení jednoduché usnadňuje vývoj aplikací Dockeru.

Podporu dockeru je zahrnuta v sadě Visual Studio 2017. Stáhnete Visual Studio 2017: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="use-docker-tools-in-visual-studio-2017"></a>Použití nástrojů Dockeru v sadě Visual Studio 2017

Existují dvě úrovně podpory Dockeru, které můžete přidat do projektu. V projektech webových aplikací .NET Core, lze přidat *soubor Dockerfile* soubor do projektu povolení podpory Dockeru. Další úrovní je podpora orchestrátoru kontejnerů, které přidává *soubor Dockerfile* do projektu (pokud ještě neexistuje) a *docker-compose.yml* souboru na úrovni řešení.

**Přidat** > **podporu Dockeru** a **přidat** > **podporu Orchestrátoru kontejnerů** jsou příkazy umístěné v místní nabídce (nebo kontextovou nabídku) uzel projektu pro projekt webové aplikace v **Průzkumníka řešení**, jak ukazuje obrázek 4 – 26:

![Přidejte podporu Dockeru nabídky v sadě Visual Studio](media/add-docker-support-menu.png)

Obrázek 4 – 26: Přidání podpory Dockeru do projektu sady Visual Studio 2017

### <a name="add-docker-support"></a>Přidání podpory Dockeru

Můžete přidat podporu Dockeru do existujícího projektu webové aplikace .NET Core tak, že vyberete **přidat** > **podporu Dockeru** v **Průzkumníka řešení**. Můžete také povolit podporu Dockeru během vytváření projektu tak, že vyberete **povolit podporu Dockeru** v **nová webová aplikace ASP.NET Core** dialogové okno, které se otevře po kliknutí na **OK** v **nový projekt** dialogové okno, jak ukazuje obrázek 4 – 27.

![Povolit podporu Dockeru pro novou webovou aplikaci ASP.NET Core v sadě Visual Studio](./media/enable-docker-support-visual-studio.png)

Obrázek 4 – 27: povolte podporu Dockeru během vytváření projektu v sadě Visual Studio 2017

Když přidáváte nebo povolit podporu Dockeru, sada Visual Studio přidá *soubor Dockerfile* soubor do projektu.

> [!NOTE]
> Když povolíte podporu Docker Compose během vytváření projektu pro projekt webové aplikace .NET Framework (nikoli projekt .NET Core webové aplikace), jak ukazuje obrázek 4 – 28, přidá se také podpora orchestrátoru kontejnerů.
>
> ![Povolit Docker compose podpory pro rozhraní .NET Framework projektu webové aplikace](media/enable-docker-compose-support.png)

> Obrázek 4 – 28: Povolení podpory Docker Compose v projektu webové aplikace .NET Framework v sadě Visual Studio 2017

### <a name="add-container-orchestrator-support"></a>Přidat podporu orchestrátoru kontejnerů

Pokud chcete vytvořit vícekontejnerových řešení, přidáte podporu orchestrátoru kontejnerů do vašich projektů. Když chcete přidat podporu orchestrátoru kontejnerů, Visual Studio přidá *soubor Dockerfile* projektu (pokud ještě neexistuje) a globální *docker-compose.yml* souboru na úrovni řešení. To vám umožní spouštět a ladit skupinu kontejnerů (celé řešení) ve stejnou dobu, pokud jsou definovány ve stejném *docker-compose.yml* souboru. Pokud *docker-compose.yml* již existuje, požadovaných řádků kódu, konfigurace sady Visual Studio právě přidá k němu.

Poté, co přidáte do projektu podporu Orchestrace kontejnerů, se zobrazí soubor Dockerfile přidat do projektu a **docker-compose** přidán do řešení ve složce **Průzkumníka řešení**, jak ukazuje obrázek 4 – 29:

![Soubory docker v Průzkumníku řešení v sadě Visual Studio](media/docker-support-solution-explorer.png)

Obrázek 4 – 29: Docker soubory v Průzkumníku řešení v sadě Visual Studio 2017

**Další informace:** další podrobnosti o implementaci služby a použití sady Visual Studio Tools for Docker v následujících článcích:

Vytváření, ladění, aktualizovat a aktualizovat aplikace v místním kontejneru Dockeru: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Nasazení kontejneru ASP.NET Core Dockeru do registru kontejneru: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

>[!div class="step-by-step"]
[Předchozí](docker-apps-inner-loop-workflow.md)
[další](set-up-windows-containers-with-powershell.md)