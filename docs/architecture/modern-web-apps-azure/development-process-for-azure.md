---
title: Proces vývoje pro Azure
description: Architekt moderních webových aplikací pomocí ASP.NET Core a Azure | Proces vývoje pro Azure
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 830271d76e5a87ed782d81fa9491328c580f0f87
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849585"
---
# <a name="development-process-for-azure"></a>Proces vývoje pro Azure

> _"Díky cloudu můžou jednotlivci a malé firmy přitahovat prsty a okamžitě nastavit služby podnikové třídy."_  
> _– Roy Stephana_

## <a name="vision"></a>Vision

> *Vytvářejte dobře navržené aplikace ASP .NET Core tak, jak chcete, pomocí sady Visual Studio nebo rozhraní příkazového řádku dotnet a Visual Studio Code nebo editoru výběru.*

## <a name="development-environment-for-aspnet-core-apps"></a>Vývojové prostředí pro aplikace ASP.NET Core

### <a name="development-tools-choices-ide-or-editor"></a>Možnosti vývojářských nástrojů: IDE nebo Editor

Bez ohledu na to, jestli dáváte přednost celému a výkonnému integrovanému vývojovém prostředí (IDE) nebo odlehčenému a agilnímu editoru, Microsoft vám při vývoji aplikací ASP.NET Core

**Visual Studio 2017.** Pokud používáte *Visual Studio 2017* , můžete sestavovat ASP.NET Coreé aplikace, pokud máte nainstalovanou úlohu *vývoje .NET Core pro různé platformy* . Obrázek 10-1 ukazuje požadovanou úlohu v dialogovém okně instalace sady Visual Studio 2017.

![Instalace úlohy .NET Core v aplikaci Visual Studio 2017](./media/image10-1.png)

**Obrázek 10-1.** Instalace úlohy .NET Core v aplikaci Visual Studio 2017.

