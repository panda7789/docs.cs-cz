---
title: Visual Studio Tools for Docker ve Windows
description: Seznámení s nástroji Dockeru k dispozici v sadě Visual Studio 2017 verze 15.7 nebo novější.
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 2b6fdc33f9cf850cf9e52fca4a1a9754cd412567
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644661"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>Použití nástrojů Dockeru v sadě Visual Studio 2017 na Windows

Pracovní postup pro vývojáře při používání nástroje Dockeru, které jsou zahrnuty v sadě Visual Studio 2017 verze 15.7 nebo novější, je podobný používání Visual Studio Code a rozhraní příkazového řádku Dockeru (ve skutečnosti vychází stejné rozhraní příkazového řádku Dockeru), ale je snadné začít, zjednodušuje proces, a poskytuje větší produktivitu pro sestavení, spouštět a vytvořit úkolů. Můžete také spustit a ladit své kontejnery pomocí obvyklého `F5` a `Ctrl+F5` klíče ze sady Visual Studio. Můžete dokonce i ladění celé řešení, pokud jeho kontejnery jsou definovány ve stejném `docker-compose.yml` souboru na úrovni řešení.

## <a name="configure-your-local-environment"></a>Konfigurace vašeho místního prostředí

S nejnovější verzí Docker pro Windows je jednodušší než někdy k vývoji aplikací Dockeru vzhledem k tomu, že instalační program je jasné, jak je vysvětleno v následující odkazy.

