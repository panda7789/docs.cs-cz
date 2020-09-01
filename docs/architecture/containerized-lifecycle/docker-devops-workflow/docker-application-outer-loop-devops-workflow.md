---
title: Kroky ve vývoji DevOps vnější smyčky pro aplikaci Dockeru
description: Přečtěte si postup pro "vnější smyčku" pracovního postupu DevOps.
ms.date: 08/06/2020
ms.openlocfilehash: 82a45c8669812580623811e18cc55f55f45cb6d3
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271904"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Kroky ve vývoji DevOps vnější smyčky pro aplikaci Dockeru

Obrázek 5-1 prezentuje ucelené znázornění kroků, které tvoří pracovní postup vnější smyčky DevOps. Zobrazuje "vnější smyčku" DevOps. Když je kód vložen do úložiště, je spuštěn kanál CI a pak zahájí kanál CD, kde se aplikace nasadí. Metriky shromážděné z nasazených aplikací se dostanou zpět do vývojové úlohy, kde se vyskytuje "vnitřní smyčka", takže vývojové týmy mají skutečná data, která odpovídají potřebám uživatelů a obchodních potřeb.

![Diagram znázorňující 6 kroků pracovního postupu DevOps vnější smyčky.](./media/docker-application-outer-loop-devops-workflow/overview-dev-ops-outter-loop-workflow.png)

**Obrázek 5-1**. DevOps pracovní postup vnější smyčky pro aplikace Docker s nástroji Microsoftu

Teď podívejme každý z těchto kroků podrobněji.

## <a name="step-1-inner-loop-development-workflow"></a>Krok 1: pracovní postup vývoje vnitřních smyček

Tento krok je podrobně vysvětlen v kapitole 4, ale do rekapitulace, kde začíná vnější smyčka, okamžik, kdy vývojář vloží kód do systému správy zdrojového kódu (jako je git) iniciující akce kanálu CI.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>Krok 2: integrace a Správa řízení zdrojového kódu pomocí Azure DevOps Services a Gitu

V tomto kroku je potřeba mít systém pro správu verzí, který bude shromažďovat konsolidovanou verzi veškerého kódu, který přichází od různých vývojářů v týmu.

I když se Správa zdrojového kódu (SCC) a Správa zdrojového kódu může zdát druhým prvkem pro většinu vývojářů, při vytváření aplikací Docker v životním cyklu DevOps je důležité zdůraznit, že nesmíte odeslat image Docker do aplikace přímo do globálního registru Docker (jako je Azure Container Registry nebo Docker Hub) z počítače vývojáře. V opačném případě musí být image Docker vydané a nasazené do produkčního prostředí vytvořené výhradně na zdrojovém kódu, který je integrován do globálního kanálu sestavení nebo CI na základě vašeho úložiště zdrojového kódu (jako je git).

Místní image generované vývojáři by je měli používat jenom při testování v rámci svých vlastních počítačů. Proto je důležité mít DevOps kanál aktivovaný z SCC kódu.

Azure DevOps Services a Team Foundation Server podporují Git a Správa verzí Team Foundation. Mezi nimi si můžete vybrat a použít ho pro komplexní prostředí Microsoftu. Můžete ale také spravovat kód v externích úložištích (jako jsou GitHub, místní úložiště Git nebo podverze) a pořád se k němu připojit a získat kód jako výchozí bod pro kanál DevOps CI.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>Krok 3: sestavení, CI, integrace a testování pomocí Azure DevOps Services a Docker

CI se ukázalo jako standard pro moderní testování a doručování softwaru. Řešení Docker udržuje jasné oddělení otázek mezi vývojovými a provozními týmy. Neměnnosti imagí Docker zajišťuje opakované nasazení mezi vyvíjeným, testovaným prostřednictvím CI a spuštěným v produkčním prostředí. Modul Docker nasazený v notebookích pro vývojáře a testovací infrastruktura zajišťuje přenos kontejnerů napříč prostředími.

