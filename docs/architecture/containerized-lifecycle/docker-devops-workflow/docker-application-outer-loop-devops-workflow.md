---
title: Kroky ve vývoji DevOps vnější smyčky pro aplikaci Dockeru
description: Naučte se kroky pro "vnější smyčku" pracovního postupu DevOps
ms.date: 02/15/2019
ms.openlocfilehash: 44bd73bf88a743e5350e422d3ea000ca075f7383
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "82021290"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Kroky ve vývoji DevOps vnější smyčky pro aplikaci Dockeru

Obrázek 5-1 představuje end-to-end zobrazení kroků, které tvoří Pracovní postup devOps vnější smyčky. Zobrazuje "vnější smyčku" DevOps. Při přepnutí kódu do repo, je spuštěn kanál CI, pak začne kanál CD, kde se aplikace nasadí. Metriky shromážděné z nasazených aplikací jsou vráceny zpět do úlohy vývoje, kde dochází k "vnitřní smyčce", takže vývojové týmy mají skutečná data, která reagují na potřeby uživatelů a podniků.

![Diagram znázorňující 6 kroků pracovního postupu devOps vnější smyčky.](./media/docker-application-outer-loop-devops-workflow/overview-dev-ops-outter-loop-workflow.png)

**Obrázek 5-1**. Pracovní postup DevOps s vnější smyčkou pro aplikace Dockeru s nástroji Microsoftu

Nyní se podívejme na každý z těchto kroků podrobněji.

## <a name="step-1-inner-loop-development-workflow"></a>Krok 1: Pracovní postup vývoje vnitřní smyčky

Tento krok je podrobně vysvětlen v kapitole 4, ale pro rekapitulaci, zde je místo, kde začíná vnější smyčka, okamžik, kdy vývojář odešle kód do systému správy správy zdrojového kódu (jako je Git) inicializační akce kanálu CI.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>Krok 2: Integrace a správa správy zdrojového kódu se službami Azure DevOps services a Git

V tomto kroku musíte mít systém správy verzí shromáždit konsolidovanou verzi všech kódů pocházejících z různých vývojářů v týmu.

I když řízení zdrojového kódu (SCC) a správa zdrojového kódu se může zdát druhé povahy pro většinu vývojářů, při vytváření aplikací Dockeru v životním cyklu DevOps, je důležité zdůraznit, že nesmíte odesílat ibližování Dockeru s aplikací přímo do globálního registru Dockeru (jako je Azure Container Registry nebo Docker Hub) z počítače vývojáře. Naopak image Dockeru, které mají být uvolněny a nasazeny do produkčního prostředí, musí být vytvořeny výhradně na zdrojovém kódu, který je integrován do globálního sestavení nebo kanálu CI na základě úložiště zdrojového kódu (například Git).

Místní bitové kopie, generované vývojáři, by měly být používány pouze jimi při testování v rámci svých vlastních počítačů. To je důvod, proč je důležité mít kanál DevOps aktivován z kódu SCC.

Služby Azure DevOps services a team foundation server podporují git a řízení verzí Team Foundation. Můžete si mezi nimi vybrat a použít je pro komplexní prostředí microsoftu. Můžete však také spravovat kód v externích úložištích (jako je GitHub, místní úložiště Git nebo Subversion) a stále můžete se k němu připojit a získat kód jako výchozí bod pro kanál DevOps CI.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>Krok 3: Sestavení, vytváření, integrace a testování se službami Azure DevOps a Dockerem

CI se objevil jako standard pro moderní testování a dodávku softwaru. Řešení Docker udržuje jasné oddělení problémů mezi vývojovými a provozními týmy. Neměnnost iobrazek Dockeru zajišťuje opakovatelné nasazení mezi tím, co je vyvinuto, testováno prostřednictvím CI a spuštěno v produkčním prostředí. Docker Engine nasazený napříč vývojářskými notebooky a testovací infrastrukturou činí kontejnery přenosnými napříč prostředími.

