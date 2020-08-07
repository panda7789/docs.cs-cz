---
title: Visual Studio Tools for Docker ve Windows
description: Získejte informace o nástrojích Docker dostupných v aplikaci Visual Studio 2017 verze 15,7 a novější.
ms.date: 08/06/2020
ms.custom: vs-dotnet
ms.openlocfilehash: 74cffaae5885a7079ec774b1e8c68241cddda99a
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915348"
---
# <a name="use-docker-tools-in-visual-studio-on-windows"></a>Použití nástrojů Docker v aplikaci Visual Studio ve Windows

Pracovní postup vývojáře při použití nástrojů Docker, který je součástí sady Visual Studio 2017 verze 15,7 a novější, je podobný použití Visual Studio Code a Docker CLI (ve skutečnosti je založen na stejném rozhraní příkazového řádku Docker), ale je snazší ho snadno spustit, zjednodušit proces a poskytuje větší produktivitu pro vytváření, spouštění a vytváření úloh. Může také spouštět a ladit kontejnery prostřednictvím běžných `F5` `Ctrl+F5` klíčů a z aplikace Visual Studio. Můžete dokonce ladit celé řešení, pokud jsou jeho kontejnery definovány ve stejném souboru na `docker-compose.yml` úrovni řešení.

## <a name="configure-your-local-environment"></a>Konfigurace místního prostředí

S nejnovějšími verzemi Docker for Windows je snazší než dřív vyvíjet aplikace Docker, protože nastavení je jednoduché, jak je vysvětleno v následujících odkazech.