V tomto okamžiku, poté, co máte systém pro správu verzí se správným kódem, budete potřebovat *sestavovací službu* pro výběr kódu a spuštění globálních sestavení a testů.

Interní pracovní postup pro tento krok (CI, Build, test) se týká konstrukce kanálu CI, který se skládá z vašeho úložiště kódu (Git atd.), serveru sestavení (Azure DevOps Services), Docker Engine a registru Docker.

Azure DevOps Services můžete použít jako základ pro sestavování aplikací a nastavení kanálu CI a pro publikování vestavěných artefaktů do úložiště artefaktů, které je vysvětleno v dalším kroku.

Při použití Docker pro nasazení jsou konečné artefakty, které se mají nasadit, image Docker s vaší aplikací nebo službami, které jsou v nich vložené. Tyto image se odešlou nebo publikují do *registru Docker* (soukromé úložiště, jako jsou ty, které můžete mít v Azure Container Registry, nebo veřejný, jako je registr Docker Hub, který se běžně používá pro oficiální základní image).

Tady je základní pojem: kanál CI se spustí potvrzením změn do úložiště SCC, jako je třeba Git. Potvrzení způsobí, že Azure DevOps Services spustí úlohu sestavení v kontejneru Docker a po úspěšném dokončení této úlohy nahrajte image Docker do registru Docker, jak je znázorněno na obrázku 5-2. První část vnější smyčky zahrnuje kroky 1 až 3, od kódu, Run, Debug a Validate a pak se kód naplní do kroku sestavení a testování CI.

![Diagram znázorňující tři kroky, které jsou součástí pracovního postupu CI.](./media/docker-application-outer-loop-devops-workflow/continuous-integration-steps.png)

**Obrázek 5-2**. Postup, který je součástí CI

Zde jsou základní kroky pracovního postupu CI s použitím Docker a Azure DevOps Services:

1. Vývojář nahraje potvrzení do úložiště SCC (Git/Azure DevOps Services, GitHub atd.).

2. Pokud používáte Azure DevOps Services nebo Git, je CI integrovaná, což znamená, že je to jednoduché jako zaškrtnutí políčka v Azure DevOps Services. Pokud používáte externí SCC (například GitHub), `webhook` bude oznámení Azure DevOps Services aktualizace nebo nabízení do Gitu/GitHubu.

3. Azure DevOps Services vyžádá úložiště SCC, včetně souboru Dockerfile popisujícího obrázek, a také aplikace a testovací kód.

4. Azure DevOps Services vytvoří obrázek Docker a označí ho číslem sestavení.

5. Azure DevOps Services vytvoří instanci kontejneru Docker v rámci zřízeného hostitele Docker a spustí příslušné testy.

6. Pokud jsou testy úspěšné, obrázek je nejprve přepsán na smysluplný název, abyste věděli, že se jedná o "spokojeni sestavení" (například "/1.0.0" nebo jakýkoli jiný popisek), a pak se přihlásili do registru Docker (Docker Hub, Azure Container Registry, DTR atd.).

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Implementace kanálu CI pomocí Azure DevOps Services a rozšíření Docker pro Azure DevOps Services

Visual Studio Azure DevOps Services obsahuje šablony verzí Build &, které můžete použít v kanálu CI/CD, pomocí kterých můžete vytvářet image Docker, image Docker do ověřeného registru Docker, spouštět image Docker nebo spouštět jiné operace nabízené rozhraním Docker CLI. Přidá taky Docker Compose úkol, který můžete použít k sestavení, vložení a spuštění aplikací Docker pro více kontejnerů, nebo spuštění jiných operací, které nabízí Docker Compose CLI, jak je znázorněno na obrázku 5-3.

![Snímek obrazovky s kanálem služby Docker CI v Azure DevOps.](./media/docker-application-outer-loop-devops-workflow/docker-ci-pipeline-azure-devops.png)

**Obrázek 5-3**. Kanál položky konfigurace Docker v Azure DevOps Services včetně šablon verzí Build & a přidružených úloh.

