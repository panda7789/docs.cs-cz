---
title: Kroky v postupu DevOps vnější smyčky pro aplikaci v Dockeru
description: Přečtěte si postup, "Vnější smyčka" pracovní postup DevOps
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 495e717787c346e451c2f79ef4200b478577aa9d
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676197"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Kroky v postupu DevOps vnější smyčky pro aplikaci v Dockeru

Obrázek 5-1 představuje začátku do konce znázornění postup skládající se z aplikací pracovních postupů DevOps vnější smyčky.

![Tento diagram znázorňuje "Vnější smyčka" DevOps. Když se kód převede do úložiště, kanálu CI spuštění a potom zahájí CD kanálu, ve kterém se aplikace nasadí. Metrikám získaným z nasazené aplikace jsou předány zpět do úlohy vývoje, kde dochází k "vnitřní smyčka", tak vývojovým týmům mít aktuální data a reagovat na uživatele a obchodní potřeby.](./media/image1.png)

**Obrázek 5-1**. Pracovní postup DevOps vnější smyčky pro aplikace Dockeru pomocí nástrojů Microsoftu

Teď se podívejme se na každý z těchto kroků podrobněji.

## <a name="step-1-inner-loop-development-workflow"></a>Krok 1: Pracovní postup vývoje vnitřní smyčky

Tento krok je podrobně popsána v kapitole 4, ale na rekapitulace, tady je kde vnější smyčky začíná, v okamžiku, kdy vývojář vloží kód do systému správy správy zdrojového kódu (např. Git) zahajuje akce kanálu CI.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>Krok 2: Integrace správy zdrojového kódu a správa pomocí služby Azure DevOps a Git

V tomto kroku musíte mít systém správy verzí ke shromáždění konsolidované verzi veškerý kód pocházející z různými vývojáři v týmu.

I když zdát samozřejmostí pro většinu vývojářů, při vytváření aplikací Dockeru v DevOps životního cyklu, správy zdrojového kódu (SCC) a správy zdrojového kódu, je důležité zdůraznit, že nemůže odeslat Image Dockeru s aplikací přímo do globální registru Docker (jako je Azure Container Registry nebo Docker Hubu) z počítače pro vývojáře. Naopak imagí Dockeru do všeobecně dostupné a nasazené do produkčního prostředí musí být vytvořeny výhradně na zdrojový kód, který je integrován v kanálu CI podle vašeho úložiště zdrojového kódu (např. Git) nebo globálního sestavení.

Místní bitové kopie generované vývojáři, měla být používána jimi při testování v rámci svých vlastních počítačích. To je důvod, proč je důležité mít aktivovat z kódu SCC kanálu DevOps.

Azure DevOps služby a Team Foundation Server podporují Gitu a Team Foundation Version Control. Můžete zvolit mezi nimi a prostředí, použijte ho začátku do konce Microsoft. Ale také můžete spravovat svůj kód v externích úložištích (např. GitHub, v místním úložišti Git nebo Subversion) a stále se může připojit k němu a získat kód jako výchozí bod pro svůj kanál DevOps CI.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>Krok 3: Sestavení CI, integraci a testování s Azure DevOps služby a Dockeru

Průběžná integrace se stal standardem pro moderní softwaru, testování a doručení. Řešení Dockeru udržuje jasně oddělené oblasti zájmu mezi týmy vývoje a provozu. Neměnnost imagí Dockeru zajišťuje opakovatelné nasazování mezi co vyvíjel, testovat pomocí položek konfigurace a spusťte v produkčním prostředí. Modul docker nasazených na přenosné počítače pro vývojáře a testovací infrastrukturu zpřístupňuje kontejnery přenosné mezi prostředími.

V tomto okamžiku až budete mít systém správy verzí se správným kódem odeslání, musíte *sestavení služby* vyzvednout kód a spouštět globální sestavení a testů.