V tomto okamžiku poté, co máte systém správy verzí se správným kódem odeslány, budete potřebovat *sestavení služby* vyzvednout kód a spustit globální sestavení a testy.

Interní pracovní postup pro tento krok (CI, sestavení, test) je o konstrukci kanálu CI skládající se z úložiště kódu (Git, atd.), serveru sestavení (Azure DevOps Services), Docker Engine a registru Dockeru.

Služby Azure DevOps Services můžete použít jako základ pro vytváření aplikací a nastavení kanálu CI a pro publikování vytvořených "artefaktů" do "úložiště artefaktů", což je vysvětleno v dalším kroku.

Při použití Dockeru pro nasazení jsou "konečné artefakty", které mají být nasazeny, iimage Dockeru s vaší aplikací nebo službami vloženými do nich. Tyto image se odesazují nebo publikují do *registru Dockeru* (privátní úložiště, jako jsou ty, které můžete mít v Azure Container Registry, nebo veřejné, jako je Docker Hub Registry, který se běžně používá pro oficiální základní image).

Zde je základní koncept: Kanál CI bude vykopnut potvrzením úložiště SCC, jako je Git. Potvrzení způsobí, že Služby Azure DevOps spustí úlohu sestavení v kontejneru Dockeru a po úspěšném dokončení této úlohy posunou image Dockeru do registru Dockeru, jak je znázorněno na obrázku 5-2. První část vnější smyčky zahrnuje kroky 1 až 3, z kódu, spustit, ladit a ověřit, pak kód repo až sestavení a test CI krok.

![Diagram znázorňující tři kroky související s pracovním postupem CI.](./media/docker-application-outer-loop-devops-workflow/continuous-integration-steps.png)

**Obrázek 5-2**. Kroky spojené s ci

Tady jsou základní kroky pracovního postupu CI s Dockerem a Službami Azure DevOps:

1. Vývojář odešle potvrzení do úložiště SCC (Git/Azure DevOps Services, GitHub atd.).

2. Pokud používáte Služby Azure DevOps nebo Git, je integrovaná ci, což znamená, že je stejně jednoduché jako zaškrtnutí políčka ve službách Azure DevOps. Pokud používáte externí SCC (jako Je `webhook` GitHub), a upozorní Služby Azure DevOps na aktualizaci nebo push na Git/GitHub.

3. Azure DevOps Services vytáhne úložiště SCC, včetně Dockerfile popisující image, stejně jako aplikace a testovací kód.

4. Azure DevOps Services vytvoří image Dockeru a označí ji číslem sestavení.

5. Azure DevOps Services instanci kontejneru Dockeru v rámci zřízeného hostitele Dockeru a spustí příslušné testy.

6. Pokud jsou testy úspěšné, bitová kopie se nejprve přeznačí na smysluplný název, abyste věděli, že se jedná o "požehnané sestavení" (například "/1.0.0" nebo jakýkoli jiný popisek) a poté se posune do registru Docker (Docker Hub, Azure Container Registry, DTR atd.)

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Implementace kanálu CI pomocí služeb Azure DevOps Services a rozšíření Dockeru pro služby Azure DevOps Services

Visual Studio Azure DevOps Services obsahuje šablony build & release, které můžete použít ve vašem kanálu CI/CD, se kterými můžete vytvářet ibi Dockeru, přesouvat ibi Dockeru do ověřeného registru Dockeru, spouštět ibi Dockeru nebo spouštět další operace nabízené cli Dockeru. Přidá také úlohu Docker Compose, kterou můžete použít k vytváření, nabízení a spouštění vícekontejnerových aplikací Dockeru nebo ke spuštění jiných operací nabízených cli zásobníku Dockercomse, jak je znázorněno na obrázku 5-3.

![Snímek obrazovky kanálu Docker CI v Azure DevOps.](./media/docker-application-outer-loop-devops-workflow/docker-ci-pipeline-azure-devops.png)

