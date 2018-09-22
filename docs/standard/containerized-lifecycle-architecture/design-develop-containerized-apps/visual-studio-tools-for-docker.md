---
title: Pomocí sady Visual Studio Tools for Docker (Visual Studio na Windows)
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: af14c92ab27885deec878dc33e7b94035f43e65b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581217"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>Pomocí sady Visual Studio Tools for Docker (Visual Studio na Windows)

Pracovní postup vývoje při použití Visual Studio Tools for Docker je podobný pracovní postup při používání Visual Studio Code a rozhraní příkazového řádku Dockeru. Ve skutečnosti je založen na stejné rozhraní příkazového řádku Dockeru, ale je snadné začít, zjednodušuje a poskytuje větší produktivitu pro sestavení, spouštět a vytvořit úkolů. Je také možné spouštět a ladit své kontejnery prostřednictvím jednoduché akce, jako je F5 a Ctrl + F5 v sadě Visual Studio. Díky podpoře Orchestrace volitelný kontejner, kromě možnosti spuštění a ladění jednoho kontejneru můžete spustit a ladit skupinu kontejnerů (celé řešení) ve stejnou dobu. Pouze definuje kontejnery ve stejném *docker-compose.yml* souboru na úrovni řešení.

## <a name="configuring-your-local-environment"></a>Konfigurace vašeho místního prostředí

Podporu dockeru je zahrnuta v sadě Visual Studio 2017 s žádným z nainstalovaných úlohách .NET a .NET Core. Docker pro Windows instalovat samostatně.

S nejnovější verzí Docker pro Windows je jednodušší než někdy k vývoji aplikací Dockeru vzhledem k tomu, že instalační program je jasné, jak je vysvětleno v následující odkazy.

**Další informace:** Další informace o instalaci Dockeru pro Windows, přejděte na <https://docs.docker.com/docker-for-windows/>.

**Další informace:** pokyny k instalaci sady Visual Studio, přejděte na [ https://visualstudio.microsoft.com/downloads/ ](https://visualstudio.microsoft.com/downloads/).

Pokud chcete zobrazit informace o instalaci Visual Studio Tools for Docker, přejděte na <http://aka.ms/vstoolsfordocker> a <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.

## <a name="using-docker-tools-in-visual-studio-2017"></a>S použitím nástrojů Docker v sadě Visual Studio 2017

Při přidávání podpory Docker do projektu (viz obrázek 4 – 26), sada Visual Studio přidá *soubor Dockerfile* do kořenového adresáře projektu.

![Zapnutí podpory řešení Dockeru v projektu sady Visual Studio 2017](./media/image32.png)

Obrázek 4 – 26: zapnutí podpory řešení Dockeru v projektu sady Visual Studio 2017

 Podpora Orchestrace kontejnerů pomocí Docker Compose, se přidá ve výchozím nastavení v sadě Visual Studio 2017 verze 15.7 nebo starší. Podpora Orchestrace kontejnerů je přihlašovaná funkce v sadě Visual Studio 2017 verze 15.8 nebo později, v takovém případě Docker Compose a Service Fabric se nepodporuje.

Pomocí sady Visual Studio verze 15,8 a novější můžete přidat podporu pro více projektů v řešení, že mají přiřazeným kontejnerem. Klikněte pravým tlačítkem na uzel řešení nebo projektu v **Průzkumníka řešení**a zvolte **přidat** > **podpora Orchestrace kontejnerů**.  Klikněte na tlačítko **Docker Compose** nebo **Service Fabric** Spravovat kontejnery.

Pokud zvolíte **Docker Compose**, sada Visual Studio přidá oddíl služby ve vašem řešení *docker-compose.yml* soubory (nebo vytvoří soubory, pokud nebyla neexistují). Je snadný způsob, jak začít vytváření řešení více kontejnerů; pak můžete otevřít *docker-compose.yml* soubory a provede jejich aktualizaci rozšířených o další funkce.

Tato akce přidá požadované konfigurace řádky kódu *docker-compose.yml* nastavená na úrovni řešení.

Také můžete zapnout podporu Dockeru při vytváření projektu aplikace ASP.NET Core v sadě Visual Studio 2017, jak ukazuje obrázek 4 – 27.

![Zapnutí podpory Dockeru při vytváření projektu](./media/image33.png)

Obrázek 4 – 27: zapnutí podpory Dockeru při vytváření projektu

Po přidání podpory Dockeru do svého řešení v sadě Visual Studio, také uvidíte nový uzel stromu **Průzkumníka řešení** s přidaného *docker-compose.yml* soubory, jak je znázorněno v obrázek 4 – 28.

![soubory docker-compose.yml nyní zobrazit v Průzkumníku řešení](./media/image34.PNG)

Obrázek 4 – 28: soubory docker-compose.yml nově zobrazují v **Průzkumníka řešení**

Můžete nasadit aplikace s více kontejnerů pomocí jediného *docker-compose.yml* souboru při spuštění `docker-compose up`, nicméně sady Visual Studio přidá skupinu z nich, takže mohou přepsat hodnoty v závislosti na prostředí (vývojové a produkční) a provedení příkazu zadejte (vydání a ladění). Tato funkce je lepší vysvětlení najdete v dalších kapitolách.

Service Fabric místo Docker Compose můžete také použít ke správě několika kontejnerů. Zobrazit [kurz: nasazení aplikace .NET v kontejneru Windows do Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-host-app-in-a-container).

**Další informace:** další podrobnosti o implementaci služby a použití sady Visual Studio Tools for Docker v následujících článcích:

Vytváření, ladění, aktualizovat a aktualizovat aplikace v místním kontejneru Dockeru: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Nasazení kontejneru ASP.NET Core Dockeru do registru kontejneru: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

>[!div class="step-by-step"]
[Předchozí](docker-apps-inner-loop-workflow.md)
[další](set-up-windows-containers-with-powershell.md)