> [!TIP]
> Další informace o instalaci Docker for Windows najdete na webu ( <https://docs.docker.com/docker-for-windows/> ).

## <a name="docker-support-in-visual-studio"></a>Podpora Docker v aplikaci Visual Studio

Existují dvě úrovně podpory Docker, které můžete přidat do projektu. V ASP.NET Core projekty můžete pouze přidat `Dockerfile` soubor do projektu povolením podpory Docker. Další úrovní je podpora orchestrace kontejnerů, která přidá `Dockerfile` do projektu (Pokud ještě neexistuje) a `docker-compose.yml` soubor na úrovni řešení. Podpora orchestrace kontejnerů, prostřednictvím Docker Compose, je ve výchozím nastavení přidána v aplikaci Visual Studio 2017 verze 15,0 na 15,7. Podpora orchestrace kontejnerů je funkce výslovného souhlasu v aplikaci Visual Studio 2017 verze 15,8 nebo novější. Visual Studio 2019 a novější podporuje taky nasazení **Kubernetes/Helm** .

Příkazy **Přidat podporu > Docker** a **Přidat > kontejneru nástroje Orchestrator** jsou umístěné v místní nabídce (nebo v kontextové nabídce) uzlu projektu pro ASP.NET Core projektu v **Průzkumník řešení**, jak je znázorněno na obrázku 4-31:

![Přidat možnost nabídky Docker support v aplikaci Visual Studio](media/add-docker-support-menu.png)

**Obrázek 4-31**. Přidání podpory Docker do projektu sady Visual Studio 2019

### <a name="add-docker-support"></a>Přidání podpory Dockeru

Kromě možnosti přidat podporu Docker do existující aplikace, jak je znázorněno v předchozí části, můžete také povolit podporu Docker během vytváření projektu výběrem možnosti **Povolit podporu Docker** v dialogovém okně **Nový ASP.NET Core webové aplikace** , které se otevře po kliknutí na tlačítko **OK** v dialogovém okně **Nový projekt** , jak je znázorněno na obrázku 4-32.

![Povolit podporu Docker pro novou ASP.NET Core webovou aplikaci v aplikaci Visual Studio](media/enable-docker-support-visual-studio.png)

**Obrázek 4-32**. Povolit podporu Docker během vytváření projektu v aplikaci Visual Studio 2019

Když přidáte nebo povolíte podporu Docker, Visual Studio přidá do projektu soubor _souboru Dockerfile_ , který obsahuje odkazy na všechny požadované projekty z řešení.

### <a name="add-container-orchestration-support"></a>Přidat podporu orchestrace kontejnerů

Pokud chcete vytvořit řešení s více kontejnery, přidejte do svých projektů podporu orchestrace kontejnerů. To vám umožní spouštět a ladit skupinu kontejnerů (celého řešení) ve stejnou dobu, pokud jsou definované ve stejném souboru _Docker-Compose. yml_ .

Chcete-li přidat podporu orchestrace kontejnerů, klikněte pravým tlačítkem myši na uzel řešení nebo projektu v **Průzkumník řešení**a vyberte možnost **Přidat > podporu orchestrace kontejnerů**. Pak zvolte **Kubernetes/Helm** nebo **Docker Compose** pro správu kontejnerů.

Po přidání podpory orchestrace kontejnerů do projektu se zobrazí souboru Dockerfile do projektu a do složky **Docker-Docker** přidané do řešení v **Průzkumník řešení**, jak je znázorněno na obrázku 4-33:

![Soubory Docker v Průzkumník řešení v aplikaci Visual Studio](media/docker-support-solution-explorer.png)

**Obrázek 4-33**. Soubory Docker v Průzkumník řešení v aplikaci Visual Studio 2019

Pokud _Docker-Compose. yml_ už existuje, Visual Studio přidá do něj požadované řádky konfiguračního kódu.

## <a name="configure-docker-tools"></a>Konfigurace nástrojů Docker

V hlavní nabídce vyberte **nástroje > možnosti**a rozbalte položku **nástroje kontejneru > nastavení**. Zobrazí se nastavení nástroje kontejneru.

![Možnosti nástrojů Docker pro Visual Studio, které zobrazují tři stránky: Obecné, jeden projekt a Docker Compose, podrobnosti najdete v textu článku.](media/visual-studio-docker-tools-options.png)

**Obrázek 4-34**. Možnosti nástrojů Docker

Následující tabulka vám může pomáhat při rozhodování, jak tyto možnosti nastavit.

| Stránka/nastavení                                |  Výchozí nastavení   | Description                                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------------------------------------- | :----------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Stránka Obecné**                            |
| V případě potřeby nainstalovat Docker Desktop            |     Zobrazit výzvu      |
| V případě potřeby spustit Docker Desktop              |     Zobrazit výzvu      |
| Důvěryhodný ASP.NET Core certifikát SSL          |     Zobrazit výzvu      | Pokud certifikát SSL místního hostitele není označený jako důvěryhodný (with `dotnet dev-certs https --trust` ), Visual Studio se při každém spuštění projektu zobrazí dotaz.                                                                                                                                                                                                                                                    |
| **Jedna stránka projektu**                     |
| Při otevření projektu vyžadovat vyžádání imagí Docker |        Ano        | Aby se zvýšil výkon při spuštění projektu, Visual Studio spustí operaci vyžádání obsahu Docker na pozadí, takže až budete připraveni ke spuštění kódu, image už je stažená nebo v procesu stahování. Pokud načítáte pouze projekty a kód procházení, můžete tuto možnost vypnout, aby nedocházelo ke stahování imagí kontejneru, které nepotřebujete. To může zpomalit uživatelské prostředí otevřeného projektu. |
| Stažení aktualizovaných imagí Docker při načtení projektu  | Projekty .NET Core | Získejte aktualizace stávajících imagí, abyste získali nejnovější aktualizace otevřeného projektu. To může zpomalit uživatelské prostředí otevřeného projektu.                                                                                                                                                                                                                                                                                          |
| Odebrat kontejnery při zavření projektu          |        Ano        | Vyčištění při zavření projektu, to může zpomalit činnost koncového uživatele projektu, ale většinou je to ale rychlé.                                                                                                                                                                                                                                                                                                            |
| Spustit kontejnery v otevřeném projektu              |        Ano        | Pro zvýšení výkonu při spuštění projektu Visual Studio spustí všechny kontejnery v řešení. To může zpomalit uživatelské prostředí otevřeného projektu.                                                                                                                                                                                                                                                        |
| **Docker Compose**                          |                    | Stránka Docker Compose obsahuje stejné nastavení jako jedna stránka projektu, ale platí pro řešení s více kontejnery.                                                                                                                                                                                                                                                                                           |

> [!WARNING]
> Pokud certifikát localhost místního hostitele není důvěryhodný a nastavíte možnost **nikdy**, nemusí webové požadavky HTTPS za běhu ve vaší aplikaci nebo službě selhat. V takovém případě znovu nastavte hodnotu znovu, aby se **zobrazila výzva** , nebo ještě lepší, aby certifikáty ve vývojovém počítači důvěřovaly pomocí příkazu `dotnet dev-certs https --trust` .

> [!TIP]
> Další podrobnosti o implementaci služeb a použití Visual Studio Tools for Docker najdete v následujících článcích:
>
> Ladění aplikací v místním kontejneru Docker:<https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
> Nasazení kontejneru ASP.NET do registru kontejneru pomocí sady Visual Studio:<https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

> [!div class="step-by-step"]
> [Předchozí](docker-apps-inner-loop-workflow.md) 
>  [Další](set-up-windows-containers-with-powershell.md)