**Obrázek 5-3**. Kanál Docker CI ve službách Azure DevOps, včetně šablon build & release a přidružených úloh.

Tyto šablony a úkoly můžete použít k vytvoření artefaktů CI/CD pro sestavení nebo testování a nasazení ve službě Azure Service Fabric, službě Azure Kubernetes a podobných nabídkách.

S těmito úlohami Visual Studio Team Services, sestavení Linux-Docker Host/VM zřízené v Azure a upřednostňovaný registr Dockeru (Azure Container Registry, Docker Hub, privátní Docker DTR nebo jakýkoli jiný registr Dockeru) můžete sestavit kanál IKTo u a konzistentně.

***Požadavky:***

- Azure DevOps Services nebo pro místní instalace, Team Foundation Server 2015 Update 3 nebo novější.

- Agent služby Azure DevOps Services, který má binární soubory Dockeru.

  Snadný způsob, jak vytvořit jednoho z těchto agentů, je použití Dockeru ke spuštění kontejneru na základě image dockeru agenta Služby Azure DevOps.

> [! INFORMACE] Další informace o sestavení kanálu Azure DevOps Services Docker CI a zobrazení návodů najdete na těchto webech:
>
> - Spuštění agenta služby Visual Studio Team Services (Now Azure DevOps Services) jako kontejneru Dockeru: \
>   <https://hub.docker.com/_/microsoft-azure-pipelines-vsts-agent>
>
> - Vytváření bitových kopií Linux dockeru .NET Core pomocí služeb Azure DevOps: \
>   <https://docs.microsoft.com/archive/blogs/stevelasker/building-net-core-linux-docker-images-with-visual-studio-team-services>
>
> - Vytváření počítače pro sestavení služby Visual Studio Team Service založené na Linuxu s podporou Dockeru: \
>   <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>Integrace, testování a ověřování aplikací Dockeru s více kontejnery

Většina aplikací Dockeru se obvykle skládá z více kontejnerů, nikoli z jednoho kontejneru. Dobrým příkladem je aplikace orientovaná na mikroslužby, pro kterou byste měli jeden kontejner na mikroslužbu. Ale i bez přísné dodržování vzorců přístupu mikroslužeb je pravděpodobné, že vaše aplikace Dockeru by se skládala z více kontejnerů nebo služeb.

Proto po sestavení kontejnerů aplikace v kanálu CI, je také nutné nasadit, integrovat a otestovat aplikaci jako celek se všemi jeho kontejnery v rámci integrace hostitele Dockeru nebo dokonce do testovacího clusteru, do kterého jsou distribuovány vaše kontejnery.

Pokud používáte jednoho hostitele, můžete použít příkazy Dockeru, jako je docker-compose k sestavení a nasazení souvisejících kontejnerů k testování a ověřování prostředí Dockeru v jednom virtuálním provozu. Ale pokud pracujete s clusteru orchestrator, jako je DC/OS, Kubernetes nebo Docker Swarm, musíte nasadit kontejnery prostřednictvím jiného mechanismu nebo orchestrátoru, v závislosti na vybraném clusteru nebo plánovače.

Následuje několik typů testů, které můžete spustit proti kontejnery Dockeru:

- Jednotkové testy pro kontejnery Dockeru

- Testovací skupiny vzájemně propojených aplikací nebo mikroslužeb

- Zkouška ve výrobě a "kanárské" verze

Důležité je, že při spuštění integrace a funkční testy, je nutné spustit tyto testy z mimo kontejnery. Testy nejsou obsaženy nebo spustit v kontejnerech, které nasazujete, protože kontejnery jsou založeny na statické image, které by měly být přesně jako ty, které budete nasazovat do produkčního prostředí.

Praktickou možností při testování pokročilejších scénářů, jako je včetně několika clusterů (testovací cluster, pracovní cluster a produkční cluster) je publikovat bitové kopie do registru, aby mohly být testovány v různých clusterech.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Zasunutí image Dockeru vlastní aplikace do globálního registru Dockeru