Informace o vytváření kanálu CI skládající se z vašeho úložiště kódu (Git, atd.), váš server sestavení (Azure DevOps služby), modul Docker a Docker Registry je interní pracovní postup pro tento krok (průběžná integrace, sestavení, testování).

Můžete Azure DevOps Services jako základ pro vytváření aplikací a nastavení kanálu CI a publikování "artefaktů sestavení" na "úložiště artefaktů," který je vysvětlen v dalším kroku.

Při použití Docker pro nasazení "konečné artefakty" nasazení jsou Image Dockeru s aplikací nebo služeb vložené v nich. Tyto Image jsou vloženy nebo publikovanou do *registru Dockeru* (soukromé úložiště jako ty, které můžete mít ve službě Azure Container Registry nebo veřejnou verzi jako registru Docker Hub, která se běžně používá pro oficiální základní Image).

Tady je základní princip: Zahájit schválení potvrzení pro úložiště SCC jako je Git bude kanálu CI. Potvrzení změn způsobí služby Azure DevOps a spustit úlohu sestavení a v kontejneru Dockeru, po úspěšném dokončení této úlohy, nasdílení image Dockeru do registru Dockeru, jak je znázorněno na obrázku 5-2.

![První část vnější smyčky zahrnuje kroky 1 až 3 z kódu, spouštění, ladění a pak ověřit kód úložiště až do kroku, položky konfigurace sestavení a testování](./media/image2.png)

**Obrázek 5-2**. Kroky v CI

Tady jsou základní kroky pracovního postupu CI s využitím Dockeru a Azure DevOps služby:

1. Vývojář nasdílí potvrzení změn do úložiště SCC (Git/Azure DevOps Services, Githubu, atd.).

2. Pokud používáte Azure DevOps Services nebo Git, CI je součástí, což znamená, že je stejně jednoduché jako zaškrtnutím políčka ve službách Azure DevOps. Pokud používáte externí SCC (např. GitHub) `webhook` budou upozornění služby Azure DevOps aktualizace nebo push pro Git/GitHub.

3. Služby Azure DevOps si vyžádá SCC úložiště, včetně souboru Dockerfile popisující bitovou kopii, jakož i kód aplikace a testů.

4. Služby Azure DevOps vytvoří image Dockeru a označí ji číslem sestavení.

5. Služby Azure DevOps vytvoří instanci kontejneru Dockeru v rámci zřízené hostitele Docker a spouští příslušné testy.

6. Pokud jsou testy úspěšné, image je nejprve relabeled na smysluplný název, abyste věděli, je "blessed sestavení" (například "/ 1.0.0" nebo libovolný popisek) a pak nahrány do registru Dockeru (Docker Hub, Azure Container Registry, DTR atd.)

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Implementace kanálu CI pomocí služby Azure DevOps a rozšíření Dockeru pro Azure DevOps služby

Visual Studio Azure DevOps služby obsahuje šablony verzí, který vám pomůže v kanálu CI/CD pomocí kterého můžete sestavit Image Dockeru, nasdílení změn imagí Dockeru do ověřeného registru Dockeru, spuštění imagí Dockeru nebo spuštění jiné operace, které nabízí & sestavení rozhraní příkazového řádku Dockeru. Také přidá úkol Docker Compose, který můžete použít k sestavení, nasdílet a spustit více kontejnerů aplikací Dockeru nebo spuštění jiné operace, které rozhraní Docker Compose příkazového řádku, jak je znázorněno v obrázek 5-3.

![Zobrazení prohlížeče s kanálu Docker CI v Azure DevOps](./media/image3.png)

**Obrázek 5 – 3**. Docker CI kanál služby Azure DevOps, včetně sestavení a vydání šablony a přidružené úlohy.

Tyto šablony a úlohy můžete použít k vytvoření artefaktů CI/CD pro sestavení / testování a nasazení v Azure Service Fabric, Azure Kubernetes Service a podobné nabídky.

