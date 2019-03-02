---
title: Proces vývoje pro Azure
description: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure | Proces vývoje pro Azure
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: b7a6ae343feae7c28fb7debdc8a6b617872d262f
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202103"
---
# <a name="development-process-for-azure"></a>Proces vývoje pro Azure

> _"S cloudem, jednotlivce a malé firmy můžete Přichytit jejich prsty a okamžitě nastavit služby na podnikové úrovni."_  
> _- Roy Stephan_

## <a name="vision"></a>Obraz

> *Vyvíjejte aplikace dobře navržené ASP .NET Core způsobem, který vám vyhovuje, pomocí sady Visual Studio nebo rozhraní příkazového řádku dotnet a Visual Studio Code nebo vašem editoru podle výběru.*

## <a name="development-environment-for-aspnet-core-apps"></a>Vývojové prostředí pro aplikace ASP.NET Core

### <a name="development-tools-choices-ide-or-editor"></a>Možnosti vývojářských nástrojů: Prostředím IDE nebo editorem

Ať už dáváte přednost úplné a výkonné IDE nebo editoru jednoduchý a flexibilní, Microsoft vám kryje záda při vývoji aplikací ASP.NET Core.

**Visual Studio 2017.** Pokud používáte *Visual Studio 2017* můžete vytvářet ASP.NET Core aplikace za předpokladu, že máte *vývoj pro různé platformy .NET Core* nainstalovaná úloha. Obrázek 10-1 zobrazuje požadovaná úloha v dialogovém okně nastavení Visual Studio 2017.

![](./media/image10-1.png)

**Obrázek 10-1.** Při instalaci úlohy .NET Core v sadě Visual Studio 2017.