Tyto šablony a úlohy můžete použít k vytvoření a otestování artefaktů CI/CD pro sestavování, testování a nasazení v Azure Service Fabric, službě Azure Kubernetes a podobných nabídek.

Pomocí těchto úloh Visual Studio Team Services, hostitele nebo virtuálního počítače se systémem Linux, který jste zřídili v Azure, a preferovaného registru Docker (Azure Container Registry, Docker Hub, privátního Docker DTR nebo jakéhokoli jiného registru Docker), můžete kanál CI Docker sestavit velmi konzistentně.

***Požadavků***

- Azure DevOps Services nebo pro místní instalace Team Foundation Server 2015 Update 3 nebo novější.

- Agent Azure DevOps Services, který obsahuje binární soubory Docker.

  Jednoduchý způsob, jak vytvořit jednoho z těchto agentů, je použít Docker ke spuštění kontejneru založeného na imagi Azure DevOps Services agenta Docker.

> [! INFORMACE] Pokud si chcete přečíst další informace o sestavení kanálu CI Azure DevOps Services Docker CI a Prohlédněte si návody, navštivte tyto weby:
>
> - Spuštění agenta Visual Studio Team Services (nyní Azure DevOps Services) jako kontejneru Docker: \
>   <https://hub.docker.com/_/microsoft-azure-pipelines-vsts-agent>
>
> - Sestavování imagí Docker platformy .NET Core Linux pomocí Azure DevOps Services: \
>   <https://docs.microsoft.com/archive/blogs/stevelasker/building-net-core-linux-docker-images-with-visual-studio-team-services>
>
> - Sestavování počítače se systémem Linux Visual Studio Team Service s podporou Docker: \
>   <https://www.donovanbrown.com/post/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>Integrace, testování a ověřování aplikací Docker pro více kontejnerů

Většinou se většina aplikací Docker skládá z několika kontejnerů, nikoli z jednoho kontejneru. Dobrým příkladem jsou aplikace orientované na mikroslužby, pro které byste měli jeden kontejner na mikroslužbu. Ale i bez naprosto podle vzorů přístupu k mikroslužbám je pravděpodobné, že se vaše aplikace Docker skládá z několika kontejnerů nebo služeb.

Proto je po sestavení kontejnerů aplikací v kanálu CI také nutné nasadit, integrovat a testovat aplikaci jako celek se všemi jeho kontejnery v rámci hostitele Docker Integration nebo i do testovacího clusteru, do nějž jsou kontejnery distribuovány.

Pokud používáte jednoho hostitele, můžete k sestavení a nasazení souvisejících kontejnerů použít příkazy Docker, jako je Docker-Build, a otestovat a ověřit prostředí Docker v jednom virtuálním počítači. Pokud ale pracujete s clusterem Orchestrator, jako je DC/OS, Kubernetes nebo Docker Swarm, budete muset své kontejnery nasadit pomocí jiného mechanismu nebo Orchestrator v závislosti na vybraném clusteru nebo plánovači.

Níže je několik typů testů, které lze spustit proti kontejnerům Docker:

- Testování částí kontejnerů Docker

- Testování skupin vzájemně souvisejících aplikací nebo mikroslužeb

- Testování v produkčním prostředí a "Kanárských" vydání

Důležité je, aby při spuštění integračních a funkčních testů bylo nutné spustit tyto testy mimo kontejnery. Testy nejsou obsaženy v kontejnerech, které nasazujete, ani je nespouštějte, protože kontejnery jsou založené na statických imagích, které by měly být přesně stejné jako ty, které nasazujete do produkčního prostředí.

Praktická možnost při testování pokročilejších scénářů, například zahrnující několik clusterů (testovací cluster, přípravný cluster a provozní cluster), je publikování imagí do registru, takže se dá testovat v různých clusterech.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Vložení vlastní image Docker aplikace do globálního registru Docker