Po otestování a ověření ibitých bitových kopií Dockeru je budete chtít označit a publikovat do registru Dockeru. Registr Dockeru je kritický mj.

Podobně jako kód aplikace uložený ve vašem úložišti SCC (Git, atd.) je vaším "zdrojem pravdy", registr Dockeru je vaším "zdrojem pravdy" pro binární aplikaci nebo bity, které mají být nasazeny do qa nebo produkčního prostředí.

Obvykle můžete chtít mít privátní úložiště pro vlastní image buď v soukromém úložišti v registru kontejnerů Azure nebo v místním registru, jako je Důvěryhodný registr Dockeru, nebo v registru veřejného cloudu s omezeným přístupem (jako je Docker Hub), i když v tomto posledním případě, pokud váš kód není open source, musíte důvěřovat zabezpečení dodavatele. Ať tak či onak, metoda, `docker push` kterou používáte, je podobná a je založena na příkazu, jak je znázorněno na obrázku 5-4.

![Diagram znázorňující nabízení vlastních irek do registru kontejnerů.](./media/docker-application-outer-loop-devops-workflow/docker-push-custom-images.png)

**Obrázek 5-4**. Publikování vlastních iobrazů do registru Dockeru

V kroku 3 pro vytváření integrace a testování (CI) můžete publikovat výsledné image dockeru do soukromého nebo veřejného registru. Existuje několik nabídek registrů Dockeru od dodavatelů cloudu, jako je Azure Container Registry, Amazon Web Services Container Registry, Google Container Registry, Quay Registry a tak dále.

Pomocí úloh Dockeru můžete nabízenou sadu ibi `docker-compose.yml` služeb definované souborem s více značkami do ověřeného registru Dockeru (jako je Azure Container Registry), jak je znázorněno na obrázku 5-5.

![Snímek obrazovky s krokem publikování obrázků do registru](./media/docker-application-outer-loop-devops-workflow/publish-custom-image-to-docker-registry.png)

**Obrázek 5-5**. Použití služeb Azure DevOps services k publikování vlastních ibi v registru Dockeru

> [! INFORMACE] Další informace o registru <https://aka.ms/azurecontainerregistry>kontejnerů Azure naleznete v tématu .

## <a name="step-4-cd-deploy"></a>Krok 4: CD, nasazení

Neměnnost iobrazek Dockeru zajišťuje opakovatelné nasazení s tím, co je vyvinuto, testováno prostřednictvím CI a spuštěno v produkčním prostředí. Po publikování iontů Dockeru aplikace v registru Dockeru (privátní nebo veřejné) je můžete nasadit do několika prostředí, která můžete mít (produkční, qa, staging atd.) z kanálu CD pomocí úloh kanálu Azure DevOps Services nebo Azure DevOps Services Release Management.

V tomto okamžiku však závisí na tom, jaký druh aplikace Dockeru nasazujete. Nasazení jednoduché aplikace (z hlediska složení a nasazení) jako monolitické aplikace zahrnující několik kontejnerů nebo služeb a nasazené na několik serverů nebo virtuálních počítačích se liší od nasazení složitější aplikace, jako je aplikace orientovaná na mikroslužby s možnostmi hyperškálování. Tyto dva scénáře jsou vysvětleny v následujících částech.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Nasazení komponujících aplikací Dockeru do více prostředí Dockeru

Podívejme se nejprve na méně složitý scénář: nasazení na jednoduché hostitele Dockeru (virtuální počítače nebo servery) v jednom prostředí nebo ve více prostředích (QA, staging a production). V tomto scénáři interně kanál CD můžete použít docker-compose (z úlohnasazení Azure DevOps Services) k nasazení aplikací Dockeru s jeho související sadu kontejnerů nebo služeb, jak je znázorněno na obrázku 5-6.

![Diagram znázorňující krok nasazení disku CD-ROM ve třech prostředích.](./media/docker-application-outer-loop-devops-workflow/deploy-app-containers-to-docker-host-environments.png)