[Stažení sady Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

**Visual Studio Code a rozhraní příkazového řádku dotnet** (nástroje Cross-Platform pro Mac, Linux a Windows). Pokud dáváte přednost jednoduchý a multiplatformní editor podporuje libovolný jazyk vývoj, můžete použít Microsoft Visual Studio Code a rozhraní příkazového řádku dotnet. Tyto produkty poskytuje jednoduché a přitom robustní prostředí, které zjednodušuje pracovní postup pro vývojáře. Kromě toho Visual Studio Code podporuje rozšíření pro jazyk C\# a vývoj pro web, technologie intellisense a místní úlohy v editoru.

[Stáhnout .NET Core SDK](https://www.microsoft.com/net/download/core)

[Stáhněte si Visual Studio Code](https://code.visualstudio.com/download)

## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Pracovní postup vývoje aplikací hostovaných v Azure ASP.NET Core

Životní cyklus vývoje aplikací začíná od počítače každý vývojář, psaní kódu aplikace pomocí jejich upřednostňovaný jazyk a místní testování. Vývojáři rozhodnout jejich preferovaného systému správy zdrojového a můžete nakonfigurovat průběžnou integraci (CI) a/nebo průběžné doručování/nasazování (CD) pomocí serveru sestavení nebo na základě předdefinovaných funkcí Azure.

Abyste mohli začít s vývojem aplikace ASP.NET Core pomocí CI/CD, můžete použít Azure DevOps služby nebo vaše organizace vlastní Team Foundation Server (TFS).

### <a name="initial-setup"></a>Počáteční nastavení

Pokud chcete vytvořit kanál pro vydávání verzí pro vaši aplikaci, musíte mít kód vaší aplikace ve správě zdrojového kódu. Nastavení místního úložiště a připojte ho do vzdáleného úložiště v týmovém projektu. Postupujte podle těchto pokynů:

- [Sdílení kódu pomocí Gitu a Visual Studio](https://docs.microsoft.com/azure/devops/git/share-your-code-in-git-vs) nebo

- [Sdílení kódu s TFVC a sady Visual Studio](https://docs.microsoft.com/azure/devops/tfvc/share-your-code-in-tfvc-vs)

Vytvořte na Azure App Service, kde budete nasazovat aplikaci. Vytvoření webové aplikace tak, že přejdete do okna pro aplikační služby na portálu Azure portal. Klikněte na + Přidat, vyberte šablonu Web App, klikněte na tlačítko Vytvořit a zadejte název a další podrobnosti. Webová aplikace bude přístupné z {name}. azurewebsites.net.

![AzureWebApp](./media/image10-2.png)

**Obrázek 10-2.** Vytvořit novou Azure App Service webovou aplikaci na webu Azure Portal.

Proces sestavení CI provede automatické sestavení pokaždé, když se zaměřuje na úložiště správy zdrojového kódu v projektu nový kód. Získáte okamžitou zpětnou vazbu, ke které dojde k sestavení kódu (a v ideálním případě předá automatizované testy) a může potenciálně být nasazen. Toto sestavení CI vytvoří webové nasazení artefaktů balíček a publikujte ji za spotřebu procesem CD.

[Definování procesu sestavení CI](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#ci)

Nezapomeňte si aktivovat nepřetržitou integraci, takže systém bude zařadit sestavení do fronty pokaždé, když se někdo z vašeho týmu potvrdí nový kód. Sestavení testu a ověřte, že je vytváření webového balíčku nasadit v jednom z jeho artefaktů.

Po úspěšném sestavení, nasadí váš proces průběžného Doručování výsledky sestavení CI do webové aplikace Azure. Pokud chcete nastavit tuto konfiguraci, můžete vytvořit a nakonfigurovat *vydání*, který se nasadí do služby Azure App Service.

[Definování procesu vydávání verzí CD](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#cd)

Po nakonfigurování svůj kanál CI/CD provést aktualizace webové aplikace a potvrzovat je do správy zdrojového kódu k jejich nasazení.

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Pracovní postup pro vývoj aplikací ASP.NET Core hostovaných v Azure

Po konfiguraci účtu Azure a procesu CI/CD, vývoj aplikací hostovaných v Azure ASP.NET Core je jednoduché. Níže jsou uvedeny základní kroky, které obvykle provést při sestavování aplikace ASP.NET Core, hostované ve službě Azure App Service jako webovou aplikaci, jak je znázorněno v obrázek 10-3.

![EndToEndDevDeployWorkflow](./media/image10-3.png)

**Obrázek 10-3.** Krok za krokem pracovního postupu pro vytváření aplikací ASP.NET Core a hostování v Azure

#### <a name="step-1-local-dev-environment-inner-loop"></a>Krok 1. Vnitřní smyčku místním vývojovém prostředí

Vývoj aplikace ASP.NET Core pro nasazení do Azure se nijak neliší od vývoje aplikace jinak. Používejte místní vývojové prostředí, které vám bude vyhovovat, ať už je Visual Studio 2017 nebo rozhraní příkazového řádku dotnet a Visual Studio Code nebo preferovaného editoru. Můžete psaní kódu, spouštět a ladit vaše změny, spuštění automatizovaných testů a provádět místní potvrzení změn správy zdrojových kódů, dokud jste připraveni své změny odeslat do svým úložištěm řízení zdrojů sdílené.

#### <a name="step-2-application-code-repository"></a>Krok 2. Úložiště kódu aplikace

Pokaždé, když budete připraveni sdílet svůj kód se svým týmem, by měl své změny odeslat z místního zdroje úložiště do úložiště sdílené zdrojového kódu vašeho týmu. Pokud jste pracovali na vlastní větvi, tento krok obvykle zahrnuje, sloučení kódu do větve sdílené (třeba podle zprávy z [žádosti o přijetí změn](https://docs.microsoft.com/azure/devops/git/pull-requests)).

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>Krok 3. Build Server: Průběžná integrace. sestavení, testování, balíček

Nové sestavení se aktivuje na server sestavení pokaždé, když je do úložiště kódu sdílené aplikace provede nové potvrzení. Jako součást procesu CI musí toto sestavení plně který aplikaci zkompiluje a spuštění automatizovaných testů, abychom potvrdili, že vše funguje podle očekávání. Konečný výsledek procesu CI by měl být zabalené verze webové aplikace připravené na nasazení.

#### <a name="step-4-build-server-continuous-delivery"></a>Krok 4. Build Server: Průběžné doručování

Po úspěšném sestavení proces průběžného Doručování vyzvedne, až bude vytvořen artefaktů sestavení. Bude se jednat webové nasazení balíčku. Server sestavení se nasadí do služby Azure App Service, nahradí všechny existující služby nově vytvořené sadou tento balíček. Obvykle tento krok, zaměřuje přípravné prostředí, ale některé aplikace nasadit přímo do produkčního prostředí prostřednictvím proces průběžného Doručování.

#### <a name="step-5-azure-app-service-web-app"></a>Krok 5. Webová aplikace Azure App Service

Po nasazení aplikace ASP.NET Core se spouští v kontextu webové aplikace služby Azure App Service. Tato webová aplikace je možné monitorovat a dále konfigurovat pomocí webu Azure Portal.

#### <a name="step-6-production-monitoring-and-diagnostics"></a>Krok 6. Monitorování produkčního prostředí a Diagnostika

Zatímco webová aplikace běží, můžete sledovat stav aplikace a shromažďovat data o chování uživatelů a diagnostiku. Application Insights je součástí sady Visual Studio a nabízí automatickou instrumentaci pro aplikace ASP.NET. To vám může poskytnout informace o využití, výjimky, požadavků, výkonu a protokolech.

## <a name="references"></a>Odkazy

**Sestavení a nasazení aplikace ASP.NET Core do Azure**  
<https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core>

>[!div class="step-by-step"]
>[Předchozí](test-asp-net-core-mvc-apps.md)
>[další](azure-hosting-recommendations-for-asp-net-web-apps.md)