Po otestování a ověření imagí Docker budete chtít označit a publikovat v registru Docker. Registr Docker je kritickým kamenem v životním cyklu aplikace Docker, protože se jedná o centrální místo, kam svůj vlastní test uložíte (označovaný také jako "ty, které se označují jako" určitě "), aby se nasadil do prostředí pro kontrolu a kontrolu a provoz.

Podobně jako v případě, že je kód aplikace uložený v úložišti SCC (Git atd.) vaším zdrojem pravdy, je registr Docker vaším zdrojem pravdy, aby se vaše binární aplikace nebo bity nasadily do prostředí pro QA nebo do produkčního prostředí.

Obvykle můžete chtít, aby vaše osobní úložiště pro vlastní image buď v privátním úložišti v Azure Container Registry, nebo v místním registru, jako je Docker Trusted Registry, nebo ve veřejném cloudu s omezeným přístupem (jako je Docker Hub), i když v tomto posledním případě není kód open source, musíte důvěřovat zabezpečení od dodavatele. V obou případech je použitá metoda podobná a je založena na `docker push` příkazu, jak je znázorněno na obrázku 5-4.

![Diagram znázorňující vložení vlastních imagí do registru kontejneru.](./media/docker-application-outer-loop-devops-workflow/docker-push-custom-images.png)

**Obrázek 5-4**. Publikování vlastních imagí do registru Docker

V kroku 3 se při vytváření integrace a testování (CI) můžou výsledné image Docker publikovat do privátního nebo veřejného registru. Existuje několik nabídek registrů Docker od dodavatelů cloudu, jako jsou Azure Container Registry, Amazon Web Services Container Registry, Google Container Registry, Registry Quay a tak dále.

Pomocí úloh Docker můžete odeslat sadu imagí služby definovaných `docker-compose.yml` souborem s více značkami do ověřeného registru Docker (například Azure Container Registry), jak je znázorněno na obrázku 5-5.

![Snímek obrazovky znázorňující krok publikování imagí do registru.](./media/docker-application-outer-loop-devops-workflow/publish-custom-image-to-docker-registry.png)

**Obrázek 5-5**. Použití Azure DevOps Services k publikování vlastních imagí do registru Docker

> [! INFORMACE] Další informace o Azure Container Registry najdete v tématu <https://aka.ms/azurecontainerregistry> .

## <a name="step-4-cd-deploy"></a>Krok 4: CD, nasazení

Neměnnosti imagí Docker zajišťuje opakované nasazení s tím, co se vyvíjí, testuje prostřednictvím CI a běží v produkčním prostředí. Jakmile budete mít image Docker aplikace publikované v registru Docker (buď privátní, nebo veřejné), můžete je nasadit do několika prostředí, která máte (v produkčním prostředí, QA, fázování atd.) z kanálu CD pomocí Azure DevOps Services úloh kanálu nebo Azure DevOps Services Release Management.

V tuto chvíli ale záleží na tom, jaký druh aplikace Docker nasazujete. Nasazení jednoduché aplikace (ze kompozice a bodu nasazení), jako je monolitické aplikace skládající se z několika kontejnerů nebo služeb a nasazených na několik serverů nebo virtuálních počítačů, se liší od nasazení složitější aplikace, jako je aplikace orientovaná na mikroslužby s možností škálování na více systémů. Tyto dva scénáře jsou vysvětleny v následujících částech.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Nasazení složených aplikací Docker do více prostředí Docker

Pojďme se nejdřív podívat na méně složitý scénář: nasazení do jednoduchých hostitelů Docker (virtuálních počítačů nebo serverů) v jednom prostředí nebo několika prostředích (QA, fázování a produkce). V tomto scénáři může interní kanál CD použít k nasazení aplikací Docker (na základě úloh nasazení Azure DevOps Services Docker) k nasazení aplikací Docker se související sadou kontejnerů nebo služeb, jak je znázorněno na obrázku 5-6.

![Diagram znázorňující krok nasazení disku CD nasazení do tří prostředí.](./media/docker-application-outer-loop-devops-workflow/deploy-app-containers-to-docker-host-environments.png)

**Obrázek 5-6**. Nasazení kontejnerů aplikací do registru jednoduchých hostitelských prostředí Docker

Obrázek 5-7 vysvětlete, jak můžete pomocí Azure DevOps Services připojit CI sestavení do prostředí pro kontrolu a testování prostřednictvím kliknutím na Docker Compose v dialogovém okně Přidat úlohu. Při nasazení do pracovních nebo produkčních prostředí byste ale obvykle použili Release Management funkcí zpracovávajících více prostředí (například QA, fázování a produkce). Pokud nasazujete na hostitele s jedním Docker, používá úlohu Azure DevOps Services "Docker Compose" (což vyvolává `docker-compose up` příkaz v digestoři). Pokud provádíte nasazení do služby Azure Kubernetes Service (AKS), používá úlohu nasazení Docker, jak je vysvětleno v následující části.

![Snímek obrazovky s dialogem přidat úkoly úlohy Docker Compose](./media/docker-application-outer-loop-devops-workflow/add-tasks-docker-compose.png)

**Obrázek 5-7**. Přidání úkolu Docker Compose do kanálu Azure DevOps Services

Když vytvoříte vydání v Azure DevOps Services, převezme sadu vstupních artefaktů. Tyto artefakty mají být neměnné po dobu života vydaných verzí napříč všemi prostředími. Při zavedení kontejnerů vstupní artefakty identifikují image v registru k nasazení. V závislosti na tom, jak se tyto image identifikují, není zaručeno, že zůstanou stejné po celou dobu trvání vydané verze, Nejčastějším případem, kdy se bude odkazovat `myimage:latest` ze `docker-compose` souboru.

Šablony Azure DevOps Services umožňují generovat artefakty sestavení, které obsahují konkrétní výtahy imagí registru, které mají zaručit jedinečnou identifikaci stejného binárního souboru bitové kopie. To je to, co opravdu chcete použít jako vstup do vydání.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Správa verzí do prostředí Docker pomocí Azure DevOps Services Release Management

Prostřednictvím šablon Azure DevOps Services můžete vytvořit novou image, publikovat ji v registru Docker, spustit ji na hostitelích se systémem Linux nebo Windows a použít příkazy, jako je například `docker-compose` nasazení více kontejnerů jako celé aplikace, a to vše prostřednictvím Azure DevOps Services Release Management možností, které jsou určeny pro více prostředí, jak je znázorněno na obrázku 5-8.

![Snímek obrazovky s konfigurací verzí pro sestavení Docker](./media/docker-application-outer-loop-devops-workflow/configure-docker-compose-release.png)

**Obrázek 5-8**. Konfigurace úloh Azure DevOps Services Docker Compose z Azure DevOps Services Release Management

Mějte ale na paměti, že scénář uvedený na obrázku 5-6 a implementovaný na obrázku 5-8 je jednoduchý (nasazuje se do jednoho hostitele Docker a virtuálních počítačů) a bude se pravděpodobně používat jenom pro scénáře vývoje nebo testování. Ve většině podnikových produkčních scénářů byste měli mít vysokou dostupnost (HA) a snadno spravovatelnou škálovatelnost vyrovnáváním zatížení napříč několika uzly, servery a virtuálními počítači, a navíc "inteligentní převzetí služeb při selhání", takže pokud se server nebo uzel nezdaří, jeho služby a kontejnery se přesunou na jiný hostitelský server nebo virtuální počítač. V takovém případě budete potřebovat pokročilejší technologie, jako jsou clustery kontejnerů, Orchestrace a plánovače. Proto je způsob, jak nasadit do těchto clusterů, nacházet pomocí pokročilých scénářů, které jsou vysvětleny v následující části.

### <a name="deploying-docker-applications-to-docker-clusters"></a>Nasazení aplikací Docker do clusterů Docker

Povaha distribuovaných aplikací vyžaduje také distribuované výpočetní prostředky. Aby bylo možné využívat možnosti produkčního prostředí, musíte mít funkce clusteringu, které poskytují vysokou škálovatelnost a vysokou dostupnost na základě prostředků ve fondu.

Kontejnery můžete do těchto clusterů nasadit ručně z nástroje CLI nebo z webového uživatelského rozhraní, ale měli byste si vyhradit tento druh ruční práce pro přímé testování nasazení nebo pro účely správy, jako je například škálování nebo monitorování.

Z místa na disku CD-ROM a Azure DevOps Services konkrétně můžete spouštět speciálně vytvořené úlohy nasazení z Azure DevOps Services Release Management prostředích, která budou nasazovat vaše kontejnerové aplikace do distribuovaných clusterů ve službě Container Service, jak je znázorněno na obrázku 5-9.

![Diagram znázorňující krok nasazení disku CD nasazení do orchestrace.](./media/docker-application-outer-loop-devops-workflow/cd-deploy-to-orchestrators.png)

**Obrázek 5-9**. Nasazení distribuovaných aplikací do služby kontejneru

Zpočátku byste při nasazení na určité clustery nebo orchestraci použili konkrétní skripty pro nasazení a mechanismy pro každý Orchestrator (tj. Kubernetes a Service Fabric mají různé mechanismy nasazení) místo jednoduššího a snadno použitelného `docker-compose` nástroje založeného na `docker-compose.yml` definičním souboru. Díky tomu, že se jedná o úlohu Azure DevOps Services Docker Deploy, která je znázorněna na obrázku 5-10, teď můžete nasadit i na podporované orchestrace jenom pomocí známého `docker-compose.yml` souboru, protože tento nástroj pro vás (ze `docker-compose.yml` souboru do formátu potřebného pro Orchestrator) provede překlad.

![Snímek obrazovky znázorňující úlohu nasazení do Kubernetes](./media/docker-application-outer-loop-devops-workflow/add-deploy-to-kubernetes-task.png)

**Obrázek 5-10**. Přidání úlohy nasazení do vašeho prostředí Kubernetes

Obrázek 5-11 ukazuje, jak můžete upravit úlohu nasazení na Kubernetes s oddíly dostupnými pro konfiguraci. Je to úkol, který načte připravené vlastní image Docker, které se mají nasadit jako kontejnery v clusteru.

![Snímek obrazovky s konfigurací úlohy nasazení do Kubernetes](./media/docker-application-outer-loop-devops-workflow/edit-deploy-to-kubernetes-task.png)

**Obrázek 5-11**. Nasazení definice úlohy Docker nasazení do služby ACS DC/OS

> [! INFORMACE] Pokud chcete získat další informace o kanálu CD pomocí Azure DevOps Services a Docker, navštivte <https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>Krok 5: spuštění a Správa

Vzhledem k tomu, že spouštění a Správa aplikací na úrovni podniku v produkčním prostředí je zásadním subjektem a v závislosti na typu operací a lidí pracujících na této úrovni (operace IT) a také v rozsáhlém rozsahu této oblasti, je k objasnění celé další kapitoly věnována celá další kapitola.

## <a name="step-6-monitor-and-diagnose"></a>Krok 6: monitorování a diagnostika

Toto téma je také popsáno v další kapitole v rámci úloh, které provádí v produkčních systémech. je ale důležité zdůraznit, že přehledy získané v tomto kroku musí předávat zpět do vývojového týmu, aby se aplikace neustále vylepšila. Z tohoto pohledu je také součástí DevOps, i když se úlohy a operace obvykle provádějí.

Pouze v případě, že jsou monitorování a diagnostika 100% v rámci sféry DevOps, jsou procesy monitorování a analýzy prováděné vývojovým týmem proti testování nebo beta prostředí. To se provádí buď zátěžovým testováním, nebo monitorováním prostředí verze beta nebo QA, kde testeri beta verzí zkouší nové verze.

>[!div class="step-by-step"]
>[Předchozí](index.md) 
> [Další](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
