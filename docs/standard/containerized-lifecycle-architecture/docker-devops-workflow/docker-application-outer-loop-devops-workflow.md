---
title: Kroky v pracovním postupu vnější smyčky DevOps pro aplikaci Docker
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 198313c260b36d3f3025606e73e220c361a7ebb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Kroky v pracovním postupu vnější smyčky DevOps pro aplikaci Docker

Obrázek 5-1 uvede začátku do konce Popis shromažďování kroky zahrnující pracovního postupu DevOps vnější smyčky.

![](./media/image1.png)

Obrázek 5-1: pracovní postup vnější smyčky DevOps pro Docker aplikací pomocí nástroje společnosti Microsoft

Nyní se podívejme se na každý z těchto kroků podrobněji.

## <a name="step-1-inner-loop-development-workflow"></a>Krok 1: Pracovní postup vývoje vnitřní smyčky

Tento krok je podrobně vysvětleny v kapitole 4, ale recap, zde je kde vnější smyčky začne, v okamžiku, kdy vývojář nabízených oznámení kódu do systému správy správy zdrojů (např. Git) inicializaci CI kanálu akce.

## <a name="step-2-source-code-control-integration-and-management-with-visual-studio-team-services-and-git"></a>Krok 2: Integrace ovládacích prvků zdrojového kódu a správy pomocí nástroje Visual Studio Team Services a Git

V tomto kroku musíte mít systém správy verzí získat konsolidované verzi všechny kód pocházejících z různých vývojáři v týmu.

I když řízení zdrojového kódu (SCC) a správy zdrojového kódu zdát sekundu povaze na Většina vývojářů, při vytváření aplikací pro Docker v DevOps životní cyklus, je velmi důležité zdůraznit, že nesmí odeslat imagí Dockeru s aplikací přímo do globální Docker registru (například Azure kontejneru registru nebo úložiště Docker Hub) z počítače pro vývojáře. Naopak imagí Dockeru vydání a nasazovány do provozních prostředí musí být vytvořeny pouze na zdrojový kód, který je právě integrován v globální sestavení nebo kanálu CI podle vašeho úložiště zdrojového kódu (např. Git).

Místní obrázky vygenerována vývojáři sami má být používána pouze vývojáři při testování v rámci své vlastní počítače. Z tohoto důvodu je důležité mít aktivovaný z kódu SCC DevOps kanálu.

Visual Studio Team Services a serveru Team Foundation Server podporují Git a správy verzí Team Foundation. Můžete vybrat mezi nimi a použít jej pro prostředí Microsoft začátku do konce. Ale můžete také spravovat kód do externího úložiště (například Githubu, místní úložiště Git nebo Subversion) a stále možné se k nim připojit a získat kód jako výchozí bod pro svůj DevOps CI kanál.

## <a name="step-3-build-ci-integrate-and-test-with-visual-studio-team-services-and-docker"></a>Krok 3: Sestavení, CI, integrace a testování pomocí sady Visual Studio Team Services a Docker

CI vyplývá jako standard pro testování moderní softwaru a doručení. Řešení Docker udržuje jasně oddělené oblasti zájmu mezi týmy vývoj a provoz. Neměnitelnosti imagí Dockeru zajišťuje opakovatelných nasazení mezi co vyvinuté, testovat prostřednictvím položky konfigurace a spuštění v produkčním prostředí. Modul docker nasazený na vývojáře přenosných počítačů a infrastruktury testovací zajišťuje kontejnery přenosné prostředích.

V tomto okamžiku až budete mít systém správy verzí s správný kód odeslat, musíte *sestavení service* vyzvednutí kód a spusťte testy a globální sestavení.

Interní pracovní postup pro tento krok (CI, sestavení, testovací) je o vytváření položek konfigurace kanálu skládající se z vašeho kódu úložiště (Git, atd.), vašem serveru sestavení (Visual Studio Team Services), modul Docker a Docker registru.

