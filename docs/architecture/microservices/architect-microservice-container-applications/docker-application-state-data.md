---
title: Stav a data v aplikacích Docker
description: Správa stavu a dat v Docker aplikacích. Instance mikroslužeb jsou vynaloženy, ale DATA nejsou, jak je zpracovat pomocí mikroslužeb.
ms.date: 09/20/2018
ms.openlocfilehash: 193ac143ca0cc42c248f449b1e1a1339af6f69d1
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834431"
---
# <a name="state-and-data-in-docker-applications"></a>Stav a data v aplikacích Docker

Ve většině případů si můžete kontejner představit jako instanci procesu. Proces neudržuje trvalý stav. I když kontejner může zapisovat do svého místního úložiště za předpokladu, že instance bude v neomezenou dobu považována za předpokladu, že jedno umístění v paměti bude trvalé. Doporučujeme předpokládat, že image kontejneru, jako jsou procesy, mají více instancí, nebo nakonec budou ukončeny. Pokud jsou spravované pomocí produktu Orchestrator, měli byste předpokládat, že se můžou přesunout z jednoho uzlu nebo virtuálního počítače do jiného.

Pro správu trvalých dat v aplikacích Docker slouží následující řešení:

Z hostitele Docker jako [svazky Docker](https://docs.docker.com/engine/admin/volumes/):

- **Svazky** se ukládají v oblasti hostitelského systému, který je spravovaný přes Docker.

- **Připojení typu bind** lze namapovat na libovolnou složku v systému souborů hostitele, takže přístup nelze ovládat z procesu Docker a může představovat bezpečnostní riziko, protože kontejner by měl přístup k citlivým složkám operačního systému.

- **tmpfs připojení** jsou jako virtuální složky, které existují pouze v paměti hostitele a nejsou nikdy zapsány do systému souborů.

Ze vzdáleného úložiště:

- [Azure Storage](https://azure.microsoft.com/documentation/services/storage/), která poskytuje geografické úložiště, poskytující dobré dlouhodobé řešení trvalosti pro kontejnery.

- Vzdálené relační databáze, jako jsou [Azure SQL Database](https://azure.microsoft.com/services/sql-database/) nebo NoSQL databáze jako [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction), nebo služby pro ukládání do mezipaměti, jako je [Redis](https://redis.io/).

Z kontejneru Docker:

> Docker poskytuje funkci s názvem *Překryvný systém souborů*. Tím se implementuje úloha kopírování a zápis, která ukládá aktualizované informace do kořenového systému souborů kontejneru. Tyto informace jsou kromě původního obrázku, na kterém je kontejner založen. Pokud se kontejner odstraní ze systému, tyto změny se ztratí. Proto je možné uložit stav kontejneru v rámci svého místního úložiště. návrh systému kolem tohoto by byl v konfliktu s interním návrhem kontejneru, který ve výchozím nastavení je bezstavový.
>
> Dříve zavedené svazky Docker jsou teď preferovaným způsobem pro zpracování místních dat Docker. Pokud potřebujete další informace o úložišti v kontejnerech, podívejte se na [ovladače úložiště Docker](https://docs.docker.com/storage/storagedriver/select-storage-driver/) a na [ovladače úložiště](https://docs.docker.com/storage/storagedriver/).

Následující informace obsahují další podrobnosti o těchto možnostech:

**Svazky** jsou adresáře mapované z HOSTITELSKÉHO operačního systému na adresáře v kontejnerech. Pokud má kód v kontejneru přístup k adresáři, je tento přístup ve skutečnosti adresářem v hostitelském operačním systému. Tento adresář není svázán s životností kontejneru samotného a adresář je spravován nástrojem Docker a izolované od základní funkce hostitelského počítače. Proto jsou datové svazky navrženy tak, aby zachovaly data nezávisle na životnosti kontejneru. Pokud odstraníte kontejner nebo bitovou kopii z hostitele Docker, data, která jsou uložena v datovém svazku, se neodstraní.

Svazky mohou být pojmenované nebo anonymní (výchozí). Pojmenované svazky představují vývoj **kontejnerů datových svazků** a usnadňují sdílení dat mezi kontejnery. Svazky také podporují ovladače svazků, které umožňují ukládat data na vzdálené hostitele kromě dalších možností.

**Připojení BIND** jsou k dispozici po dlouhou dobu a umožňují mapování kterékoli složky na přípojný bod v kontejneru. Připojení vazby mají větší omezení než svazky a některé důležité problémy se zabezpečením, takže svazky jsou doporučenými možnostmi.

**tmpfs připojení** jsou v podstatě virtuální složky, které jsou živě pouze v paměti hostitele a nejsou nikdy zapsány do systému souborů. Jsou rychlé a bezpečné, ale používají paměť a jsou určeny pouze pro netrvalá data.

Jak je znázorněno na obrázku 4-5, běžné svazky Docker lze ukládat mimo samotné kontejnery, ale v rámci fyzických hranic hostitelského serveru nebo virtuálního počítače. Kontejnery Docker ale nemají přístup ke svazku z jednoho hostitelského serveru nebo virtuálního počítače do jiného. Jinými slovy, u těchto svazků není možné spravovat data sdílená mezi kontejnery, které běží na různých hostitelích Docker, i když se dá dosáhnout pomocí ovladače svazku, který podporuje vzdálené hostitele.

![Diagram znázorňující svazky a externí zdroje dat pro aplikace založené na kontejnerech](./media/docker-application-state-data/volumes-external-data-sources.png)

**Obrázek 4-5**. Svazky a externí zdroje dat pro aplikace založené na kontejnerech

Svazky lze sdílet mezi kontejnery, ale pouze ve stejném hostiteli, pokud nepoužíváte vzdálený ovladač, který podporuje vzdálené hostitele. Kromě toho, když jsou kontejnery Docker spravovány nástrojem Orchestrator, kontejnery se mohou pohybovat mezi hostiteli v závislosti na optimalizacích prováděných clusterem. Proto se nedoporučuje používat datové svazky pro obchodní data. Jsou však dobrým mechanismem pro práci s trasovacími soubory, dočasnými soubory nebo podobnými, které nebudou mít vliv na konzistenci obchodních dat.

**Vzdálené zdroje dat a** nástroje pro ukládání do mezipaměti, jako je Azure SQL Database, Azure Cosmos DB nebo Vzdálená mezipaměť, jako je Redis, se dají použít v kontejnerových aplikacích stejným způsobem jako při vývoji bez kontejnerů. Toto je prověřený způsob, jak ukládat data obchodních aplikací.

**Azure Storage.** Podniková data se obvykle musí umístit do externích prostředků nebo databází, jako je Azure Storage. Azure Storage v betonu poskytuje následující služby v cloudu:

- Úložiště objektů BLOB ukládá nestrukturovaná data objektů. Objekt BLOB může být libovolný typ textu nebo binárních dat, jako je například dokument nebo mediální soubory (obrázky, zvukové soubory a videosoubory). Blob Storage se taky může říkat Úložiště objektů.

- Úložiště souborů nabízí sdílené úložiště pro starší verze aplikací, které používají standardní protokol SMB. Virtuální počítače a cloudové služby Azure můžou sdílet souborová data mezi komponentami aplikace přes připojené sdílené složky. Místní aplikace můžou k souborovým datům ve sdílené složce přistupovat prostřednictvím souborové služby REST API.

- Úložiště tabulek ukládá strukturované datové sady. Table Storage je úložiště dat NoSQL klíčového atributu, které umožňuje rychlý vývoj a rychlý přístup k velkým objemům dat.

**Relační databáze a databáze NoSQL.** K dispozici je celá řada možností pro externí databáze, od relačních databází, jako jsou SQL Server, PostgreSQL, Oracle nebo databáze NoSQL, jako jsou Azure Cosmos DB, MongoDB atd. Tyto databáze nebudou v rámci tohoto průvodce vysvětleny, protože jsou v naprosto jiném předmětu.

>[!div class="step-by-step"]
>[Předchozí](containerize-monolithic-applications.md)@no__t – 1 –[Další](service-oriented-architecture.md)
