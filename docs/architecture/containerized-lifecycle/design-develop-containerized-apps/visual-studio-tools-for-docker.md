---
title: Visual Studio Tools for Docker ve Windows
description: Získejte informace o nástrojích Docker dostupných v aplikaci Visual Studio 2017 verze 15,7 a novější.
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 2b6fdc33f9cf850cf9e52fca4a1a9754cd412567
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295808"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>Použití nástrojů Docker v aplikaci Visual Studio 2017 ve Windows

Pracovní postup vývojáře při použití nástrojů Docker, který je součástí sady Visual Studio 2017 verze 15,7 a novější, je podobný použití Visual Studio Code a Docker CLI (ve skutečnosti je založena na stejném rozhraní příkazového řádku Docker), ale je snazší ho snadno spustit, zjednodušit proces a poskytuje větší produktivitu pro úlohy vytváření, spouštění a vytváření. Může také spouštět a ladit kontejnery prostřednictvím běžných `F5` klíčů a `Ctrl+F5` z aplikace Visual Studio. Můžete dokonce ladit celé řešení, pokud jsou jeho kontejnery definovány ve stejném `docker-compose.yml` souboru na úrovni řešení.

## <a name="configure-your-local-environment"></a>Konfigurace místního prostředí

S nejnovějšími verzemi Docker for Windows je snazší než dřív vyvíjet aplikace Docker, protože nastavení je jednoduché, jak je vysvětleno v následujících odkazech.