Můžete Visual Studio Team Services jako základ pro vytváření aplikací a nastavení svůj kanál položek konfigurace a publikování integrovaný "artefakty" "artefakty úložiště," které je popsané v dalším kroku.

Při použití Docker pro nasazení "poslední artefakty" k nasazení jsou imagí Dockeru vaší aplikace nebo služby vložených v nich. K publikování nebo poslat tyto bitové kopie *Docker registru* (privátní úložiště jako ty, které může mít v registru kontejner Azure nebo veřejné jeden jako Docker Hub registru, který se běžně používá pro oficiální základní Image).

Tady je základní princip: CI kanálu bude spuštěna vypnout potvrzení změn do úložiště SCC jako Git. Potvrzení způsobí, že Visual Studio Team Services a spusťte úlohu sestavení v rámci kontejner Docker, po úspěšném dokončení této úlohy, nabízená bitovou kopii Docker Docker registru, jak je znázorněno na obrázku 5-2.

![](./media/image2.png)

Obrázek 5 – 2: kroky ve službě CI

Zde jsou základní kroky konfigurace pracovního postupu s Docker a Visual Studio Team Services:

1.  Vývojář doručí potvrzení změn do úložiště SCC (Git/Visual Studio Team Services, GitHub, atd.).

2.  Pokud používáte Visual Studio Team Services nebo Git, CI je součástí, což znamená, že je stejně jednoduché jako výběrem zaškrtávacího políčka v sadě Visual Studio Team Services. Pokud používáte externí SCC (např. Githubu), *webhooku* bude oznámit Visual Studio Team Services aktualizace nebo nabízená Git/Githubu.

3.  Visual Studio Team Services vrátí SCC úložiště, včetně soubor Docker popisující bitovou kopii, jakož i kód aplikace a testování.

4.  Visual Studio Team Services popisky s číslo sestavení a sestavení Docker image.

5.  Visual Studio Team Services vytvoří kontejner Docker v rámci zřízené Docker hostitele a spustí příslušné testy.

6.  Pokud jsou testy úspěšné, bitovou kopii je nejdřív relabeled smysluplný název, abyste věděli, je "blessed sestavení" (například "/ 1.0.0" nebo jiné štítek) a pak instaluje do vaší Docker registru (úložiště Docker Hub, Azure kontejneru registru, DTR atd.)

### <a name="implementing-the-ci-pipeline-with-visual-studio-team-services-and-the-docker-extension-for-visual-studio-team-services"></a>Implementace CI kanálu s Visual Studio Team Services a Docker rozšíření pro Visual Studio Team Services

