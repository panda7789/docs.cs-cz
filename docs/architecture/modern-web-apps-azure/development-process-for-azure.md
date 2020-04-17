---
title: Proces vývoje pro Azure
description: Architekt moderní webové aplikace s ASP.NET core a Azure | Proces vývoje pro Azure
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 640cfebea3c70314be4a597bc07b0dc6854f5848
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607890"
---
# <a name="development-process-for-azure"></a>Proces vývoje pro Azure

> _"Díky cloudu mohou jednotlivci i malé firmy lusknout prsty a okamžitě nastavit služby podnikové třídy."_  
> _- Roy Štěpán_

## <a name="vision"></a>Obraz

> *Vyvíjejte dobře navržené aplikace ASP .NET Core tak, jak se vám líbí, pomocí sady Visual Studio nebo dotnet CLI a Visual Studio Code nebo editoru.*

## <a name="development-environment-for-aspnet-core-apps"></a>Vývojové prostředí pro ASP.NET základní aplikace

### <a name="development-tools-choices-ide-or-editor"></a>Volby vývojových nástrojů: IDE nebo editor

Ať už dáváte přednost úplnému a výkonnému rozhraní IDE nebo lehkému a agilnímu editoru, společnost Microsoft vás pokryje při vývoji aplikací ASP.NET Core.

**Visual Studio 2019.** Visual Studio 2019 je nejlepší ide ve své třídě pro vývoj aplikací pro ASP.NET Core. Nabízí celou řadu funkcí, které zvyšují produktivitu vývojářů. Můžete ji použít k vývoji aplikace a poté analyzovat její výkon a další charakteristiky. Integrovaný ladicí program umožňuje pozastavit spuštění kódu a krok tam a zpět prostřednictvím kódu za běhu, jak je spuštěn. Vestavěný testovací běžec umožňuje uspořádat testy a jejich výsledky a dokonce může provádět živé testování částí při kódování. Pomocí live share můžete spolupracovat v reálném čase s ostatními vývojáři a bez problémů sdílet relaci kódu v síti. A až budete připraveni, Visual Studio obsahuje vše, co potřebujete k publikování aplikace do Azure nebo kdekoli, kde ji můžete hostovat.

