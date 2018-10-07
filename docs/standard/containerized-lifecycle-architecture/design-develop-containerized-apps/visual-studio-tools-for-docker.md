---
title: Visual Studio Tools for Docker ve Windows
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: faae4b3e3ef96d1d8dd73b7ac313b0a5deffec34
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838231"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>Pomocí sady Visual Studio Tools for Docker (Visual Studio na Windows)

Visual Studio Tools for Docker pracovní postup vývoje je pracovní postup podobně jako při použití Visual Studio Code a rozhraní příkazového řádku Dockeru. Ve skutečnosti je založen na stejné rozhraní příkazového řádku Dockeru, ale je snadné začít, zjednodušuje a poskytuje větší produktivitu pro sestavení, spouštět a vytvořit úkolů. Spustit a ladit své kontejnery prostřednictvím jednoduché akce, jako je **F5** a **Ctrl**+**F5**. Díky podpoře Orchestrace volitelný kontejner, kromě možnosti spuštění a ladění jednoho kontejneru můžete spustit a ladit skupinu kontejnerů (celé řešení) ve stejnou dobu.

> [!NOTE]
> Tento článek se týká sady Visual Studio ve Windows a ne Visual Studio pro Mac.

## <a name="configure-your-local-environment"></a>Konfigurace vašeho místního prostředí

S nejnovější verzí Docker pro Windows ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), nastavení jednoduché usnadňuje vývoj aplikací Dockeru.

Podporu dockeru je zahrnuta v sadě Visual Studio 2017. Stáhnete Visual Studio 2017: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="use-docker-tools-in-visual-studio-2017"></a>Použití nástrojů Dockeru v sadě Visual Studio 2017

Existují dvě úrovně podpory Dockeru, které můžete přidat do projektu. V projektech webových aplikací .NET Core, lze přidat *soubor Dockerfile* soubor do projektu povolení podpory Dockeru. Další úrovní je podpora Orchestrace kontejnerů, které přidává *soubor Dockerfile* do projektu (pokud ještě neexistuje) a *docker-compose.yml* souboru na úrovni řešení. Podpora Orchestrace kontejnerů pomocí Docker Compose, se přidá ve výchozím nastavení v sadě Visual Studio 2017 verze 15.7 nebo starší. Podpora Orchestrace kontejnerů je přihlašovaná funkce v sadě Visual Studio 2017 verze 15.8 nebo později, v takovém případě Docker Compose a Service Fabric se nepodporuje.

**Přidat** > **podporu Dockeru** a **přidat** > **Orchestrace kontejnerů podporu** jsou příkazy umístěné v místní nabídce (nebo kontextovou nabídku) uzel projektu pro projekt webové aplikace v **Průzkumníka řešení**, jak ukazuje obrázek 4 – 26:

![Přidejte podporu Dockeru nabídky v sadě Visual Studio](media/add-docker-support-menu.png)

Obrázek 4 – 26: Přidání podpory Dockeru do projektu sady Visual Studio 2017

### <a name="add-docker-support"></a>Přidání podpory Dockeru

Můžete přidat podporu Dockeru do existujícího projektu webové aplikace .NET Core tak, že vyberete **přidat** > **podporu Dockeru** v **Průzkumníka řešení**. Můžete také povolit podporu Dockeru během vytváření projektu tak, že vyberete **povolit podporu Dockeru** v **nová webová aplikace ASP.NET Core** dialogové okno, které se otevře po kliknutí na **OK** v **nový projekt** dialogové okno, jak ukazuje obrázek 4 – 27.

![Povolit podporu Dockeru pro novou webovou aplikaci ASP.NET Core v sadě Visual Studio](./media/enable-docker-support-visual-studio.png)

Obrázek 4 – 27: povolte podporu Dockeru během vytváření projektu v sadě Visual Studio 2017

Když přidáváte nebo povolit podporu Dockeru, sada Visual Studio přidá *soubor Dockerfile* soubor do projektu.

