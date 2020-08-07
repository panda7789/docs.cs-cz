---
title: Stav a data v aplikacích Dockeru
description: Seznamte se s možností dostupnosti pro uložení stavu v kontejnerových aplikacích.
ms.date: 08/06/2020
ms.openlocfilehash: dc9a1a3eccb77e9fd67e69fd3295f3db1edf5e66
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915332"
---
# <a name="state-and-data-in-docker-applications"></a>Stav a data v aplikacích Dockeru

Ve většině případů si můžete kontejner představit jako instanci procesu. Proces neudržuje trvalý stav. I když kontejner může zapisovat do svého místního úložiště, za předpokladu, že instance bude přibližně neomezená, například za předpokladu, že jedno umístění v paměti bude trvalé. Image kontejneru, jako jsou procesy, by se měly předpokládat, že mají více instancí a že se nakonec budou usmrceny. Pokud jsou spravované pomocí kontejneru Orchestrator, měl by se předpokládat, že se můžou přesunout z jednoho uzlu nebo virtuálního počítače do jiného.

Pro správu trvalých dat v aplikacích Docker slouží následující řešení:

Z hostitele Docker jako [svazky Docker](https://docs.docker.com/engine/admin/volumes/):

- **Svazky** se ukládají v oblasti hostitelského systému, který je spravovaný přes Docker.

- **Připojení typu bind** lze namapovat na libovolnou složku v systému souborů hostitele, takže přístup nelze ovládat z procesu Docker a může představovat bezpečnostní riziko, protože kontejner by měl přístup k citlivým složkám operačního systému.

- **tmpfs připojení** jsou jako virtuální složky, které existují pouze v paměti hostitele a nejsou nikdy zapsány do systému souborů.

Ze vzdáleného úložiště:

- [Azure Storage](https://azure.microsoft.com/documentation/services/storage/) poskytuje geograficky Distribuovatelný úložiště, které poskytuje dobré dlouhodobé řešení trvalého uložení pro kontejnery.

- Vzdálené relační databáze, jako je [Azure SQL Database](https://azure.microsoft.com/services/sql-database/), databáze NoSQL jako [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction)nebo služby pro ukládání do mezipaměti, jako je [Redis](https://redis.io/).

Z kontejneru Docker:

- Docker poskytuje funkci s názvem *Překryvný systém souborů*. Tato funkce implementuje úlohu kopírování na zápis, která ukládá aktualizované informace do kořenového systému souborů kontejneru. Tyto informace "se týkají" původního obrázku, na kterém je kontejner založen. Pokud se kontejner odstraní ze systému, tyto změny se ztratí. Proto je možné uložit stav kontejneru v rámci svého místního úložiště. návrh systému na základě této funkce by byl v konfliktu s interním návrhem kontejneru, který je ve výchozím nastavení v pořádku.

- Teď jsou ale dokovací svazky v Docker preferovaným způsobem, jak zpracovávat místní data v Docker. Pokud potřebujete další informace o úložišti v kontejnerech, podívejte se na [ovladače úložiště Docker](https://docs.docker.com/engine/userguide/storagedriver/) a [o imagí, kontejnerech a ovladačích úložiště](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).

Následující informace obsahují další podrobnosti o těchto možnostech.

**Svazky** jsou adresáře mapované z HOSTITELSKÉHO operačního systému na adresáře v kontejnerech. Pokud má kód v kontejneru přístup k adresáři, je tento přístup ve skutečnosti adresářem v hostitelském operačním systému. Tento adresář není svázán s životností kontejneru samotného a adresář je spravován nástrojem Docker a izolované od základní funkce hostitelského počítače. Proto jsou datové svazky navrženy tak, aby zachovaly data nezávisle na životnosti kontejneru. Pokud odstraníte kontejner nebo image z hostitele Docker, data, která jsou trvale uložena v datovém svazku, nebudou odstraněna.

Svazky mohou být pojmenované nebo anonymní (výchozí). Pojmenované svazky představují vývoj **kontejnerů datových svazků** a usnadňují sdílení dat mezi kontejnery. Svazky také podporují ovladače svazků, které umožňují ukládat data na vzdálené hostitele kromě dalších možností.

**Připojení k vazbě** byla k dispozici po dlouhou dobu a umožňují mapování kterékoli složky na přípojný bod v kontejneru. Připojení vazby mají větší omezení než svazky a některé důležité problémy se zabezpečením, takže svazky jsou doporučenými možnostmi.

** `tmpfs` připojení** jsou virtuální složky, které jsou živě pouze v paměti hostitele a nejsou nikdy zapsány do systému souborů. Jsou rychlé a bezpečné, ale používají paměť a jsou určeny pouze pro netrvalá data.

Jak je znázorněno na obrázku 4-5, běžné svazky Docker lze ukládat mimo samotné kontejnery, ale v rámci fyzických hranic hostitelského serveru nebo virtuálního počítače. Kontejnery Docker ale nemají přístup ke svazku z jednoho hostitelského serveru nebo virtuálního počítače do jiného. Jinými slovy, u těchto svazků není možné spravovat data sdílená mezi kontejnery, které běží na různých hostitelích Docker, i když se dá dosáhnout pomocí ovladače svazku, který podporuje vzdálené hostitele.

![Diagram znázorňující svazky Docker uložené mimo kontejnery.](./media/state-and-data-in-docker-applications/container-based-application-external-data-sources.png)

**Obrázek 4-5**. Svazky a externí zdroje dat pro aplikace založené na kontejnerech

Kromě toho, když jsou kontejnery Docker spravovány nástrojem Orchestrator, kontejnery se mohou pohybovat mezi hostiteli v závislosti na optimalizacích prováděných clusterem. Proto se nedoporučuje používat datové svazky pro obchodní data. Jsou však dobrým mechanismem pro práci s trasovacími soubory, dočasnými soubory nebo podobnými, které nebudou mít vliv na konzistenci obchodních dat.

**Vzdálené zdroje dat a** nástroje pro ukládání do mezipaměti, jako je Azure SQL Database, Azure Cosmos DB nebo Vzdálená mezipaměť, jako je Redis, se dají použít v kontejnerových aplikacích stejným způsobem jako při vývoji bez kontejnerů. Toto je prověřený způsob, jak ukládat data obchodních aplikací.

**Azure Storage.** Obchodní data se obvykle musí umístit do externích prostředků nebo databází, jako je Azure Storage. Azure Storage poskytuje v cloudu následující služby:

- Úložiště objektů BLOB ukládá nestrukturovaná data objektů. Objekt BLOB může být libovolný typ textu nebo binárních dat, jako je například dokument nebo mediální soubory (obrázky, zvukové soubory a videosoubory). Blob Storage se taky může říkat Úložiště objektů.

- Úložiště souborů nabízí sdílené úložiště pro starší verze aplikací, které používají standardní protokol SMB. Virtuální počítače a cloudové služby Azure můžou sdílet souborová data mezi komponentami aplikace přes připojené sdílené složky. Místní aplikace můžou k souborovým datům ve sdílené složce přistupovat prostřednictvím souborové služby REST API.

- Tabulkové úložiště slouží k ukládání strukturovaných datových sad. Table Storage je úložiště dat NoSQL klíčového atributu, které umožňuje rychlý vývoj a rychlý přístup k velkým objemům dat.

**Relační databáze a databáze NoSQL.** K dispozici je celá řada možností pro externí databáze, od relačních databází, jako jsou SQL Server, PostgreSQL, Oracle nebo databáze NoSQL, jako jsou Azure Cosmos DB, MongoDB atd. Tyto databáze nebudou v rámci tohoto průvodce vysvětleny, protože se jedná o jiné téma úplně.

>[!div class="step-by-step"]
>[Předchozí](monolithic-applications.md) 
> [Další](soa-applications.md)