[Rozšíření Visual Studio Team Services Docker](https://aka.ms/vstsdockerextension) přidá do kanálu CI se kterým můžete vytvářet bitové kopie Docker, nabízená imagí Dockeru ověření Docker registru, spustit imagí Dockeru nebo spuštění jiné operace, které nabízí úlohu Docker rozhraní příkazového řádku. Také přidá Docker Compose úloh, které můžete použít k sestavení, push a spouštět aplikace multicontainer Docker nebo spuštění jiné operace, které nabízí Docker Compose CLI, jak je znázorněno v obrázku 5-3.

![](./media/image3.png)

Obrázek 5 – 3: kanálu Docker CI ve Visual Studio Team Services

Rozšíření Docker pomocí koncových bodů služby pro hostitelů Docker a pro kontejner nebo registrech bitové kopie. Výchozí úlohy pomocí místního hostitele Docker, pokud je k dispozici (to aktuálně vyžaduje vlastní agenta Visual Studio Team Services); jinak vyžadují připojení hostitelů Docker zadat. Akce, které jsou závislé na ověřovaného s Docker registru, například když zavedete bitovou kopii, vyžadují, abyste zadali Docker registru připojení.

Ve vašem účtu Visual Studio Team Services instalaci rozšíření je Visual Studio Team Services Docker následující součásti:

-   Koncový bod služby pro připojení k registru Docker

-   Koncový bod služby pro připojení k hostiteli kontejner Docker

-   Úloha Docker proveďte následující:

-   Vytvoření obrázku

-   Odešlete bitovou kopii nebo úložiště do registru

-   Spustit bitovou kopii v kontejneru

-   Spusťte příkaz Docker

-   Úloha Docker Compose spustit příkaz Docker Compose

Tyto úlohy Visual Studio Team Services sestavení hostitele nebo virtuálních počítačů Linux Docker zřízené v Azure a vaše upřednostňované Docker registru (registru kontejner Azure, úložiště Docker Hub, privátní DTR Docker nebo jiných Docker registru) můžete sestavit svůj Docker CI kanál v velmi konzistentní způsob.

***Požadavky:***

-   Visual Studio Team Services, nebo na místní instalace, Team Foundation Server 2015 Update 3 nebo novější.

-   Visual Studio Team Services agenta, který má Docker binární soubory.

Snadný způsob, jak vytvořit jednu z těchto je se použije ke spuštění na základě bitové kopie Visual Studio Team Services agenta Docker kontejner Docker.

**Další informace o** číst informace o kompletace CI služby Docker sady Visual Studio Team kanálu a návody najdete na následujících serverech:

Spuštění agenta Visual Studio Team Services jako kontejner Docker: [ https://hub.docker.com/r/\ microsoft nebo služby vsts-agent nebo](https://hub.docker.com/r/microsoft/vsts-agent/)

Služby VSTS Docker rozšíření: <https://aka.ms/vstsdockerextension>

Vytváření bitových kopií .NET Core Linux Docker s Visual Studio Team Services: <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>

Vytváření sestavení počítač založený na Linuxu Visual Studio Team služby s Docker podpory: <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multicontainer-docker-applications"></a>Integrace, testování a ověření multicontainer Docker aplikace

Většina aplikací Docker se obvykle skládají z několika kontejnerů než jednoho kontejneru. Dobrým příkladem je orientované mikroslužeb aplikace, pro které byste měli jednoho kontejneru typu jedné mikroslužby. Ale i bez výhradně následující vzory mikroslužeb přístup, je velmi pravděpodobné, že by aplikace Docker skládá z více kontejnerů nebo služby.

Proto po vytvoření aplikace kontejnerů v kanálu CI, musíte také nasadit, integrace a testování aplikace jako celek se všemi jeho kontejnery v rámci hostitele integraci Docker nebo i do na zkušební cluster, do které jsou kontejnerů distribuován.

Pokud používáte jednoho hostitele, můžete použít příkazy Docker jako docker-tvoří k vytváření a nasazování související kontejnery pro otestování a ověření prostředí Docker v jeden virtuální počítač. Ale pokud pracujete s clusteru služby orchestrator jako DC/OS, Kubernetes nebo Docker Swarm, budete muset nasazení kontejnerů přes jiný mechanismus nebo orchestrator, v závislosti na vybrané clusteru nebo plánovače.

Následují několik typů testů, které se dají spouštět i proti Docker kontejnerů:

-   Testování částí pro Docker kontejnery

-   Testování skupiny vzájemně souvisejících aplikací nebo mikroslužeb

-   Testování v produkčním a "Kanárských" verzích

Důležité je, že při spuštění, integrace a funkčních testů, musíte spustit tyto testy z mimo kontejnery. Testy nesmí být definována a spustit v rámci kontejnerů, které nasazujete, protože kontejnery jsou založené na statických bitových kopií, které by měly být úplně stejně jako ty, které budete nasazovat do produkčního prostředí.

Velmi vhodná možnost při testování pokročilejší scénáře jako testování několik clusterů (test clusteru, cluster pracovní a provozní cluster), je publikovat bitové kopie do registru k testování v různých clusterech.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Push bitovou kopii Docker vlastní aplikaci do globální registru Docker

Po imagí Dockeru byly testovány a ověřit, budete chtít značky a publikovat je do vašeho Docker registru. Docker registru je důležitých typů v životním cyklu aplikace Docker, protože je centrálním místem, kde ukládáte svůj vlastní test (neboli "blessed Image") k nasazení do QA a provozní prostředí.

Podobně jako jak kód aplikace, které jsou uložené v úložišti SCC (Git atd.) je "zdrojem pravdivosti", Docker registru je vaše "zdrojem pravdivosti" binární aplikace nebo služba bits k nasazení do QA nebo produkční prostředí.

Obvykle můžete chtít mít vaší privátní úložiště pro vaše vlastní Image, buď v privátní úložiště v registru kontejner Azure nebo místní registru jako důvěryhodné registru Docker nebo veřejného cloudu registru s omezeným přístupem (např. Úložiště docker Hub), i když v tomto případě Pokud váš kód není otevřený zdroj, musí důvěřovat zabezpečení od dodavatele. V obou případech metodu, pomocí kterého můžete to udělat je poměrně podobné a nakonec podle docker nabízené příkaz, jak je to znázorněno na obrázku 5-4.

![](./media/image4.png)

Obrázek 5-4: publikování vlastních bitových kopií do registru Docker

Existuje více nabídek Docker registrech od dodavatelů cloud jako registru kontejner Azure, Amazon Web Services kontejneru registru, Google kontejneru registru, molo registru a tak dále.

Pomocí rozšíření Visual Studio Team Services Docker, můžete nabízet sadu bitové kopie služby definované soubor docker-compose.yml s více značek ověření registru Docker (např. Azure registru kontejneru), jak je znázorněno v obrázku 5-5.

![](./media/image5.png)

Obrázek 5 – 5: použití Visual Studio Team Services k publikování vlastních bitových kopií do registru Docker

**Další informace o** Další informace o Docker rozšíření pro Visual Studio Team Services, přejděte na <https://aka.ms/vstsdockerextension>. Další informace o registru kontejner Azure, přejděte na <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>Krok 4: CD, nasazení

Neměnitelnosti imagí Dockeru zajišťuje opakovatelných nasazení co vyvinuté, testovat prostřednictvím položky konfigurace a spuštění v produkčním prostředí. Až budete mít imagí Dockeru aplikace publikována v registru systému Docker (privátní nebo veřejné), můžete je nasadit do několika prostředí, které by mohly mít (produkční, kontrolu kvality, pracovní, apod.) z vaší CD kanálu pomocí Visual Studio Team Services úlohy v kanálu nebo Visual Studio Team Services Release Management.

Ale v tuto chvíli to závisí na jaký druh Docker aplikace, kterou nasazujete. Nasazení jednoduchou aplikaci (z sestavení a nasazení hlediska) jako monolitický aplikace, která zahrnuje několik kontejnery nebo služeb a nasazené na několika serverech nebo virtuálních počítačů je příliš neliší od nasazení složitější aplikaci jako aplikace orientované mikroslužeb s možností hyperškálovatelný systém. Tyto dva scénáře jsou vysvětlené v následujících částech.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Nasazení skládá Docker aplikace pro prostředí s více Docker

Podívejme se na méně komplexní scénář první: nasazení jednoduché hostitelů Docker (virtuální počítače nebo servery) v prostředí jednoho nebo několika prostředí (QA, přípravné nebo produkční prostředí). V tomto scénáři interně svůj CD kanál můžete použít docker-tvoří (z úloh nasazení Visual Studio Team Services) pro nasazení aplikací Docker pomocí jeho související sady kontejnery nebo služeb, jak ukazuje následující obrázek 5 a 6.

![](./media/image6.png)

Obrázek 5 – 6: nasazení kontejnery aplikací jednoduché registru prostředí hostitelů Docker

Obrázek 5 – 7 označuje, jak připojit vaše CI sestavení do QA a testovací prostředí pomocí sady Visual Studio Team Services kliknutím Docker Compose v dialogovém okně Přidat úloha. Ale při nasazení v pracovním nebo produkčním prostředí, obvykle použijete zpracování prostředí s více funkcí správy verzí (jako kontrolu kvality, přípravné nebo produkční prostředí). Pokud nasazujete jednu hostitelů Docker, používá Visual Studio Team Services úkolů "Docker Compose" (což je vyvolání docker-tvoří až příkaz pod pokličkou). Pokud nasazujete do Azure Container Service, použije úloha Docker nasazení, jak je popsáno v následující části.

![](./media/image7.png)

Obrázek 5 – 7: Přidání Docker Compose úlohy v kanálu Visual Studio Team Services

Když vytvoříte verze ve Visual Studio Team Services, trvá sadu vstupní artefakty. To by měla být neměnný po celou dobu verze ve více prostředích. Když zavedete kontejnery, identifikujte vstupní artefakty bitové kopie v registru pro nasazení. V závislosti na tom, jak tyto identifikovat budou se nezaručuje, zůstane po dobu trvání verze nejobvyklejší je případ se, když odkazujete "myimage:latest" ze souboru docker-compose.

Docker rozšíření pro Visual Studio Team Services vám dává, které umožňuje vygenerovat artefaktů sestavení, které obsahují konkrétní registru image hodnoty Digest který zaručeně k jednoznačné identifikaci binární stejnou bitovou kopii. Jsou to, co Opravdu chcete použít jako vstup pro vydání.

### <a name="managing-releases-to-docker-environments-by-using-visual-studio-team-services-release-management"></a>Správa verzí do prostředí Docker pomocí Visual Studio Team Services Release Management

Prostřednictvím rozšíření Visual Studio Team Services, můžete vytvořit novou bitovou kopii, publikování do registru Docker, spusťte ho na hostitele se systémem Linux nebo Windows a použijte příkazy jako docker-tvoří k nasazení několika kontejnerů jako celá aplikace, to vše Vizuálu Možnosti správy verzí Team Services Studio určený pro prostředí s více, jak je znázorněno v obrázku 5 až 8.

![](./media/image8.png)

Obrázek 5 – 8: konfigurace Visual Studio Team Services Docker Compose úlohy z Visual Studio Team Services Release Management

Ale mějte na paměti, že scénář zobrazují v obrázku 5 a 6 a je implementována v obrázku 5 až 8 je poměrně základní (nasazení jednoduché hostitelů Docker a virtuální počítače a bude jediný kontejner nebo instance pro každý image) a pravděpodobně by měl být použity pouze pro vývoj nebo testování sc enarios. Ve většině scénářů produkční enterprise by budete chtít mít vysokou dostupnost (HA) a snadno spravovat škálovatelnost pomocí vyrovnávání zatížení napříč více uzly, serverů a virtuálních počítačů a "inteligentního převzetí služeb při selhání" proto, pokud server nebo uzel selže, jejích služeb a kontejnery přesune do jiného serveru hostitele nebo virtuálního počítače. V takovém případě musíte pokročilejší technologie, jako je kontejner clustery, orchestrators a plánovače. Proto je způsob, jak nasadit do těchto clusterů přesněji prostřednictvím pokročilých scénářích vysvětlené v další části.

### <a name="deploying-complex-docker-applications-to-docker-clusters-dcos-kubernetes-and-docker-swarm"></a>Nasazení aplikací komplexní Docker do clusterů Docker (DC/OS, Kubernetes a Docker Swarm)

Povaze distribuovaných aplikací vyžaduje výpočetní prostředky, které se taky distribuují. Do mají funkce pro produkční škálování, je potřeba mít clustering možnosti, které zajišťují vysokou škálovatelnost a vysokou DOSTUPNOSTÍ na základě ve fondu prostředků.

Můžete nasadit kontejnery ručně do těchto clusterů z rozhraní příkazového řádku nástroje, jako je například Docker Swarm (například pomocí [vytvoření služby docker](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/)) nebo webového uživatelského rozhraní, jako [Mesosphere Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) pro DC/OS clustery, ale měli Rezervujte, který pouze pro testování včasnou nasazení nebo pro účely správy jako škálování na více systémů nebo účely monitorování.

Z hlediska CD a Visual Studio Team Services konkrétně můžete spustit úlohy speciálně učiněna nasazení z vašeho prostředí Visual Studio Team Services Release Management, které bude nasadit kontejnerizované aplikací pro distribuované clustery v Kontejner služby, jak ukazuje následující obrázek 5-9.

![](./media/image9.png)

Obrázek 5 – 9: nasazení distribuované aplikace do kontejneru služby

Na začátku při nasazení v určité clustery nebo orchestrators, tradičně použijete skriptů konkrétní nasazení a mechanismy pro každý orchestrator (tedy Mesosphere DC/OS nebo Kubernetes mechanismů jiné nasazení než Docker a Docker Swarm) místo jednodušší a snadno použitelné docker tvoří nástroj podle definice soubor docker-compose.yml. Však díky úlohy nasazení webu společnosti Microsoft Visual Studio Team Services Docker, zobrazí obrázek 5-10 nyní také můžete nasadit na DC/OS právě pomocí souboru známé docker-compose.yml, protože Microsoft provádí pro vás tento "překlad" (z vaší soubor docker-compose.yml do jiných formátů vyžaduje DC/OS).

![](./media/image10.png)

Obrázek 5-10: Přidání úloha Docker nasazení do vašeho prostředí RM

Obrázek 5-11 ukazuje, jak můžete upravit úloha Docker nasazení a zadat typ cíle (Azure Container Service DC/OS, v tomto případě), váš soubor Docker Compose a připojení k registru Docker (např. Azure kontejneru registru nebo úložiště Docker Hub). Toto je, kde úloha načte připravené k použití vlastních Docker bitových kopií pro nasazení jako kontejnery v clusteru DC/OS.

![](./media/image11.png)

Obrázek 5 – 11: Docker nasazení úloh definice nasazení Azure Container Service DC/OS

**Další informace o** Další informace o kanálu disku CD s Visual Studio Team Services a Docker, najdete na následujících stránkách:

Rozšíření sady Visual Studio Team Services pro Docker a Azure Container Service: [ https://aka.ms/\ vstsdockerextension](https://aka.ms/vstsdockerextension)

Azure Container Service: <https://aka.ms/azurecontainerservice>

Mesosphere DC/OS: <https://mesosphere.com/product/>

## <a name="step-5-run-and-manage"></a>Krok 5: Spuštění a Správa

Vzhledem k tomu spouštění a správu aplikací v podniku produkční úroveň je hlavní předmět při sám sebe a z důvodu typ operace a lidí pracujících na této úrovni (IT oddělení) a také velký rozsah této oblasti, budeme mít odeberte celý další kapitoly k vysvětlením ho.

## <a name="step-6-monitor-and-diagnose"></a>Krok 6: Sledování a Diagnostika

Toto téma taky je popsaná v další kapitoly jako součást úlohy, které IT oddělení provádí v produkční systémy; je ale důležité ukázat, že statistiky získat v tomto kroku musí kanálu zpět do vývojového týmu tak, aby je neustále vylepšené aplikace. Z tohoto hlediska, je také součástí DevOps, i když operace a úlohy jsou obvykle provádí IT.

Jenom v případě, že monitorování a Diagnostika jsou 100 procent v rámci sféru DevOps jsou monitorování procesů a analýzy provádí vývojový tým, proti prostředí testování nebo beta. To se provádí tak, že provedete zátěžové testování nebo jednoduše tak, že monitorování beta nebo QA prostředí, kde beta testery zkoušíte nové verze.

>[!div class="step-by-step"]
[Předchozí] (index.md) [Další] (.. /Run-Manage-monitor-docker-Environments/index.MD)