S těmito úkoly Visual Studio Team Services sestavení linuxového Dockeru hostitelů/virtuálních počítačů zřízené v Azure a upřednostňované registru Dockeru (Azure Container Registry, Docker Hubu, privátní DTR Dockeru nebo jiných registru Dockeru) můžete sestavit v kanálu Docker CI velmi konzistentní způsob.

***Požadavky:***

- Služby Azure DevOps, nebo na místní instalace Team Foundation Server 2015 Update 3 nebo novější.

- Azure DevOps služby agenta, který obsahuje binární soubory Docker.

  Snadný způsob, jak vytvořit jeden z těchto agentů se má používat Docker ke spuštění kontejneru na základě image Dockeru agenta služby Azure DevOps.

> [! Informace o] Přečtěte si další informace o sestavení Azure DevOps služby Docker CI kanál a zobrazit návody, naleznete na těchto webech:
>
> - Spuštění agenta aplikace Visual Studio Team Services (teď Azure DevOps služby) jako kontejneru Docker: \
>   [*https://hub.docker.com/r/microsoft/vsts-agent/*](https://hub.docker.com/r/microsoft/vsts-agent/)
>
> - Vytváření imagí Dockeru Linux .NET Core se službami Azure DevOps: \
>   [*https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/*](https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/)
>
> - Vytváření služby založené na Linuxu týmu Visual Studio vytvořte počítač s podporou Dockeru: \
>   [*http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support*](http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support)

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>Integrace, testování a ověřování vícekontejnerových aplikací Dockeru

Většina aplikací Dockeru se obvykle skládají z víc kontejnerů než jednoho kontejneru. Dobrým příkladem je aplikace orientované na mikroslužby pro kterou byste měli jeden kontejner na mikroslužbách. Ale i bez striktního vzory přístupu mikroslužeb, je pravděpodobné, že vaši aplikaci v Dockeru by obsahovat více kontejnerů a služeb.

Proto po vytvoření aplikace kontejnerů v kanálu CI, budete potřebovat k nasazení, integrovat a otestujte aplikaci jako celek se všemi jeho kontejnery v rámci hostitele služby integrace Dockeru nebo dokonce do testovací cluster, ke kterému jsou kontejnery distribuovat.

Pokud při použití jednoho hostitele, můžete použít příkazy Dockeru, jako je docker-compose pro sestavování a nasazování kontejnerů související k testování a validaci prostředí Docker v jednom virtuálním počítači. Ale pokud pracujete s clusterem orchestrator jako DC/OS, Kubernetes a Docker Swarm, budete muset nasadit prostřednictvím orchestrator, v závislosti na vybrané cluster a Plánovač a jiný mechanismus kontejnery.

Následuje několik typů testů, které lze spustit pro kontejnery Dockeru:

- Testy jednotek pro kontejnery Dockeru

- Testování skupin vzájemně propojené aplikace nebo mikroslužeb

- Testování v produkčním prostředí a "Kanárské" verze

Důležité je, že při spuštění integrace a funkční testy, musíte spustit tyto testy z mimo kontejnery. Testy nejsou obsaženy nebo spouštění v kontejnerech, které nasazujete, protože kontejnery jsou založeny na statické obrázky, které by měly být úplně stejně jako ty, které vám bude nasazení do produkčního prostředí.

Praktické možnost při testování pokročilejší scénáře, jako jsou včetně několik clusterů (testovací cluster, pracovní clusteru a clusteru pro produkční prostředí) je k publikování Image do registru, takže testování v různých clusterech.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Odeslání image Dockeru vlastní aplikace na globální registru Dockeru

Po imagí Dockeru otestovali a ověřili, budete chtít označit a publikovat je do registru Dockeru. Registr Dockeru je důležité část v životním cyklu aplikace Dockeru, protože je centrální místo, kam ukládat vaše vlastní test (označované také jako "blessed Image") má být nasazen do dotazů a odpovědí a produkčního prostředí.

Podobně jako na to, jak kód aplikace, které jsou uložené v úložišti SCC (Git atd.) je "zdrojem pravdivých informací", "zdroji pravdivých informací" pro binární aplikace nebo služba bits k nasazení do prostředí QA nebo produkčním prostředí je registru Dockeru.

Obvykle můžete chtít mít privátní úložiště pro vaše vlastní Image do soukromého úložiště ve službě Azure Container Registry nebo v místním registru, jako je Docker Trusted Registry nebo veřejný cloud registru s omezeným přístupem (např. Docker Hubu), i když v tomto posledním případě, pokud není váš kód jako software open source musí důvěřovat zabezpečení od příslušného dodavatele. V obou případech se podobá metodu, kterou používáte a je založena na `docker push` příkaz, jak je znázorněno v obrázek 5 – 4.

![V kroku 3, pro integraci sestavení a testování (CI) může publikovat výsledná imagí dockeru do registru privátní nebo veřejné.](./media/image4.png)

**Obrázek 5 – 4**. Publikování vlastní Image do registru Dockeru

Existuje několik nabídek registry Dockeru z cloudových vendorů, jako je Azure Container Registry, Amazon Web Services Container Registry, Google Container Registry, molo registru a tak dále.

Používání úloh Dockeru, můžete odeslat sadu imagí služby určené `docker-compose.yml` souboru s více značek do ověřeného registru Dockeru (jako je Azure Container Registry), jak je znázorněno v obrázek 5 – 5.

![Zobrazit v prohlížeči kroku k publikování Image do registru z Azure DevOps.](./media/image5.png)

**Obrázek 5 až 5**. Pomocí služby Azure DevOps publikování vlastní Image do registru Dockeru

> [! Informace o] Další informace o službě Azure Container Registry, najdete v části <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>Krok 4: CD, nasazení

Neměnnost imagí Dockeru zajišťuje opakovatelné nasazování s co vyvíjel, testovat pomocí položek konfigurace a spusťte v produkčním prostředí. Až budete mít Image Dockeru aplikace publikované v registru Dockeru (privátní nebo veřejné), můžete je nasadit do několika prostředí, které bude pravděpodobně (výroba, kontrola kvality, Fázování importu, atd.) z kanálu průběžného Doručování s využitím služby Azure DevOps úlohy kanálu nebo Azure DevOps služby Release Management.

Ale v tuto chvíli to závisí na druhu aplikaci v Dockeru nasazujete. Nasazení jednoduché aplikace (ze sestavení a nasazení hlediska) stejně jako monolitické aplikace zahrnující několik kontejnerů nebo služeb a nasazené na několika serverech nebo virtuálních počítačů se liší od složitější aplikaci, jako je nasazení aplikace orientované na mikroslužby s mnoha funkcemi. Tyto dva scénáře jsou vysvětlené v následujících částech.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Nasazení skládá aplikací Dockeru do různých prostředí Dockeru

Podívejme se nejprve sledovat bez komplexní scénář: nasazení do jednoduchého hostitelů Docker (virtuální počítače nebo servery) v prostředí jeden nebo více prostředí (dotazů a odpovědí, přípravným a produkčním prostředím). V tomto scénáři interně kanálu průběžného Doručování můžete použít docker-compose (z vaší úlohy nasazení služby Azure DevOps) při nasazování aplikací Dockeru s jeho související sadu kontejnerů a služeb, jak je znázorněno na obrázku 5 a 6.

![Nasazení CD kroku (4) můžete publikovat do různých prostředí, jako jsou funkce q & a, přípravným a produkčním prostředím.](./media/image6.png)

**Obrázek 5 a 6**. Nasazení kontejnerů aplikací jednoduché registru prostředí hostitele Docker

Obrázek 5 – 7 ukazuje, jak připojit vaše sestavení CI pro kontrolu kvality a testovacích prostředí pomocí služby Azure DevOps kliknutím Docker Compose v dialogovém okně Přidat úkol. Ale při nasazení v přípravném nebo produkčním prostředí, obvykle použijete funkcím nástroje Release Management zpracování více prostředí (procesu kontroly kvality, jako jsou přípravným a produkčním prostředím). Pokud nasazujete na jednoho hostitele Docker, je pomocí služby Azure DevOps úkolu "Docker Compose" (což je vyvolání `docker-compose up` příkaz pod pokličkou). Pokud nasazení provádíte do služby Azure Container Service, používá úlohy nasazení prostředí Docker, jak je vysvětleno v následující části.

![Zobrazení prohlížeče s přidávat úkoly Docker Compose.](./media/image7.png)

**Obrázek 5 – 7**. Přidání úkolu Docker Compose v kanálu služby Azure DevOps

Při vytváření vydané verze ve službě Azure DevOps Services trvá sadu vstupní artefakty. Tyto artefakty by měla být neměnný po dobu platnosti verze, ve všech prostředích. Když zavádíte kontejnery, vstupní artefakty zjistit imagí v registru pro nasazení. V závislosti na tom, jak se tyto Image jsou identifikovat, není zaručeno, nebudou po dobu, vydání, Nejobvyklejšími případu se při odkazování na `myimage:latest` z `docker-compose` souboru.

Šablony služby Azure DevOps vám poskytnou, které hodnoty Digest generovat artefaktů sestavení, které obsahují konkrétní registru image, která se zaručeně k jednoznačné identifikaci binární stejnou bitovou kopii. Jedná se o co skutečně chcete použít jako vstup pro vydanou verzi.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Správa vydaných verzí do prostředí Dockeru pomocí Azure DevOps služby Release Management

Prostřednictvím šablon služeb Azure DevOps můžete sestavíte novou image, její publikování do registru Dockeru, spusťte na hostitelích se systémem Linux nebo Windows a pomocí příkazů, jako `docker-compose` nasazení několika kontejnerů jako celé aplikace, to vše prostřednictvím Azure DevOps Služby určené pro více prostředí, možnosti správy vydaných verzí, jak je znázorněno v obrázek 5 až 8.

![Zobrazení prohlížeče s Azure DevOps, konfiguraci Docker compose vydané verze.](./media/image8.png)

**Obrázek 5 až 8**. Konfigurace úlohy Azure DevOps služby Docker Compose v Azure DevOps služby Release Management

Však mít na paměti, že scénáře uvedené v obrázek 5 a 6 a implementovat v obrázek 5 až 8 je jednoduchý (nasazení jednoho hostitele Dockeru a virtuální počítače a bude možné jedním kontejnerem nebo instance pro každý obrázek) a pravděpodobně by měla sloužit pouze pro vývoj nebo testování sce narios. Ve většině scénářů organizace produkčního prostředí, byste měli mít vysokou dostupnost (HA) a snadno spravovat škálovatelnost ve Vyrovnávání zatížení napříč více uzly, servery a virtuální počítače navíc "inteligentní převzetí služeb při selhání" tak pokud server nebo uzel selže, jejích služeb a kontejnery Přesune na jiný hostitelský server nebo virtuální počítač. V takovém případě musíte pokročilejší technologií, jako jsou clustery kontejnerů a orchestrátorů, plánovače. Proto způsob, jak nasadit do těchto clusterů se zpracováním pokročilé scénáře je vysvětleno v další části.

### <a name="deploying-docker-applications-to-docker-clusters"></a>Nasazení aplikací Dockeru do Docker clusterů

Povaze distribuovaných aplikací vyžaduje výpočetní prostředky, které se taky distribuují. Pokud chcete, aby funkce produkčním měřítku, musíte mít clusteringu, které nabízejí vysokou škálovatelnost a vysokou dostupností na základě ve fondu prostředků.

Můžete nasadit kontejnery ručně do těchto clusterů z nástroje rozhraní příkazového řádku nebo webovým uživatelským rozhraním, ale měli byste si rezervovat tento druh ručního testování přímé nasazení nebo účely správy, jako je škálování na více instancí nebo monitorování.

Z hlediska CD a služeb Azure DevOps konkrétně, můžete spustit úlohy speciálně provedl nasazení z prostředí Azure DevOps služby Release Management, které bude nasazování kontejnerizovaných aplikací do distribuované clusterů v kontejneru Služby, jak je znázorněno na obrázku 5 až 9.

![Nasazení CD kroku (4) můžete také publikovat do clusterů pomocí orchestrátorů.](./media/image9.png)

**Obrázek 5 až 9**. Nasazení distribuované aplikace do služby Container Service

Na začátku při nasazování do některých clusterů nebo orchestrátorů, obvykle použijete mechanismy jednotlivých orchestrátorů (to znamená, Kubernetes a mějte připravené mechanismy jiného nasazení, Service Fabric) a skriptů pro konkrétní nasazení místo jednodušší a snadným ovládáním `docker-compose` na základě nástroj `docker-compose.yml` definičního souboru. Ale díky Azure DevOps služby Docker nasazení úloh zobrazí obrázek 5 až 10 nyní také můžete nasadit podporovaných orchestrátorů pouze pomocí vaší známý `docker-compose.yml` souboru vzhledem k tomu, že nástroj provádí tento "překlad" (z vašeho `docker-compose.yml`soubor do formátu vyžadované orchestrator).

![Úloha nasazení zobrazit v prohlížeči z katalogu úloh v Azure DevOps, zobrazuje Dockeru.](./media/image10.png)

**Obrázek 5 až 10**. Přidání úlohy nasazení Dockeru na váš správce prostředků prostředí

Obrázek 5 – 11 předvádí, jak můžete upravit úkol nasadit Docker a zadat typ cíle (Azure Container Service DC/OS, v tomto případě), váš soubor Docker Compose a připojení k registru Dockeru (jako je Azure Container Registry nebo Docker Hubu). Toto je úloha, která načte připravené k použití imagí vlastní Dockeru umožňující nasadit ho jako kontejnery v clusteru.

![Zobrazení prohlížeče s Azure DevOps, nasaďte do definice úlohy nástroje orchestrator.](./media/image11.png)

**Obrázek 5 – 11**. Docker nasazení úloh definici nasazení Azure Container Service DC/OS

> [! Informace o] Další informace o kanálu CD se službami Azure DevOps a Docker, navštivte <https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>Krok 5: Spuštění a Správa

Vzhledem k tomu, že spouštění a správu aplikací na podnikové produkční úroveň je hlavní předmět v a sám sebe a z důvodu typ operace a lidé pracují na této úrovni (IT oddělení) a také velký rozsah této oblasti, se věnovala celý následující kapitoly s vysvětlením ho.

## <a name="step-6-monitor-and-diagnose"></a>Krok 6: Monitorování a Diagnostika

Toto téma také je obsaženo v následující kapitole jako součást úlohy se provádí v produkční systémy; je však třeba zvýraznit, že poznatky získané v tomto kroku musí informačního kanálu zpět k vývojovému týmu tak, aby se neustále vylepšené aplikace. Z tohoto hlediska, je také součástí DevOps, i když se úkoly a operace se běžně provádějí v IT.

Pouze v případě monitorování a Diagnostika jsou 100 % v rámci sféry DevOps se monitorování procesů a analytics provádí vývojový tým proti testování nebo beta prostředí. To se provádí pomocí provádí zátěžové testování nebo sledováním beta nebo dotazů a odpovědí prostředí, ve kterém jsou testerům beta verzí pokusu o nové verze.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