[Stažení sady Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

Rozhraní příkazového **řádku Visual Studio Code a dotnet** (Nástroje pro různé platformy pro Mac, Linux a Windows). Pokud dáváte přednost zjednodušenému editoru pro různé platformy, který podporuje jazyk vývoje, můžete použít Microsoft Visual Studio kód a dotnet CLI. Tyto produkty poskytují jednoduché a přesto robustní prostředí, které zjednodušuje pracovní postup vývojářů. Kromě toho Visual Studio Code podporuje rozšíření pro jazyk\# C a vývoj pro web a poskytuje IntelliSense a zástupce úloh v editoru.

[Stáhnout .NET Core SDK](https://dotnet.microsoft.com/download)

[Stáhnout Visual Studio Code](https://code.visualstudio.com/download)

## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Pracovní postup vývoje pro aplikace ASP.NET Core hostované v Azure

Životní cyklus vývoje aplikací začíná od jednotlivých počítačů vývojářů a kóduje aplikace pomocí jejich preferovaného jazyka a lokálně testuje. Vývojáři si můžou zvolit svůj preferovaný systém správy zdrojů a můžou nakonfigurovat průběžnou integraci (CI) a průběžné doručování a nasazování (CD) pomocí serveru sestavení nebo založené na integrovaných funkcích Azure.

Pokud chcete začít s vývojem ASP.NET Core aplikace pomocí CI/CD, můžete použít Azure DevOps Services nebo vlastní Team Foundation Server (TFS) vaší organizace.

### <a name="initial-setup"></a>Počáteční nastavení

Chcete-li vytvořit kanál pro vydání aplikace, musíte mít kód aplikace ve správě zdrojového kódu. Nastavte místní úložiště a připojte ho ke vzdálenému úložišti v týmovém projektu. Postupujte podle těchto pokynů:

- [Sdílejte svůj kód s Git a sadou Visual Studio](https://docs.microsoft.com/azure/devops/git/share-your-code-in-git-vs) nebo

- [Sdílejte svůj kód s TFVC a sadou Visual Studio](https://docs.microsoft.com/azure/devops/tfvc/share-your-code-in-tfvc-vs)

Vytvořte Azure App Service, do které budete aplikaci nasazovat. Webovou aplikaci můžete vytvořit tak, že v Azure Portal převedete na okno App Services. Klikněte na + Přidat, vyberte šablonu webové aplikace, klikněte na vytvořit a zadejte název a další podrobnosti. Webová aplikace bude přístupná z {Name}. azurewebsites. NET.

![AzureWebApp](./media/image10-2.png)

**Obrázek 10-2.** Vytvoření nové Azure App Service webové aplikace na webu Azure Portal.

Proces sestavení CI provede automatizované sestavení pokaždé, když se nový kód potvrdí do úložiště správy zdrojového kódu projektu. Tím získáte okamžitou zpětnou vazbu, kterou kód sestaví (a v ideálním případě projde automatizované testy) a je možné jej nasadit. Toto sestavení CI vytvoří artefakt balíčku nasazení webu a publikuje ho pro využití procesem CD.

[Definování procesu sestavení CI](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#ci)

Nezapomeňte povolit průběžnou integraci, aby systém zařadí do fronty sestavení, kdykoli někdo v týmu potvrdí nový kód. Otestujte sestavení a ověřte, že vytváří balíček nasazení webu jako jeden z jeho artefaktů.

Po úspěšném sestavení bude váš proces CD nasazovat výsledky sestavení CI do vaší webové aplikace Azure. Pokud to chcete nakonfigurovat, vytvoříte a nakonfigurujete *vydání*, které se nasadí do vašeho Azure App Service.

[Definování procesu verze CD](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#cd)

Po nakonfigurování kanálu CI/CD můžete jednoduše provést aktualizace webové aplikace a odeslat je do správy zdrojového kódu, aby se nasadily.

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Pracovní postup pro vývoj aplikací ASP.NET Core hostovaných v Azure

Po nakonfigurování účtu Azure a procesu CI/CD je vývoj aplikací ASP.NET Core hostovaných v Azure jednoduchý. Následují základní kroky, které obvykle provádíte při sestavování aplikace ASP.NET Core hostované v Azure App Service jako webové aplikace, jak je znázorněno na obrázku 10-3.

![EndToEndDevDeployWorkflow](./media/image10-3.png)

**Obrázek 10-3.** Podrobný pracovní postup pro vytváření ASP.NET Corech aplikací a jejich hostování v Azure

#### <a name="step-1-local-dev-environment-inner-loop"></a>Krok 1. Vnitřní smyčka místního vývojového prostředí

Vývoj aplikace ASP.NET Core pro nasazení do Azure se neliší od vývoje aplikace v opačném případě. Použijte místní vývojové prostředí, se kterým máte v pohodlí, ať už jde o Visual Studio 2017 nebo dotnet CLI a Visual Studio Code nebo preferovaný Editor. Můžete psát kód, spouštět a ladit změny, spouštět automatizované testy a provádět místní potvrzení změn do správy zdrojových kódů, dokud nebudete připraveni na vložení změn do sdíleného úložiště správy zdrojového kódu.

#### <a name="step-2-application-code-repository"></a>Krok 2. Úložiště kódu aplikace

Kdykoli budete připraveni sdílet svůj kód s týmem, měli byste odeslat změny z místního zdrojového úložiště do sdíleného zdrojového úložiště vašeho týmu. Pokud pracujete ve vlastní větvi, tento krok obvykle zahrnuje sloučení kódu do sdílené větve (například prostřednictvím [žádosti](https://docs.microsoft.com/azure/devops/git/pull-requests)o přijetí změn).

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>Krok 3. Server sestavení: Průběžná integrace. sestavení, testování, balení

Nové sestavení je spuštěno na serveru sestavení vždy, když je provedeno nové potvrzení do úložiště kódu sdílené aplikace. V rámci procesu CI by toto sestavení mělo plně kompilovat aplikaci a spouštět automatizované testy, aby bylo možné potvrdit, že vše funguje podle očekávání. Konečný výsledek procesu CI by měl být zabalená verze webové aplikace připravená pro nasazení.

#### <a name="step-4-build-server-continuous-delivery"></a>Krok 4. Server sestavení: Průběžné doručování

Po úspěšném sestavení si proces CD zachová vytvořené artefakty sestavení. To bude zahrnovat balíček nasazení webu. Server sestavení tento balíček nasadí, aby Azure App Service a nahradil existující službu nově vytvořenou. Tento krok obvykle cílí na přípravné prostředí, ale některé aplikace se nasazují přímo do výroby prostřednictvím procesu CD.

#### <a name="step-5-azure-app-service-web-app"></a>Krok 5. Azure App Service webové aplikace

Po nasazení se aplikace ASP.NET Core spustí v kontextu Azure App Service webové aplikace. Tato webová aplikace se dá monitorovat a dále konfigurovat pomocí webu Azure Portal.

#### <a name="step-6-production-monitoring-and-diagnostics"></a>Krok 6. Monitorování a diagnostika provozu

Když je webová aplikace spuštěná, můžete monitorovat stav aplikace a shromažďovat data o diagnostice a chování uživatelů. Application Insights je součástí sady Visual Studio a nabízí automatické instrumentace pro aplikace ASP.NET. Může vám poskytnout informace o využití, výjimkách, požadavcích, výkonu a protokolech.

## <a name="references"></a>Odkazy

**Sestavení a nasazení aplikace ASP.NET Core do Azure**  
<https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core>

>[!div class="step-by-step"]
>[Předchozí](test-asp-net-core-mvc-apps.md)Další
>[](azure-hosting-recommendations-for-asp-net-web-apps.md)