**Obrázek 5-6**. Nasazení kontejnerů aplikací do jednoduchého registru hostitelských prostředí Dockeru

Obrázek 5-7 zvýrazní, jak můžete připojit vaše sestavení CI qa/testovací prostředí prostřednictvím služby Azure DevOps kliknutím na Docker Compose v dialogovém okně Přidat úlohu. Při nasazování do pracovního nebo produkčního prostředí byste však obvykle používali funkce správy verzí, které by zpracovávaly více prostředí (jako je qa, pracovní a produkční). Pokud nasazujete do jednoho hostitele Dockeru, používá se pomocí úlohy Azure DevOps Services `docker-compose up` "Docker Compose" (která se odvolává na příkaz pod kapotou). Pokud nasazujete do služby Azure Kubernetes Service (AKS), používá úlohu nasazení Dockeru, jak je vysvětleno v následující části.

![Snímek obrazovky s dialogem Přidat úkol Vytvořit úlohu Dockeru](./media/docker-application-outer-loop-devops-workflow/add-tasks-docker-compose.png)

**Obrázek 5-7**. Přidání úlohy Docker Compose v kanálu služby Azure DevOps Services

Když vytvoříte vydání ve službě Azure DevOps Services, bude mít sadu vstupních artefaktů. Tyto artefakty jsou určeny k neměnné po celou dobu vydání ve všech prostředích. Při zavádění kontejnerů vstupní artefakty identifikovat bitové kopie v registru k nasazení. V závislosti na tom, jak jsou tyto obrázky identifikovány, není zaručeno, že zůstanou stejné po celou dobu trvání vydání, nejzřejmější případ je, když odkazujete `myimage:latest` ze souboru. `docker-compose`

Šablony služby Azure DevOps Services poskytují možnost generovat artefakty sestavení, které obsahují konkrétní knihovny bitových kopii registru, které zaručeně jednoznačně identifikují binární bitovou kopii stejné bitové kopie. To jsou to, co opravdu chcete použít jako vstup do vydání.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Správa verzí do prostředí Dockeru pomocí Azure DevOps Services Release Management

Prostřednictvím šablon Azure DevOps Services můžete vytvořit novou bitovou kopii, publikovat ji do registru Dockeru, `docker-compose` spustit ji na hostitelích Linuxu nebo Windows a použít příkazy, jako je nasazení více kontejnerů jako celé aplikace, a to prostřednictvím funkcí Azure DevOps Services Release Management určených pro více prostředí, jak je znázorněno na obrázku 5-8.

![Snímek obrazovky zobrazující konfiguraci Dockeru tvoří vydání.](./media/docker-application-outer-loop-devops-workflow/configure-docker-compose-release.png)

**Obrázek 5-8**. Konfigurace úloh y Azure DevOps Services Docker Compose ze správy verzí služby Azure DevOps Services

Mějte však na paměti, že scénář znázorněný na obrázku 5-6 a implementovaný na obrázku 5-8 je jednoduchý (nasazuje se do jednoho hostitelů a virtuálních zařízení dockeru a bude existovat jeden kontejner nebo instance na bitovou kopii) a pravděpodobně by měl být použit pouze pro scénáře vývoje nebo testování. Ve většině podnikových produkčních scénářů byste chtěli mít vysokou dostupnost (HA) a snadno spravovat škálovatelnost pomocí vyrovnávání zatížení napříč více uzly, servery a virtuálními počítači a "inteligentní převzetí služeb při selhání", takže pokud server nebo uzel selže, jeho služby a kontejnery budou přesunuty na jiný hostitelský server nebo virtuální počítač. V takovém případě potřebujete pokročilejší technologie, jako jsou clustery kontejnerů, orchestrátory a plánovače. Způsob nasazení do těchto clusterů je tedy zpracováním pokročilých scénářů vysvětlených v další části.

### <a name="deploying-docker-applications-to-docker-clusters"></a>Nasazení aplikací Dockeru do clusterů Dockeru