> [!TIP]
> Další informace o instalaci Dockeru pro Windows, přejděte na (<https://docs.docker.com/docker-for-windows/>).

## <a name="docker-support-in-visual-studio-2017"></a>Podpora dockeru v sadě Visual Studio 2017

Existují dvě úrovně podpory Dockeru, které můžete přidat do projektu. V projektech ASP.NET Core, lze přidat `Dockerfile` soubor do projektu povolení podpory Dockeru. Další úrovní je podpora Orchestrace kontejnerů, které přidává `Dockerfile` do projektu (pokud ještě neexistuje) a `docker-compose.yml` souboru na úrovni řešení. Podpora Orchestrace kontejnerů pomocí Docker Compose, se přidá ve výchozím nastavení v sadě Visual Studio 2017 verze 15.0: 15.7. Podpora Orchestrace kontejnerů je přihlašovaná funkce v sadě Visual Studio 2017 verze 15,8 nebo novější. Na novější verzi 15.8 podporu Docker Compose a Service Fabric.

**Přidat > Podpora Dockeru** a **Přidat > Podpora Orchestrátoru kontejnerů** příkazy jsou umístěné v místní nabídce (nebo kontextovou nabídku) uzel projektu pro projekt ASP.NET Core v  **Průzkumník řešení**, jak ukazuje obrázek 4-31:

![Přidejte podporu Dockeru nabídky v sadě Visual Studio](./media/add-docker-support-menu.png)

**Obrázek 4-31**. Přidání podpory Dockeru do projektu sady Visual Studio 2017

### <a name="add-docker-support"></a>Přidání podpory Dockeru

Můžete přidat podporu Dockeru do existujícího projektu ASP.NET Core tak, že vyberete **přidat** > **podporu Dockeru** v **Průzkumníka řešení**. Můžete také povolit podporu Dockeru během vytváření projektu tak, že vyberete **povolit podporu Dockeru** v **nová webová aplikace ASP.NET Core** dialogové okno, které se otevře po kliknutí na **OK** v **nový projekt** dialogové okno, jak ukazuje obrázek 4-32.

![Povolit podporu Dockeru pro novou webovou aplikaci ASP.NET Core v sadě Visual Studio](./media/enable-docker-support-visual-studio.png)

**Obrázek 4 – 32**. Povolit podporu Dockeru během vytváření projektu v sadě Visual Studio 2017

Když přidáváte nebo povolit podporu Dockeru, sada Visual Studio přidá *soubor Dockerfile* soubor do projektu.

> [!NOTE]
> Když povolíte podporu Docker Compose během vytváření projektu pro projekt ASP.NET (.NET Framework, ne k projektu .NET Core), jak ukazuje obrázek 4-33, přidá se také podpora Orchestrace kontejnerů.

![Povolit Docker compose podporu pro technologie ASP.NET](media/enable-docker-compose-support.png)

**Obrázek 4-33**. Povolení podpory Docker Compose pro projektu ASP.NET v sadě Visual Studio 2017

### <a name="add-container-orchestration-support"></a>Přidat podporu Orchestrace kontejnerů

Pokud chcete vytvořit řešení více kontejnerů, přidáte do vašich projektů podpora Orchestrace kontejnerů. To vám umožní spouštět a ladit skupinu kontejnerů (celé řešení) ve stejnou dobu, pokud jsou definovány ve stejném *docker-compose.yml* souboru.

Chcete-li přidat podporu Orchestrace kontejnerů, klikněte pravým tlačítkem na uzel řešení nebo projektu v **Průzkumníku řešení**a zvolte **Přidat > Podpora Orchestrace kontejnerů**. Klikněte na tlačítko **Docker Compose** nebo **Service Fabric** Spravovat kontejnery.

Poté, co přidáte do projektu podporu Orchestrace kontejnerů, se zobrazí soubor Dockerfile přidat do projektu a **docker-compose** přidán do řešení ve složce **Průzkumníka řešení**, jak ukazuje obrázek 4 – 34:

![Soubory docker v Průzkumníku řešení v sadě Visual Studio](media/docker-support-solution-explorer.png)

**Obrázek 4 – 34**. Soubory docker v Průzkumníku řešení v sadě Visual Studio 2017

Pokud *docker-compose.yml* již existuje, požadovaných řádků kódu, konfigurace sady Visual Studio právě přidá k němu.

## <a name="configure-docker-tools"></a>Konfigurace nástroje Dockeru

V hlavní nabídce zvolte **nástroje > Možnosti**a rozbalte **nástroje kontejneru sady > Nastavení**. Nastavení nástroje kontejneru se zobrazí.

![Visual Studio Docker tools možnosti zobrazení: Automaticky získat požadované Image Dockeru při načtení projektu, automaticky spustit kontejnery na pozadí, automaticky ukončit kontejnery v řešení zavřít a nechcete zobrazovat výzvu pro důvěřující certifikát SSL.](./media/visual-studio-docker-tools-options.png)

**Obrázek 4 – 35**. Možnosti nástrojů dockeru

V následující tabulce může pomoct při rozhodování, jak nastavit tyto možnosti.

| Name | Výchozí nastavení | Platí pro | Popis |
| -----|:---------------:|:----------:| ----------- |
| Automaticky získat požadované Image Dockeru při načtení projektu | On | Docker Compose | Pro zvýšení výkonu při načítání projektů sady Visual Studio spustí operaci Docker pull na pozadí tak, že až budete připraveni ke spuštění kódu, se image nestáhne již nebo probíhá stahování. Pokud jste právě načítá projekty a procházení kódu, můžete to vypnout aby se zabránilo stahování imagí kontejnerů, které nepotřebujete. |
| Automaticky spustit kontejnery na pozadí | On | Docker Compose | Znovu pro zajištění zvýšeného výkonu sady Visual Studio vytvoří kontejner s připojí svazek připravené pro když sestavíte a spustíte svůj kontejner. Pokud chcete řídit, kdy se vytvoří kontejner, vypněte toto. |
| Automaticky ukončit kontejnery na řešení zavřít | On | Docker Compose | Pokud byste o ni kontejnerů pro vaše řešení, aby kontinuálně běžely po zavření řešení nebo zavření sady Visual Studio, vypnutí této funkce. |
| Nezobrazovat výzvu důvěřující certifikátu SSL pro localhost | Off | Projekty ASP.NET Core 2.2 | Pokud localhost certifikát SSL není důvěryhodný, Visual Studio zobrazí výzvu pokaždé, když spuštění projektu, pokud je toto políčko zaškrtnuté. |

> [!WARNING]
> Pokud localhost certifikát SSL není důvěryhodný a zaškrtněte políčko pro potlačení výzvy k potvrzení, nemusí podařit HTTPS webové požadavky v době běhu ve vaší aplikaci nebo službě. V takovém případě zrušte zaškrtnutí políčka **nechcete zobrazovat výzvu** zaškrtávací políčko, spouštění vašeho projektu a označuje vztah důvěryhodnosti na řádku.

> [!TIP]
> Další podrobnosti o implementaci služby a použití sady Visual Studio Tools for Docker v následujících článcích:
>
>Ladění aplikací v místním kontejneru Dockeru: <https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>Nasazení kontejneru ASP.NET do služby container registry pomocí sady Visual Studio: <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[Předchozí](docker-apps-inner-loop-workflow.md)
>[další](set-up-windows-containers-with-powershell.md)
