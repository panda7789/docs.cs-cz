---
title: Nástroje Visual Studia pro Docker ve Windows
description: Seznamte se s nástroji Dockeru dostupnými ve Visual Studiu 2017 verze 15.7 a novějších.
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 2b6fdc33f9cf850cf9e52fca4a1a9754cd412567
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295808"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>Použití nástrojů Dockeru ve Visual Studiu 2017 ve Windows

Pracovní postup pro vývojáře při použití nástrojů Dockeru zahrnutých ve Visual Studiu 2017 verze 15.7 a novějších je podobný jako použití kódu Visual Studio a cli Dockeru (ve skutečnosti je založený na stejném cli Dockeru), ale je jednodušší začít, zjednodušuje proces a poskytuje vyšší produktivitu pro úlohy sestavení, spuštění a vytváření. Může také spustit a ladit kontejnery `F5` `Ctrl+F5` prostřednictvím obvyklé a klíče z visual studia. Můžete dokonce ladit celé řešení, pokud jeho kontejnery jsou definovány ve stejném `docker-compose.yml` souboru na úrovni řešení.

## <a name="configure-your-local-environment"></a>Konfigurace místního prostředí

S nejnovějšími verzemi Dockeru pro Windows je vývoj aplikací Dockeru jednodušší než kdy dříve, protože nastavení je jednoduché, jak je vysvětleno v následujících odkazech.

> [!TIP]
> Další informace o instalaci Dockeru pro<https://docs.docker.com/docker-for-windows/>Windows najdete na .

## <a name="docker-support-in-visual-studio-2017"></a>Podpora Dockeru ve Visual Studiu 2017

Existují dvě úrovně podpory Dockeru, které můžete přidat do projektu. V ASP.NET projektů Core můžete `Dockerfile` do projektu přidat soubor povolením podpory Dockeru. Další úroveň je podpora orchestrace kontejneru, která přidá `Dockerfile` do projektu (pokud `docker-compose.yml` ještě neexistuje) a soubor na úrovni řešení. Podpora orchestrace kontejnerů, přes Docker Compose, je přidána ve výchozím nastavení ve verzích Visual Studio 2017 15.0 až 15.7. Podpora orchestrace kontejnerů je funkce přihlášení ve verzi Visual Studio 2017 15.8 nebo novější. Verze 15.8 novější podporu Docker Compose a Service Fabric.

Příkazy **Přidat podporu > Dockeru** a **Přidat > orchestrator kontejneru jsou** umístěny v nabídce pravým tlačítkem myši (nebo kontextové nabídce) uzlu projektu pro ASP.NET základní projekt v **Průzkumníku řešení**, jak je znázorněno na obrázku 4-31:

![Přidat možnost nabídky podpory Dockeru v sadě Visual Studio](./media/add-docker-support-menu.png)

**Obrázek 4-31**. Přidání podpory Dockeru do projektu Visual Studia 2017

### <a name="add-docker-support"></a>Přidání podpory Dockeru

Podporu Dockeru můžete přidat k existujícímu projektu ASP.NET Core tak, že v **Průzkumníku řešení**vyberete **Přidat** > podporu**Dockeru** . Podporu Dockeru můžete povolit také při vytváření projektu tak, že v dialogovém okně **Nová ASP.NET základní webová aplikace,** které se otevře po klepnutí na **tlačítko OK** v dialogovém okně **Nový projekt,** vyberete **možnost Povolit podporu Dockeru,** jak je znázorněno na obrázku 4-32.

![Povolení podpory Dockeru pro novou ASP.NET základní webovou aplikaci ve Visual Studiu](./media/enable-docker-support-visual-studio.png)

**Obrázek 4-32**. Povolení podpory Dockeru během vytváření projektu ve Visual Studiu 2017

Když přidáte nebo povolíte podporu Dockeru, Visual Studio přidá do projektu soubor *Dockerfile.*

> [!NOTE]
> Když povolíte podporu Docker Compose během vytváření projektu pro ASP.NET projektu (.NET Framework, ne .NET Core project), jak je znázorněno na obrázku 4-33, je přidána také podpora orchestrace kontejneru.

![Povolení podpory dockeru pro ASP.NET projekt](media/enable-docker-compose-support.png)

**Obrázek 4-33**. Povolení podpory Dockeru Compose pro projekt ASP.NET v sadě Visual Studio 2017