Povaha distribuovaných aplikací vyžaduje výpočetní prostředky, které jsou také distribuovány. Chcete-li mít možnosti škálování v produkčním prostředí, musíte mít možnosti clusteringu, které poskytují vysokou škálovatelnost a vysokou dostupnost na základě sdružených prostředků.

Kontejnery můžete nasadit ručně do těchto clusterů z nástroje cli nebo webového uživatelského uživatelského okna, ale měli byste si tento druh ruční práce vyhradit na účely testování nebo správy na místě, jako je škálování nebo monitorování.

Z hlediska CD a konkrétně služby Azure DevOps Services můžete spustit speciálně provedené úlohy nasazení z prostředí Azure DevOps Services Release Management, které nasadí kontejnerizované aplikace do distribuovaných clusterů ve službě Container Service, jak je znázorněno na obrázku 5-9.

![Diagram znázorňující krok nasazení disku CD-ROM do orchestrátorů.](./media/docker-application-outer-loop-devops-workflow/cd-deploy-to-orchestrators.png)

**Obrázek 5-9**. Nasazení distribuovaných aplikací do kontejnerové služby

Zpočátku při nasazování do určitých clusterů nebo orchestrátorů byste tradičně používali specifické skripty a mechanismy nasazení na každém orchestrátoru (to znamená Kubernetes a Service Fabric mají různé mechanismy nasazení) namísto jednoduššího a snadno použitelného `docker-compose` nástroje založeného na definičním `docker-compose.yml` souboru. Nicméně díky úlohě Azure DevOps Services Docker Deploy, která je znázorněna na obrázku 5-10, `docker-compose.yml` teď můžete také nasadit do podporovaných `docker-compose.yml` orchestrátorů pomocí známého souboru, protože nástroj provede tento "překlad" za vás (ze souboru do formátu potřebného orchestrátorem).

![Snímek obrazovky s úlohou Nasazení do Kubernetes](./media/docker-application-outer-loop-devops-workflow/add-deploy-to-kubernetes-task.png)

**Obrázek 5-10**. Přidání úlohy Nasazení do Kubernetes do prostředí

Obrázek 5-11 ukazuje, jak můžete upravit úlohu Nasazení do Kubernetes s oddíly, které jsou k dispozici pro konfiguraci. Toto je úloha, která načte vaše vlastní image Dockeru připravené k použití, které se nasazují jako kontejnery v clusteru.

![Snímek obrazovky s konfigurací úlohy Nasazení do Kubernetes](./media/docker-application-outer-loop-devops-workflow/edit-deploy-to-kubernetes-task.png)

**Obrázek 5-11**. Docker nasazení definice úlohy nasazení do Řadič domény a operačního systému ACS

> [! INFORMACE] Další informace o kanálu CD s Azure DevOps Services a Dockerem najdete na<https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>Krok 5: Spuštění a správa

Vzhledem k tomu, že provoz a správa aplikací na úrovni podnikové výroby je sama o sobě hlavním tématem a vzhledem k typu operací a lidem pracujícím na této úrovni (it operace) a velké oblasti působnosti této oblasti je celá další kapitola věnována jeho vysvětlení.

## <a name="step-6-monitor-and-diagnose"></a>Krok 6: Monitorování a diagnostika

Toto téma je také zahrnuto v další kapitole jako součást úkolů, které IT provádí ve výrobních systémech; je však důležité zdůraznit, že přehledy získané v tomto kroku musí být podkladem pro vývojový tým tak, aby aplikace je neustále vylepšována. Z tohoto hlediska je také součástí DevOps, i když úkoly a operace jsou běžně prováděny IT.

Pouze v případě, že monitorování a diagnostika jsou 100 % v rámci devOps jsou procesy monitorování a analýzy prováděné vývojovým týmem proti testování nebo beta prostředí. To se provádí buď provedením zátěžového testování nebo sledováním beta nebo qa prostředí, kde beta testeři zkoušejí nové verze.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