> [!TIP]
> Další informace o instalaci Docker for Windows najdete na webu (<https://docs.docker.com/docker-for-windows/>).

## <a name="docker-support-in-visual-studio-2017"></a>Podpora Docker v aplikaci Visual Studio 2017

Existují dvě úrovně podpory Docker, které můžete přidat do projektu. V ASP.NET Core projekty můžete pouze přidat `Dockerfile` soubor do projektu povolením podpory Docker. Další úrovní je podpora orchestrace kontejnerů, která přidá `Dockerfile` do projektu (Pokud ještě neexistuje) `docker-compose.yml` a soubor na úrovni řešení. Podpora orchestrace kontejnerů, prostřednictvím Docker Compose, je ve výchozím nastavení přidána v aplikaci Visual Studio 2017 verze 15,0 na 15,7. Podpora orchestrace kontejnerů je funkce výslovného souhlasu v aplikaci Visual Studio 2017 verze 15,8 nebo novější. Verze 15,8 později podporuje Docker Compose a Service Fabric.

Příkazy **Přidat podporu > Docker** a **Přidat > kontejneru nástroje Orchestrator** jsou umístěné v místní nabídce (nebo v kontextové nabídce) uzlu projektu pro ASP.NET Core projektu v **Průzkumník řešení**, jak je znázorněno na obrázku 4-31:

![Přidat možnost nabídky Docker support v aplikaci Visual Studio](./media/add-docker-support-menu.png)

**Obrázek 4-31**. Přidání podpory Docker do projektu sady Visual Studio 2017

### <a name="add-docker-support"></a>Přidat podporu Docker

Podporu Docker můžete přidat do existujícího projektu ASP.NET Core tak, že v **Průzkumník řešení**vyberete **Přidat** > **podporu Docker** . Můžete také povolit podporu Docker během vytváření projektu výběrem možnosti **Povolit podporu Docker** v dialogovém okně **Nový ASP.NET Core webové aplikace** , které se otevře po kliknutí na tlačítko **OK** v dialogovém okně **Nový projekt** , jak je znázorněno na obrázku. 4-32.

![Povolit podporu Docker pro novou ASP.NET Core webovou aplikaci v aplikaci Visual Studio](./media/enable-docker-support-visual-studio.png)

**Obrázek 4-32**. Povolit podporu Docker během vytváření projektu v aplikaci Visual Studio 2017

Když přidáte nebo povolíte podporu Docker, Visual Studio přidá do projektu soubor *souboru Dockerfile* .

> [!NOTE]
> Pokud povolíte podporu Docker Compose během vytváření projektu pro projekt ASP.NET (.NET Framework, nikoli projekt .NET Core), jak je znázorněno na obrázku 4-33, je přidána i podpora orchestrace kontejnerů.

![Povolit podporu pro vytváření Docker pro projekt ASP.NET](media/enable-docker-compose-support.png)

**Obrázek 4-33**. Povolení podpory Docker Compose pro projekt ASP.NET v aplikaci Visual Studio 2017

### <a name="add-container-orchestration-support"></a>Přidat podporu orchestrace kontejnerů

Pokud chcete vytvořit řešení s více kontejnery, přidejte do svých projektů podporu orchestrace kontejnerů. To vám umožní spouštět a ladit skupinu kontejnerů (celého řešení) ve stejnou dobu, pokud jsou definované ve stejném souboru *Docker-Compose. yml* .

Chcete-li přidat podporu orchestrace kontejnerů, klikněte pravým tlačítkem myši na uzel řešení nebo projektu v **Průzkumník řešení**a vyberte možnost **Přidat > podporu orchestrace kontejnerů**. Pak zvolte **Docker Compose** nebo **Service Fabric** ke správě kontejnerů.

Po přidání podpory orchestrace kontejnerů do projektu se zobrazí souboru Dockerfile do projektu a do složky **Docker-Docker** přidané do řešení v **Průzkumník řešení**, jak je znázorněno na obrázku 4-34:

![Soubory Docker v Průzkumník řešení v aplikaci Visual Studio](media/docker-support-solution-explorer.png)

**Obrázek 4-34**. Soubory Docker v Průzkumník řešení v aplikaci Visual Studio 2017

Pokud *Docker-Compose. yml* už existuje, Visual Studio přidá do něj požadované řádky konfiguračního kódu.

## <a name="configure-docker-tools"></a>Konfigurace nástrojů Docker

V hlavní nabídce vyberte **nástroje > možnosti**a rozbalte položku **nástroje kontejneru > Nastavení**. Zobrazí se nastavení nástroje kontejneru.

![Možnosti nástrojů Docker sady Visual Studio zobrazující: Automatické vyžádání požadovaných imagí Docker při načtení projektu, automatické spuštění kontejnerů na pozadí, automatické ukončení kontejnerů při zavření řešení a nedotazování na důvěryhodný certifikát SSL.](./media/visual-studio-docker-tools-options.png)

**Obrázek 4-35**. Možnosti nástrojů Docker

Následující tabulka vám může pomáhat při rozhodování, jak tyto možnosti nastavit.

| Name | Výchozí nastavení | Platí pro | Popis |
| -----|:---------------:|:----------:| ----------- |
| Při načtení projektu automaticky stáhnout požadované image Docker | On | Docker Compose | Pro zvýšení výkonu při načítání projektů aplikace Visual Studio spustí operaci získání dat Docker na pozadí, takže až budete připraveni ke spuštění kódu, image je již stažena nebo v procesu stahování. Pokud načítáte pouze projekty a kód procházení, můžete tuto možnost vypnout, aby nedocházelo ke stahování imagí kontejneru, které nepotřebujete. |
| Automatické spouštění kontejnerů na pozadí | On | Docker Compose | Pro zvýšení výkonu Visual Studio vytvoří kontejner s připojenými svazky, který je připravený pro sestavení a spuštění kontejneru. Pokud chcete určit, kdy se kontejner vytvoří, vypněte ho. |
| Automaticky odstranit kontejnery v blízkosti řešení | On | Docker Compose | Tuto funkci zapněte, pokud chcete, aby kontejnery pro vaše řešení nadále běžely po zavření řešení nebo ukončení sady Visual Studio. |
| Nedotazovat se na důvěřování certifikátům SSL místního hostitele | Off | Projekty ASP.NET Core 2,2 | Pokud se nejedná o důvěryhodný certifikát SSL pro localhost, Visual Studio se zobrazí dotaz při každém spuštění projektu, pokud není zaškrtnuto toto políčko. |

> [!WARNING]
> Pokud certifikát SSL pro localhost není důvěryhodný a zaškrtnete políčko pro potlačení výzvy, můžou webové požadavky HTTPS za běhu ve vaší aplikaci nebo službě selhat. V takovém případě zrušte zaškrtnutí políčka **nedotazovat** se na výzvu, spusťte projekt a na příkazovém řádku uveďte vztah důvěryhodnosti.

> [!TIP]
> Další podrobnosti o implementaci služeb a použití Visual Studio Tools for Docker najdete v následujících článcích:
>
>Ladění aplikací v místním kontejneru Docker:<https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>Nasazení kontejneru ASP.NET do registru kontejneru pomocí sady Visual Studio:<https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[Předchozí](docker-apps-inner-loop-workflow.md)Další
>[](set-up-windows-containers-with-powershell.md)
