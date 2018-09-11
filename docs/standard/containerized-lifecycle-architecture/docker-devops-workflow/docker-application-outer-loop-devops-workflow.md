---
title: Kroky v postupu DevOps vnější smyčky pro aplikaci v Dockeru
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/10/2018
ms.openlocfilehash: a03853a508cfb3d5dd5fbfe66e4ef484b685faaa
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339032"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Kroky v postupu DevOps vnější smyčky pro aplikaci v Dockeru

Obrázek 5-1 představuje začátku do konce znázornění postup skládající se z aplikací pracovních postupů DevOps vnější smyčky.

![](./media/image1.png)

Obrázek 5-1: DevOps vnější smyčky pracovní postup pro aplikace Dockeru pomocí nástrojů Microsoftu

Teď se podívejme se na každý z těchto kroků podrobněji.

## <a name="step-1-inner-loop-development-workflow"></a>Krok 1: Pracovní postup vývoje vnitřní smyčky

Tento krok je podrobně popsána v kapitole 4, ale na rekapitulace, tady je kde vnější smyčky začíná, v okamžiku, kdy vývojář vloží kód do systému správy správy zdrojového kódu (např. Git) zahajuje akce kanálu CI.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>Krok 2: Integrace správy zdrojového kódu a správa pomocí služby Azure DevOps a Git

V tomto kroku musíte mít systém správy verzí ke shromáždění konsolidované verzi veškerý kód pocházející z různými vývojáři v týmu.

I když zdát samozřejmostí pro většinu vývojářů, při vytváření aplikací Dockeru v DevOps životního cyklu, správy zdrojového kódu (SCC) a správy zdrojového kódu, je důležité zdůraznit, že nemůže odeslat Image Dockeru s aplikací přímo do globální registru Docker (jako je Azure Container Registry nebo Docker Hubu) z počítače pro vývojáře. Naopak imagí Dockeru do všeobecně dostupné a nasazené do produkčního prostředí musí být vytvořeny výhradně na zdrojový kód, který je integrován v kanálu CI podle vašeho úložiště zdrojového kódu (např. Git) nebo globálního sestavení.

Místní Image generovaných vývojáře sami by měly být používány pouze vývojáři při testování v rámci svých vlastních počítačích. To je důvod, proč je důležité mít aktivovat z kódu SCC kanálu DevOps.

Azure DevOps služby a Team Foundation Server podporují Gitu a Team Foundation Version Control. Můžete zvolit mezi nimi a prostředí, použijte ho začátku do konce Microsoft. Ale také můžete spravovat svůj kód v externích úložištích (např. GitHub, v místním úložišti Git nebo Subversion) a stále se může připojit k němu a získat kód jako výchozí bod pro svůj kanál DevOps CI.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>Krok 3: Sestavení, průběžná integrace, integrace a testování s Azure DevOps služby a Dockeru

Průběžná integrace se stal standardem pro moderní softwaru, testování a doručení. Řešení Dockeru udržuje jasně oddělené oblasti zájmu mezi týmy vývoje a provozu. Neměnnost imagí Dockeru zajišťuje opakovatelné nasazování mezi co vyvíjel, testovat pomocí položek konfigurace a spusťte v produkčním prostředí. Modul docker nasazených na přenosné počítače pro vývojáře a testovací infrastrukturu zpřístupňuje kontejnery přenosné mezi prostředími.

V tomto okamžiku až budete mít systém správy verzí se správným kódem odeslání, musíte *sestavení služby* vyzvednout kód a spouštět globální sestavení a testů.

Informace o vytváření kanálu CI skládající se z vašeho úložiště kódu (Git, atd.), váš server sestavení (Azure DevOps služby), modul Docker a Docker Registry je interní pracovní postup pro tento krok (průběžná integrace, sestavení, testování).

Můžete Azure DevOps Services jako základ pro vytváření aplikací a nastavení kanálu CI a publikování "artefaktů sestavení" na "úložiště artefaktů," který je vysvětlen v dalším kroku.