> [!NOTE]
> Když povolíte podporu Docker Compose během vytváření projektu pro projekt webové aplikace .NET Framework (nikoli projekt .NET Core webové aplikace), jak ukazuje obrázek 4 – 28, přidá se také podpora Orchestrace kontejnerů.
>
> ![Povolit Docker compose podpory pro rozhraní .NET Framework projektu webové aplikace](media/enable-docker-compose-support.png)

> Obrázek 4 – 28: Povolení podpory Docker Compose v projektu webové aplikace .NET Framework v sadě Visual Studio 2017

### <a name="add-container-orchestration-support"></a>Přidat podporu Orchestrace kontejnerů

Pokud chcete vytvořit vícekontejnerových řešení, přidáte do vašich projektů podpora Orchestrace kontejnerů. To vám umožní spouštět a ladit skupinu kontejnerů (celé řešení) ve stejnou dobu, pokud jsou definovány ve stejném *docker-compose.yml* souboru.

Chcete-li přidat podporu Orchestrace kontejnerů, klikněte pravým tlačítkem na uzel řešení nebo projektu v **Průzkumníka řešení**a zvolte **přidat** > **kontejner Orchestrace podporovat**. Klikněte na tlačítko **Docker Compose** nebo **Service Fabric** Spravovat kontejnery.

Poté, co přidáte do projektu podporu Orchestrace kontejnerů, se zobrazí soubor Dockerfile přidat do projektu a **docker-compose** přidán do řešení ve složce **Průzkumníka řešení**, jak ukazuje obrázek 4 – 29:

![Soubory docker v Průzkumníku řešení v sadě Visual Studio](media/docker-support-solution-explorer.png)

Obrázek 4 – 29: Docker soubory v Průzkumníku řešení v sadě Visual Studio 2017

Pokud *docker-compose.yml* již existuje, požadovaných řádků kódu, konfigurace sady Visual Studio právě přidá k němu.

## <a name="configure-docker-tools"></a>Konfigurace nástroje Dockeru

V hlavní nabídce zvolte **nástroje** > **možnosti**a rozbalte **kontejnerových nástrojů** > **nastavení**. Nastavení nástroje kontejneru se zobrazí.

![](./media/visual-studio-docker-tools-options.png)

Obrázek 4-30: Možnosti nástrojů Dockeru

V následující tabulce může pomoct při rozhodování, jak nastavit tyto možnosti.

| Název | Výchozí nastavení | Popis |
| -----|:---------------:| ----------- |
| Automaticky získat požadované Image Dockeru při načtení projektu | On | Pro zvýšení výkonu, při načítání projektů Visual Studio spustí operaci Docker pull na pozadí tak, že až budete připravení ke spuštění kódu, se image nestáhne již nebo probíhá stahování. Pokud jste právě načítá projekty a procházení kódu, můžete to vypnout aby se zabránilo stahování imagí kontejnerů, které nepotřebujete. |
| Automaticky spustit kontejnery na pozadí | On | Znovu pro zajištění zvýšeného výkonu sady Visual Studio vytvoří kontejner s připojí svazek připravené pro když sestavíte a spustíte svůj kontejner. Pokud chcete řídit, kdy se vytvoří kontejner, vypněte toto. |
| Automaticky ukončit kontejnery na řešení zavřít | On | Pokud byste o ni kontejnerů pro vaše řešení, aby kontinuálně běžely po zavření řešení nebo zavření sady Visual Studio, vypnutí této funkce. |
| Nezobrazovat výzvu důvěřující certifikátu SSL pro localhost | Off | Visual Studio nadále výzvu pro nové projekty i po certifikát SSL byl důvěryhodný pro starší projektu. Můžete nastavit toto políčko, aby předejít výzvu, při otevření jiné projekty. |

**Další informace:** další podrobnosti o implementaci služby a použití sady Visual Studio Tools for Docker v následujících článcích:

Vytváření, ladění, aktualizovat a aktualizovat aplikace v místním kontejneru Dockeru: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Nasazení kontejneru ASP.NET Core Dockeru do registru kontejneru: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

>[!div class="step-by-step"]
[Předchozí](docker-apps-inner-loop-workflow.md)
[další](set-up-windows-containers-with-powershell.md)