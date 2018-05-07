---
title: Terminologie docker
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Terminologie docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 9bbeff8c467e762e682fdaf99c8a11851b291db8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="docker-terminology"></a>Terminologie docker

Tato část uvádí termíny a definice, které byste měli být před získáním hlubší do Docker znají. Pro další definice, najdete v článku rozsáhlé [Glosář](https://docs.docker.com/glossary/) poskytované Docker.

**Kontejner image**: balíček se všechny závislosti a informace potřebné k vytvoření kontejneru. Obrázek zahrnuje všechny závislosti (například rozhraní) plus konfigurace nasazení a spuštění má být používána runtime kontejneru. Obvykle bitovou kopii je odvozena z více základní bitové kopie, které jsou vrstvy sebe k vytvoření kontejneru systému souborů. Obrázek je nezměnitelná, po vytvoření.

**Kontejner**: instance Docker bitové kopie. Kontejner představuje spuštění jednu aplikaci, procesu nebo služby. Skládá se z obsah bitovou kopii Docker, prostředí pro spuštění a standardní sadu pokynů. Když škálování služby, můžete vytvořit více instancí kontejner ze stejné image. Nebo dávkovou úlohu můžete vytvořit více kontejnerů ze stejné image, předávání různé parametry pro každou instanci.

**Značka**: značka nebo popisek lze použít pro obrázky, takže lze identifikovat různé obrázky nebo verzích stejnou bitovou kopii (v závislosti na číslo verze nebo cílovém prostředí).

**Soubor Docker**: textový soubor, který obsahuje pokyny k sestavení Docker bitové kopie.

**Sestavení**: akci vytváření obrazem kontejneru na základě informací a kontext poskytované jeho soubor Docker, plus další soubory ve složce, ve kterém je sestavena bitovou kopii. Můžete vytvořit Image pomocí příkazu Docker docker sestavení.

**Úložiště (úložiště)**: kolekce souvisejících imagí Dockeru s názvem bez přípony se značkou, která označuje verzi bitové kopie. Některé úložiště obsahovat více variant konkrétní image, jako je například bitové kopie obsahující bitovou kopii obsahující pouze moduly runtime (světlejší) sady SDK (těžší), atd. Těchto variant může být označen značky. Jednoho úložiště může obsahovat variant platformy, jako je například bitovou kopii systému Linux a bitové kopie systému Windows.

**Registru**: služba, která poskytuje přístup k úložiště. Je výchozím nastavení registru pro nejvíce veřejné bitové kopie [úložiště Docker Hub](https://hub.docker.com/) (vlastníkem Docker organizace). Registru obvykle obsahuje úložiště od více týmů. Společnosti musí často privátní registrech k ukládání a správě bitových kopií, které jste sami vytvořili. Azure registru kontejneru je další příklad.

**Úložiště docker Hub**: veřejné registru nahrát bitové kopie a pracovat s nimi. Úložiště docker Hub poskytuje Docker hostování bitové kopie, registrech veřejných nebo privátních, aktivační události sestavení a webové háky a integrace s Githubu a Bitbucket.

**Azure kontejneru registru**: prostředek veřejné pro práci s imagí Dockeru a jeho komponenty v Azure. To poskytuje registr, která je blízko svá nasazení v Azure a udávající řízení přístupu, aby bylo možné pomocí skupin Azure Active Directory a oprávnění.

**Docker důvěryhodné registru (DTR)**: A Docker služba registru (z Docker), která může být nainstalován na místě, a proto je umístěn v rámci datového centra a sítě organizace. Je vhodné pro privátní bitové kopie, které se mají spravovat v rámci podniku. Docker důvěryhodné registru je součástí produktu Docker Datacenter. Další informace najdete v tématu [Docker důvěryhodné registru (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE)**: nástroje pro vývoj pro systém Windows a systému macOS pro vytváření, spouštění a testování kontejnery místně. CE docker pro systém Windows poskytuje vývojové prostředí pro Linux a Windows kontejnery. Je na základě hostitelů Linux Docker v systému Windows [technologie Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) virtuálního počítače. Hostitel pro kontejnery Windows je přímo založená na systému Windows. Docker CE pro Mac je založené na rozhraní framework Apple hypervisoru a [xhyve hypervisoru](https://github.com/mist64/xhyve), který poskytuje Linux Docker hostitele virtuálního počítače Mac OS X. Docker CE pro systém Windows a Mac nahrazuje Docker sada nástrojů, která je založena na Oracle VirtualBox.

**Docker Enterprise Edition (EE)**: na podnikovém měřítku verzi Docker nástroje pro vývoj pro Linux a Windows.

**Napište**: nástroj příkazového řádku a YAML souboru formátu s metadaty pro definování a spouštění aplikací více kontejneru. Můžete definovat jednu aplikaci založené na více bitových kopií se jeden nebo více .yml soubory, které můžete přepsat hodnoty v závislosti na prostředí. Po vytvoření definice, můžete nasadit aplikace celý více kontejnerů pomocí jednoho příkazu (docker-tvoří nahoru) na hostiteli Docker vytvářející kontejner pro bitovou kopii.

**Cluster**: kolekce hostitelů Docker zveřejněné jako by šlo jediného virtuálního Docker hostitele, tak, aby aplikace lze škálovat na více instancí služeb rozloženy víc hostitelích v clusteru. Clustery docker lze vytvořit pomocí Docker Swarm, Mesosphere DC/OS, Kubernetes a Azure Service Fabric. (Pokud používáte Docker Swarm pro správu clusteru, je obvykle podívejte se na clusteru jako *swarm* místo clusteru.)

**Orchestrator**: nástroj, který zjednodušuje správu clusterů a hostitelů Docker. Orchestrators umožňují spravovat jejich obrázků, kontejnery a hostitelů pomocí rozhraní příkazového řádku (CLI) nebo grafického uživatelského rozhraní. Můžete spravovat kontejner sítě, konfigurace, Vyrovnávání zatížení, zjišťování služby, vysokou dostupnost, konfigurace hostitelů Docker a další. Orchestrator je zodpovědná za spuštění, distribuci, škálování a opravy zatížení napříč kolekce uzlů. Produkty orchestrator jsou obvykle stejné produkty, které zajišťují infrastrukturu clusteru, jako je Mesosphere DC/OS, Kubernetes, Docker Swarm a Azure Service Fabric.


>[!div class="step-by-step"]
[Předchozí] (docker-defined.md) [Další] (docker kontejnery Image registries.md)