Při použití Docker pro nasazení "konečné artefakty" nasazení jsou Image Dockeru s aplikací nebo služeb vložené v nich. Tyto Image jsou vloženy nebo publikovanou do *registru Dockeru* (soukromé úložiště jako ty, které můžete mít ve službě Azure Container Registry nebo veřejnou verzi jako registru Docker Hub, která se běžně používá pro oficiální základní Image).

Tady je základní princip: kanál CI bude začaly vypnout potvrzení pro úložiště SCC jako je Git. Potvrzení změn způsobí služby Azure DevOps a spustit úlohu sestavení a v kontejneru Dockeru, po úspěšném dokončení této úlohy, nasdílení image Dockeru do registru Dockeru, jak je znázorněno na obrázku 5-2.

![](./media/image2.png)

Obrázek 5 – 2: potřebnými kroky k CI

Tady jsou základní kroky pracovního postupu CI s využitím Dockeru a Azure DevOps služby:

1.  Vývojář nasdílí potvrzení změn do úložiště SCC (Git/Azure DevOps Services, Githubu, atd.).

2.  Pokud používáte Azure DevOps Services nebo Git, CI je součástí, což znamená, že je stejně jednoduché jako zaškrtnutím políčka ve službách Azure DevOps. Pokud používáte externí SCC (např. GitHub) *webhooku* budou upozornění služby Azure DevOps aktualizace nebo push pro Git/GitHub.

3.  Služby Azure DevOps si vyžádá SCC úložiště, včetně souboru DockerFile popisující bitovou kopii, jakož i kód aplikace a testů.

4.  Služby Azure DevOps vytvoří image Dockeru a označí ji číslem sestavení.

5.  Služby Azure DevOps vytvoří instanci kontejneru Dockeru v rámci zřízené hostitele Docker a spouští příslušné testy.

6.  Pokud jsou testy úspěšné, image je nejprve relabeled na smysluplný název, abyste věděli, je "blessed sestavení" (například "/ 1.0.0" nebo libovolný popisek) a pak nahrány do registru Dockeru (Docker Hub, Azure Container Registry, DTR atd.)

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Implementace kanálu CI pomocí služby Azure DevOps a rozšíření Dockeru pro Azure DevOps služby