### <a name="add-container-orchestration-support"></a>Přidání podpory orchestrace kontejnerů

Pokud chcete vytvořit řešení s více kontejnery, přidejte podporu orchestrace kontejnerů do vašich projektů. To umožňuje spustit a ladit skupinu kontejnerů (celé řešení) současně, pokud jsou definovány ve stejném souboru *docker-compose.yml.*

Chcete-li přidat podporu orchestrace kontejneru, klepněte pravým tlačítkem myši na uzel řešení nebo projektu v **Průzkumníku řešení**a zvolte **Přidat > podporu orchestrace kontejneru**. Pak zvolte **Docker Compose** nebo **Service Fabric** pro správu kontejnerů.

Po přidání podpory orchestrace kontejnerů do projektu se zobrazí dockerfile přidaný do projektu a složka **docker-compose přidaná** do řešení v **Průzkumníku řešení**, jak je znázorněno na obrázku 4-34:

![Soubory Dockeru v Průzkumníkovi řešení v Sadě Visual Studio](media/docker-support-solution-explorer.png)

**Obrázek 4-34**. Soubory Dockeru v Průzkumníkovi řešení v Visual Studiu 2017

Pokud *docker-compose.yml* již existuje, Visual Studio pouze přidá požadované řádky konfiguračního kódu.

## <a name="configure-docker-tools"></a>Konfigurace nástrojů Dockeru

V hlavní nabídce zvolte **Nástroje > Možnosti**a **rozbalte položku Nástroje kontejneru > Nastavení**. Zobrazí se nastavení nástrojů kontejneru.

![Možnosti nástrojů Visual Studio Docker, zobrazující: Automaticky vytahovat požadované image Dockeru při načtení projektu, Automaticky spustit kontejnery na pozadí, Automaticky zabít kontejnery při zavření řešení a Nezobrazovat výzvu k důvěřování certifikátu SSL.](./media/visual-studio-docker-tools-options.png)

**Obrázek 4-35**. Možnosti nástrojů Dockeru

Následující tabulka vám může pomoci při rozhodování o nastavení těchto možností.

| Name (Název) | Výchozí nastavení | Platí pro | Popis |
| -----|:---------------:|:----------:| ----------- |
| Automatické vytahování požadovaných ibi Dockeru při zatížení projektu | Zapnuto | Docker Compose | Pro zvýšení výkonu při načítání projektů, Visual Studio spustí operace vyžádat Docker na pozadí tak, že když jste připraveni ke spuštění kódu, image je již stažena nebo v procesu stahování. Pokud právě načítáte projekty a procházíte kód, můžete to vypnout, abyste se vyhnuli stahování obrázků kontejnerů, které nepotřebujete. |
| Automatické spouštění kontejnerů na pozadí | Zapnuto | Docker Compose | Znovu pro zvýšení výkonu Visual Studio vytvoří kontejner s připojením svazku připravené pro při vytváření a spuštění kontejneru. Pokud chcete řídit, kdy je váš kontejner vytvořen, vypněte toto. |
| Automaticky zabít kontejnery na řešení zavřít | Zapnuto | Docker Compose | Vypněte tuto otázku, pokud chcete, aby kontejnery pro vaše řešení nadále spouštěly po zavření řešení nebo zavření sady Visual Studio. |
| Nezobrazovat výzvu k důvěřování certifikátu Localhost SSL | Vypnuto | ASP.NET projekty Core 2.2 | Pokud certifikát Localhost SSL není důvěryhodný, Visual Studio zobrazí výzvu při každém spuštění projektu, pokud toto políčko není zaškrtnuto. |

> [!WARNING]
> Pokud certifikát Localhost SSL není důvěryhodný a zaškrtnete políčko potlačit výzvy, pak https webové požadavky může selhat za běhu ve vaší aplikaci nebo službě. V takovém případě zaškrtněte políčko **Nezobrazovat výzvu,** spusťte projekt a na výzvu uveďte důvěryhodnost.

> [!TIP]
> Další podrobnosti o implementaci služeb a použití nástrojů Visual Studio pro Docker, přečtěte si následující články:
>
>Ladění aplikací v místním kontejneru Dockeru:<https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>Nasazení kontejneru ASP.NET do registru kontejneru pomocí sady Visual Studio:<https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[Předchozí](docker-apps-inner-loop-workflow.md)
>[další](set-up-windows-containers-with-powershell.md)