[Stáhněte si Visual Studio 2019](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

**Visual Studio Code a dotnet CLI** (Nástroje pro různé platformy pro Mac, Linux a Windows). Pokud dáváte přednost lehký a cross-platformní editor podporující jakýkoli vývojový jazyk, můžete použít Microsoft Visual Studio Code a dotnet CLI. Tyto produkty poskytují jednoduché, ale robustní prostředí, které zjednodušuje pracovní postup pro vývojáře. Kromě toho Visual Studio Code podporuje\# rozšíření pro C a vývoj webových aplikací, poskytuje intellisense a zkratky úkoly v rámci editoru.

[Stažení sady .NET Core SDK](https://dotnet.microsoft.com/download)

[Stáhnout kód sady Visual Studio](https://code.visualstudio.com/download)

## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Pracovní postup vývoje pro aplikace ASP.NET Core hostované v Azure

Životní cyklus vývoje aplikací se spustí z počítače každého vývojáře, kódovat aplikaci pomocí jejich preferovaného jazyka a testování místně. Vývojáři si mohou vybrat svůj upřednostňovaný systém správy zdrojového kódu a mohou konfigurovat průběžnou integraci (CI) a/nebo průběžné doručování/nasazení (CD) pomocí serveru sestavení nebo na základě integrovaných funkcí Azure.

Chcete-li začít s vývojem aplikace ASP.NET Core pomocí CI/CD, můžete použít Služby Azure DevOps nebo vlastní server Team Foundation (TFS) vaší organizace.

### <a name="initial-setup"></a>Počáteční nastavení

Chcete-li vytvořit kanál vydání pro vaši aplikaci, musíte mít kód aplikace ve zdrojovém kódu. Nastavte místní úložiště a připojte ho ke vzdálenému úložišti v týmovém projektu. Postupujte podle těchto pokynů:

- [Sdílení kódu s Gitem a Visual Studio](https://docs.microsoft.com/azure/devops/git/share-your-code-in-git-vs) nebo

- [Sdílení kódu s TFVC a Visual Studio](https://docs.microsoft.com/azure/devops/tfvc/share-your-code-in-tfvc-vs)

Vytvořte službu Azure App Service, kde budete nasadit svou aplikaci. Vytvořte webovou aplikaci tak, že přejdete do okna Služby aplikací na webu Azure Portal. Klikněte na +Přidat, vyberte šablonu Web Appu, klikněte na Vytvořit a zadejte název a další podrobnosti. Webová aplikace bude přístupná z {name}.azurewebsites.net.

![AzureWebApp](./media/image10-2.png)

**Obrázek 10-1.** Vytvoření nové webové aplikace Služby aplikací Azure na webu Azure Portal.

Proces sestavení CI provede automatické sestavení vždy, když je do úložiště správy zdrojového kódu projektu potvrzen nový kód. To vám dává okamžitou zpětnou vazbu, že kód sestaví (a v ideálním případě projde automatizované testy) a může být potenciálně nasazen. Toto sestavení CI vytvoří artefakt balíčku nasazení webu a publikuje jej pro spotřebu procesem disku CD.This CI build will produce a web deploy package artifact and publish it for consumption by YOUR CD process.

[Definování procesu sestavení CI](https://docs.microsoft.com/azure/devops/pipelines/ecosystems/dotnet-core)

Ujistěte se, že povolit průběžnou integraci, takže systém bude fronty sestavení vždy, když někdo z vašeho týmu potvrdí nový kód. Otestujte sestavení a ověřte, zda vytváří balíček nasazení webu jako jeden z jeho artefaktů.

Když sestavení proběhne úspěšně, proces cd nasadí výsledky vašeho sestavení CI do webové aplikace Azure. Chcete-li to nakonfigurovat, vytvořte a nakonfigurujte *verzi*, která se nasadí do služby Azure App Service.

[Nasazení webové aplikace Azure](https://docs.microsoft.com/azure/devops/pipelines/targets/webapp)

Jakmile je kanál CI/CD nakonfigurován, můžete jednoduše provést aktualizace webové aplikace a potvrdit je do správy zdrojového kódu, aby byly nasazeny.

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Pracovní postup pro vývoj aplikací ASP.NET Core hostovaných v Azure

Po konfiguraci účtu Azure a procesu CI/CD je vývoj aplikací hostovaných v Azure ASP.NET Core jednoduchý. Následují základní kroky, které obvykle provedete při vytváření aplikace ASP.NET Core, hostované ve službě Azure App Service jako webová aplikace, jak je znázorněno na obrázku 10-2.

![EndToEndDevDeployWorkflow](./media/image10-3.png)

**Obrázek 10-2.** Podrobný pracovní postup pro vytváření aplikací ASP.NET Core a jejich hostování v Azure

#### <a name="step-1-local-dev-environment-inner-loop"></a>Krok 1. Vnitřní smyčka místního prostředí pro dev prostředí

Vývoj aplikace ASP.NET Core pro nasazení do Azure se nijak neliší od vývoje aplikace jinak. Použijte prostředí místního vývoje, se kterým jste spokojení, ať už je to Visual Studio 2017 nebo dotnet CLI a Visual Studio Code nebo preferovaný editor. Můžete psát kód, spouštět a ladit změny, spouštět automatizované testy a provádět místní potvrzení do správy zdrojového kódu, dokud nebudete připraveni posunout změny do sdíleného úložiště správy zdrojového kódu.

#### <a name="step-2-application-code-repository"></a>Krok 2. Úložiště kódu aplikace

Kdykoli budete připraveni sdílet kód se svým týmem, měli byste své změny z místního zdrojového úložiště odsunout do sdíleného zdrojového úložiště vašeho týmu. Pokud jste pracovali ve vlastní větvi, tento krok obvykle zahrnuje sloučení kódu do sdílené větve (například pomocí [žádosti o přijetí vyžádat).](https://docs.microsoft.com/azure/devops/git/pull-requests)

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>Krok 3. Build Server: Průběžná integrace. sestavení, testování, balení

Nové sestavení se aktivuje na serveru sestavení při každém provedení nového potvrzení do úložiště kódu sdílené aplikace. Jako součást procesu CI by toto sestavení mělo plně zkompilovat aplikaci a spustit automatizované testy, abyste potvrdili, že vše funguje podle očekávání. Konečným výsledkem procesu CI by měla být zabalená verze webové aplikace připravená k nasazení.

#### <a name="step-4-build-server-continuous-delivery"></a>Krok 4. Server sestavení: Průběžné doručování

Jakmile sestavení bylo úspěšné, proces CD převezme artefakty sestavení vyrobené. To bude zahrnovat balíček nasazení webu. Server sestavení nasadí tento balíček do služby Azure App Service a nahradí všechny existující služby nově vytvořenou službou. Tento krok obvykle cílí na pracovní prostředí, ale některé aplikace se nasazují přímo do produkčního prostředí prostřednictvím procesu CD.

#### <a name="step-5-azure-app-service-web-app"></a>Krok 5. Webová aplikace Azure App Service

Po nasazení se aplikace ASP.NET Core spustí v kontextu webové aplikace Služby Azure App Service. Tuto webovou aplikaci můžete monitorovat a dále konfigurovat pomocí portálu Azure Portal.

#### <a name="step-6-production-monitoring-and-diagnostics"></a>Krok 6. Monitorování a diagnostika výroby

Během spuštění webové aplikace můžete sledovat stav aplikace a shromažďovat diagnostická data a data chování uživatelů. Application Insights je součástí sady Visual Studio a nabízí automatickou instrumentaci pro ASP.NET aplikace. Může vám poskytnout informace o použití, výjimky, požadavky, výkon a protokoly.

## <a name="references"></a>Odkazy

**Sestavení a nasazení ASP.NET základní aplikace do Azure**  
<https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core>

>[!div class="step-by-step"]
>[Předchozí](test-asp-net-core-mvc-apps.md)
>[další](azure-hosting-recommendations-for-asp-net-web-apps.md)