[Rozšíření Azure DevOps služby Docker](https://aka.ms/vstsdockerextension) přidá úkol do vašeho kanálu CI, se kterým můžete sestavit Image Dockeru, nasdílení změn imagí Dockeru do ověřeného registru Dockeru, spuštění imagí Dockeru nebo spustit další operace, které nabízí Dockeru ROZHRANÍ PŘÍKAZOVÉHO ŘÁDKU. Také přidá úkol Docker Compose, který můžete použít k sestavení, nasdílet a spusťte vícekontejnerových aplikací Dockeru nebo spuštění jiné operace, které rozhraní Docker Compose příkazového řádku, jak je znázorněno v obrázek 5-3.

![](./media/image3.png)

Obrázek 5-3: kanálu Docker CI v Azure DevOps služby

Rozšíření Docker můžete použít koncové body služby pro hostitele Dockeru a kontejnerů nebo registry imagí. Výchozí úkoly pomocí místního hostitele Docker, pokud je k dispozici (to aktuálně vyžaduje vlastní agenta služby Azure DevOps); v opačném případě vyžadují zadání připojení hostitele Dockeru. Akce, které jsou závislé na ověřuje pomocí registru Dockeru, jako je například nahráním image, vyžadují, abyste zadali Docker připojení k registru.

Rozšíření Azure DevOps služby Docker nainstaluje následující součásti ve vašem účtu služby Azure DevOps:

-   Koncový bod služby pro připojení k registru Dockeru

-   Koncový bod služby pro připojení k hostiteli kontejneru Dockeru

-   Docker úkolů můžete provádět následující:

-   Sestavte image

-   Nahrání image nebo úložiště do registru

-   Spuštění image v kontejneru

-   Spuštění příkazu Dockeru

-   Docker Compose úlohy ke spuštění příkazu Docker Compose

S těmito úlohami Azure DevOps služby sestavení linuxového Dockeru hostitelů/virtuálních počítačů zřízené v Azure a upřednostňované registru Dockeru (Azure Container Registry, Docker Hubu, privátní DTR Dockeru nebo jiných registru Dockeru) můžete sestavit v kanálu Docker CI velmi konzistentní způsob.

***Požadavky:***

-   Služby Azure DevOps, nebo na místní instalace Team Foundation Server 2015 Update 3 nebo novější.

-   Azure DevOps služby agenta, který obsahuje binární soubory Docker.

Snadný způsob, jak vytvořit jeden z nich se má používat Docker ke spuštění kontejneru na základě image Dockeru agenta služby Azure DevOps.

**Další informace o** číst informace o sestavení CI Azure DevOps služby Docker kanálu a návody, naleznete na následujících stránkách:

Spuštění agenta služby Azure DevOps jako kontejneru Docker: [ https://hub.docker.com/r/\ microsoft/vsts-agent /](https://hub.docker.com/r/microsoft/vsts-agent/)

Rozšíření Azure Docker DevOps služby: <https://aka.ms/vstsdockerextension>

Vytváření imagí Dockeru Linux .NET Core se službami Azure DevOps: <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>

Vytváření sestavení počítače založené na Linuxu Visual Studio Team Service s podporou Dockeru: <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multicontainer-docker-applications"></a>Integrovat, otestovat a ověřit vícekontejnerových aplikací Dockeru

Většina aplikací Dockeru se obvykle skládají z víc kontejnerů než jednoho kontejneru. Dobrým příkladem je aplikace orientované na mikroslužby pro kterou byste měli jeden kontejner na mikroslužbách. Ale i bez striktního vzory přístupu mikroslužeb, je velmi pravděpodobné, že vaši aplikaci v Dockeru by obsahovat více kontejnerů a služeb.

Proto po vytvoření aplikace kontejnerů v kanálu CI, budete potřebovat k nasazení, integrovat a otestujte aplikaci jako celek se všemi jeho kontejnery v rámci hostitele služby integrace Dockeru nebo dokonce do testovací cluster, ke kterému jsou kontejnery distribuovat.

Pokud při použití jednoho hostitele, můžete použít příkazy Dockeru, jako je docker-compose pro sestavování a nasazování kontejnerů související k testování a validaci prostředí Docker v jednom virtuálním počítači. Ale při práci s clusterem orchestrator jako DC/OS, Kubernetes a Docker Swarm, budete muset nasadit prostřednictvím orchestrator, v závislosti na vybrané cluster a Plánovač a jiný mechanismus kontejnery.

Následuje několik typů testů, které lze spustit pro kontejnery Dockeru:

-   Testy jednotek pro kontejnery Dockeru

-   Testování skupin vzájemně propojené aplikace nebo mikroslužeb

-   Testování v produkčním prostředí a "Kanárské" verze

Důležité je, že při spuštění integrace a funkční testy, musíte spustit tyto testy z mimo kontejnery. Testy nesmí být definována a spuštěna v rámci kontejnerů, které nasazujete, protože kontejnery jsou založeny na statické obrázky, které by měly být úplně stejně jako ty, které budete nasazovat do produkčního prostředí.

Je velmi vhodná možnost při testování pokročilejší scénáře, jako je testování (test clusteru, pracovní clusteru a clusteru pro produkční prostředí) několik clusterů k publikování Image do registru k testování v různých clusterech.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Odeslání image Dockeru vlastní aplikace na globální registru Dockeru

Po imagí Dockeru otestovali a ověřili, budete chtít označit a publikovat je do registru Dockeru. Registr Dockeru je důležité část v životním cyklu aplikace Dockeru, protože je centrální místo, kam ukládat vaše vlastní test (označuje se také jako "blessed Image") má být nasazen do dotazů a odpovědí a produkčního prostředí.

Podobně jako na to, jak kód aplikace, které jsou uložené v úložišti SCC (Git atd.) je "zdrojem pravdivých informací", "zdroji pravdivých informací" pro binární aplikace nebo služba bits k nasazení do prostředí QA nebo produkčním prostředí je registru Dockeru.

Obvykle můžete chtít mít privátní úložiště pro vaše vlastní Image do soukromého úložiště ve službě Azure Container Registry nebo v místním registru, jako je Docker Trusted Registry nebo veřejný cloud registru s omezeným přístupem (např. Docker Hubu), i když v tomto posledním případě, pokud není váš kód jako software open source musí důvěřovat zabezpečení od příslušného dodavatele. V obou případech metodu, pomocí kterého lze provést je hodně podobné a nakonec podle v příkazu push docker znázorněný v obrázku 5 až 4.

![](./media/image4.png)

Obrázek 5 – 4: publikování vlastní Image do registru Dockeru

Existuje několik nabídek registry Dockeru z cloudových vendorů, jako je Azure Container Registry, Amazon Web Services Container Registry, Google Container Registry, molo registru a tak dále.

Použití rozšíření Azure DevOps služby Docker, můžete nabízet sadu imagí služby určené soubor docker-compose.yml s více značek do ověřeného registru Dockeru (jako je Azure Container Registry), jak je znázorněno v obrázek 5 – 5.

![](./media/image5.png)

Obrázek 5 – 5: publikování vlastní Image do registru Dockeru pomocí služby Azure DevOps

**Další informace o** Další informace o rozšíření Dockeru pro Azure DevOps služby, přejděte na <https://aka.ms/vstsdockerextension>. Další informace o službě Azure Container Registry, pokračujte <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>Krok 4: CD nasazení

Neměnnost imagí Dockeru zajišťuje opakovatelné nasazování s co vyvíjel, testovat pomocí položek konfigurace a spusťte v produkčním prostředí. Až budete mít Image Dockeru aplikace publikované v registru Dockeru (privátní nebo veřejné), můžete je nasadit do několika prostředí, které bude pravděpodobně (výroba, kontrola kvality, Fázování importu, atd.) z kanálu průběžného Doručování s využitím služby Azure DevOps úlohy kanálu nebo Azure DevOps služby Release Management.

Ale v tuto chvíli to závisí na druhu aplikaci v Dockeru, kterou nasazujete. Nasazení jednoduché aplikace (ze sestavení a nasazení hlediska) stejně jako monolitické aplikace zahrnující několik kontejnerů nebo služeb a nasazené na několika serverech nebo virtuálních počítačů se velmi liší od složitější aplikaci, jako je nasazení aplikace orientované na mikroslužby s mnoha funkcemi. Tyto dva scénáře jsou vysvětlené v následujících částech.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Nasazení skládá aplikací Dockeru do různých prostředí Dockeru

Podívejme se nejprve sledovat bez komplexní scénář: nasazení do jednoduchého hostitelů Docker (virtuální počítače nebo servery) v prostředí jeden nebo více prostředí (dotazů a odpovědí, přípravným a produkčním prostředím). V tomto scénáři interně kanálu průběžného Doručování můžete použít docker-compose (z vaší úlohy nasazení služby Azure DevOps) při nasazování aplikací Dockeru s jeho související sadu kontejnerů a služeb, jak je znázorněno na obrázku 5 a 6.

![](./media/image6.png)

Obrázek 5 a 6: nasazení kontejnerů aplikací jednoduché registru prostředí hostitele Docker

Obrázek 5 – 7 ukazuje, jak připojit vaše sestavení CI pro kontrolu kvality a testovacích prostředí pomocí služby Azure DevOps kliknutím Docker Compose v dialogovém okně Přidat úkol. Ale při nasazení v přípravném nebo produkčním prostředí, obvykle použijete funkcím nástroje Release Management zpracování více prostředí (procesu kontroly kvality, jako jsou přípravným a produkčním prostředím). Pokud nasazujete na jednoho hostitele Docker, je pomocí služby Azure DevOps "Docker Compose" úloh (což je vyvolání docker-compose up příkaz pod pokličkou). Pokud nasazení provádíte do služby Azure Container Service, používá úlohy nasazení prostředí Docker, jak je vysvětleno v následující části.

![](./media/image7.png)

Obrázek 5 – 7: Přidání úkolu Docker Compose v kanálu služby Azure DevOps

Při vytváření vydané verze ve službě Azure DevOps Services trvá sadu vstupní artefakty. Ty by měla být neměnný po celou dobu vydání napříč několika prostředími. Když zavádíte kontejnery, vstupní artefakty zjistit imagí v registru pro nasazení. V závislosti na tom, jak tyto identifikovat není zaručeno nebudou po dobu, vydání, se při odkazování na "myimage:latest" ze souboru docker-compose nejobvyklejší je případ.

Rozšíření Dockeru pro Azure DevOps služby vám, které hodnoty Digest generovat artefaktů sestavení, které obsahují konkrétní registru image, která se zaručeně k jednoznačné identifikaci binární stejnou bitovou kopii. Jedná se o co skutečně chcete použít jako vstup pro vydanou verzi.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Správa vydaných verzí do prostředí Dockeru pomocí Azure DevOps služby Release Management

Prostřednictvím rozšíření Azure DevOps služby můžete vytvořit novou bitovou kopii, její publikování do registru Dockeru, spustit na hostitelích se systémem Linux nebo Windows a použít příkazech, jako je docker-compose pro nasazení několika kontejnerů jako celé aplikace, to vše prostřednictvím Azure DevOps Služby určené pro více prostředí, možnosti správy vydaných verzí, jak je znázorněno v obrázek 5 až 8.

![](./media/image8.png)

Obrázek 5 – 8: Konfigurace úloh Azure DevOps služby Docker Compose v Azure DevOps služby Release Management

Však mít na paměti, že scénáře uvedené v obrázek 5 a 6 a implementovat v obrázek 5 až 8 je poměrně základní (je nasazování jednoduchý hostitelů Docker a virtuálním počítačům a bude možné jedním kontejnerem nebo instance pro každý obrázek) a pravděpodobně by měla sloužit pouze pro vývoj nebo testování sc enarios. Ve většině scénářů organizace produkčního prostředí, byste měli mít vysokou dostupnost (HA) a snadno spravovat škálovatelnosti pomocí služby Vyrovnávání zatížení napříč více uzly, servery a virtuální počítače navíc "inteligentní převzetí služeb při selhání" tak, pokud server nebo uzel selže, jejích služeb a kontejnery se přesune do jiné hostitelský server nebo virtuální počítač. V takovém případě potřebujete pokročilé technologie, jako jsou clustery kontejnerů a orchestrátorů, plánovače. Proto je způsob, jak nasadit do těchto clusterů přesně prostřednictvím pokročilých scénářů je vysvětleno v další části.

### <a name="deploying-complex-docker-applications-to-docker-clusters-dcos-kubernetes-and-docker-swarm"></a>Nasazení složitých aplikací Dockeru do Docker clusterů (DC/OS, Kubernetes a Docker Swarm)

Povaze distribuovaných aplikací vyžaduje výpočetní prostředky, které se taky distribuují. Pokud chcete, aby funkce produkčním měřítku, musíte mít clusteringu, které poskytují vysokou škálovatelnost a vysokou DOSTUPNOSTÍ na základě ve fondu prostředků.

Můžete nasadit kontejnery ručně do těchto clusterů z rozhraní příkazového řádku nástroje, jako je Docker Swarm (například [vytvoření služby docker](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/)) nebo webovým uživatelským rozhraním, jako [Mesosphere Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) pro DC/OS clustery, ale měli Rezervujte, který pouze pro včasnou nasazení testování nebo pro účely správy, jako je škálování na více instancí nebo účely monitorování.

Z hlediska CD a služeb Azure DevOps konkrétně, můžete spustit úlohy speciálně provedl nasazení z prostředí Azure DevOps služby Release Management, které se nasazují kontejnerizovaných aplikací do distribuované clusterů v kontejneru Služby, jak je znázorněno na obrázku 5 až 9.

![](./media/image9.png)

Obrázek 5 až 9: nasazení distribuované aplikace do služby Container Service

Na začátku při nasazování do některých clusterů nebo orchestrátorů, obvykle použijete mechanismy jednotlivých orchestrátorů (to znamená, Mesosphere DC/OS nebo Kubernetes, mějte připravené mechanismy jiné nasazení než Docker a Docker a skriptů pro konkrétní nasazení Swarm) namísto jednodušší a snadným ovládáním docker-compose nástroj na základě definice souboru docker-compose.yml. Ale díky Microsoft Azure DevOps služby Docker nasazení úloh zobrazí obrázek 5 až 10 nyní také můžete nasadit na DC/OS pouze pomocí souboru docker-compose.yml zkušenosti, protože Microsoft za vás provádí tento "překlad" (z vašeho soubor docker-compose.yml do jiných formátů vyžadované DC/OS).

![](./media/image10.png)

Obrázek 5 – 10: přidání úlohy nasazení Dockeru na váš správce prostředků prostředí

Obrázek 5 – 11 předvádí, jak můžete upravit úkol nasadit Docker a zadat typ cíle (Azure Container Service DC/OS, v tomto případě), váš soubor Docker Compose a připojení k registru Dockeru (jako je Azure Container Registry nebo Docker Hubu). Je to, kde úloha načte připravené k použití imagí vlastní Dockeru umožňující nasadit ho jako kontejnery v clusteru DC/OS.

![](./media/image11.png)

Obrázek 5 – 11: Docker nasazení úloh definici nasazení Azure Container Service DC/OS

**Další informace o** Další informace o kanálu CD se službami Azure DevOps a Docker, naleznete na následujících stránkách:

Rozšíření Azure DevOps služby Docker a Azure Container Service: [ https://aka.ms/\ vstsdockerextension](https://aka.ms/vstsdockerextension)

Azure Container Service: <https://aka.ms/azurecontainerservice>

Mesosphere DC/OS: <https://mesosphere.com/product/>

## <a name="step-5-run-and-manage"></a>Krok 5: Spuštění a Správa

Vzhledem k tomu, že spouštění a správu aplikací na podnikové produkční úroveň je hlavní předmět v a sám sebe a z důvodu typ operace a lidé pracují na této úrovni (IT oddělení) a také velký rozsah této oblasti, můžeme mít věnovala celý vedle kapitola s vysvětlením ho.

## <a name="step-6-monitor-and-diagnose"></a>Krok 6: Monitorování a Diagnostika

Toto téma také je obsaženo v následující kapitole jako součást úlohy, které IT oddělení provádí v produkční systémy; je však třeba zvýraznit, že poznatky získané v tomto kroku musí informačního kanálu zpět k vývojovému týmu tak, aby se neustále vylepšené aplikace. Z tohoto hlediska, je také součástí DevOps, i když se úkoly a operace se obvykle zpracovávají pomocí IT.

Pouze v případě monitorování a Diagnostika jsou 100 % jeho obsahu v rámci sféry DevOps se monitorování procesů a analytics provádí vývojový tým proti testování nebo beta prostředí. To se provádí pomocí provádí zátěžové testování nebo jednoduše tak, že monitorování beta nebo dotazů a odpovědí prostředí, ve kterém jsou testerům beta verzí pokusu o nové verze.

>[!div class="step-by-step"]
[Předchozí](index.md)
[další](../run-manage-monitor-docker-environments/index.md)
