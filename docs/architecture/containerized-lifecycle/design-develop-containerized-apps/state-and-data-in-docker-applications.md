---
title: Stav a data v aplikacích Dockeru
description: Naučte se dostupnou možnost uložit stav v kontejnerizovaných aplikacích.
ms.date: 02/15/2019
ms.openlocfilehash: b2368efb0eff2bdce48b77b2addcc4de89822c74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394645"
---
# <a name="state-and-data-in-docker-applications"></a>Stav a data v aplikacích Dockeru

Ve většině případů si můžete myslet kontejner jako instanci procesu. Proces neudržuje trvalý stav. Zatímco kontejner může zapisovat do místního úložiště, za předpokladu, že instance bude po neomezenou dobu, je jako za předpokladu, že jedno umístění v paměti bude trvalé. Kontejnerové obrazy, stejně jako procesy, by měly mít více instancí a že budou nakonec zabity; Pokud jsou spravované pomocí orchestrátoru kontejneru, je třeba předpokládat, že se můžou přesunout z jednoho uzlu nebo virtuálního uživatele do jiného.

Následující řešení se používají ke správě trvalých dat v aplikacích Dockeru:

Z hostitele Dockeru jako [svazky Dockeru](https://docs.docker.com/engine/admin/volumes/):

- **Svazky** jsou uloženy v oblasti hostitelského souborového systému, který je spravován Dockerem.

- **Připojení vazby** lze mapovat na libovolnou složku v hostitelském souborovém systému, takže přístup nelze řídit z procesu Dockeru a může představovat bezpečnostní riziko, protože kontejner může přistupovat k citlivým složkám operačního systému.

- **tmpfs připojení** jsou jako virtuální složky, které existují pouze v paměti hostitele a nejsou nikdy zapsány do souborového systému.

Ze vzdáleného úložiště:

- [Azure Storage](https://azure.microsoft.com/documentation/services/storage/) poskytuje geograficky distribuovatelné úložiště a poskytuje dobré dlouhodobé řešení trvalosti pro kontejnery.

- Vzdálené relační databáze, jako je [Azure SQL Database](https://azure.microsoft.com/services/sql-database/), NoSQL databáze jako Azure [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction)nebo služby mezipaměti jako [Redis](https://redis.io/).

Z kontejneru Dockeru:

- Docker poskytuje funkci s názvem *systém souborů překrytí*. Tato funkce implementuje úlohu kopírování při zápisu, která ukládá aktualizované informace do kořenového systému souborů kontejneru. Tato informace "položí na" původní obrázek, na kterém je kontejner založen. Pokud je kontejner odstraněn ze systému, tyto změny budou ztraceny. Proto i když je možné uložit stav kontejneru v rámci místního úložiště, navrhování systému založeného na této funkci by bylo v konfliktu s předpokladem návrhu kontejneru, který je ve výchozím nastavení bezstavový.

- Svazky Dockeru je však nyní upřednostňovaný způsob zpracování místních dat v Dockeru. Pokud potřebujete další informace o úložišti v kontejnerech, zkontrolujte [ovladače úložiště Dockeru](https://docs.docker.com/engine/userguide/storagedriver/) a [ovladače úložiště O ifotkách, kontejnerech a ovladačích úložiště](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).

Následující obsahuje další podrobnosti o těchto možnostech.

**Svazky** jsou adresáře mapované z hostitelského operačního režimu na adresáře v kontejnerech. Pokud kód v kontejneru má přístup k adresáři, tento přístup je ve skutečnosti do adresáře v hostitelském os. Tento adresář není vázán na životnost samotného kontejneru a adresář je spravován Dockerem a izolován od základních funkcí hostitelského počítače. Objemy dat jsou proto navrženy tak, aby uchovávají data nezávisle na životnosti kontejneru. Pokud odstraníte kontejner nebo bitovou kopii z hostitele Dockeru, data trvalá ve svazku dat se neodstraní.

Svazky lze pojmenovat nebo anonymně (výchozí). Pojmenované svazky jsou vývoj **kontejnerů svazků dat** a usnadňují sdílení dat mezi kontejnery. Svazky také podporují ovladače svazků, které umožňují mimo jiné ukládat data na vzdálených hostitelích.

**Připojení vazeb** jsou k dispozici po dlouhou dobu a umožňují mapování libovolné složky na přípojný bod v kontejneru. Připojení vazeb mají více omezení než svazky a některé důležité problémy se zabezpečením, takže svazky jsou doporučenou možností.

připojí jsou virtuální složky, které žijí pouze v paměti hostitele a nejsou nikdy zapsány do souborového systému. ** `tmpfs` ** Jsou rychlé a bezpečné, ale používají paměť a jsou určeny pouze pro netrvalá data.

Jak je znázorněno na obrázku 4-5, běžné svazky Dockeru mohou být uloženy mimo samotné kontejnery, ale v rámci fyzických hranic hostitelského serveru nebo virtuálního počítače. Kontejnery Dockeru však nemají přístup ke svazku z jednoho hostitelského serveru nebo virtuálního serveru do jiného. Jinými slovy, s těmito svazky není možné spravovat data sdílená mezi kontejnery, které běží na různých hostitelích Dockeru, i když toho lze dosáhnout pomocí ovladače svazku, který podporuje vzdálené hostitele.

![Diagram znázorňující svazky Dockeru uložené mimo kontejnery.](./media/state-and-data-in-docker-applications/container-based-application-external-data-sources.png)

**Obrázek 4-5**. Svazky a externí zdroje dat pro aplikace založené na kontejnerech

Kromě toho při dockeru kontejnery jsou spravovány orchestrator, kontejnery může "přesunout" mezi hostiteli, v závislosti na optimalizace prováděné clusteru. Proto se nedoporučuje používat datové svazky pro obchodní data. Ale jsou dobrým mechanismem pro práci se soubory trasování, časovými soubory nebo podobnými soubory, které nebudou mít vliv na konzistenci obchodních dat.

Vzdálené zdroje dat a nástroje **mezipaměti,** jako je Azure SQL Database, Azure Cosmos DB nebo vzdálená mezipaměť, jako je Redis, se dají používat v kontejnerizovaných aplikacích stejným způsobem, jako se používají při vývoji bez kontejnerů. Toto je osvědčený způsob ukládání dat obchodních aplikací.

**Azure Storage.** Obchodní data obvykle musí být umístěna v externích prostředků nebo databází, jako je Azure Storage. Azure Storage poskytuje v cloudu následující služby:

- Úložiště objektů blob ukládá nestrukturovaná data objektů. Objekt blob může být libovolný typ textu nebo binárních dat, například soubory dokumentů nebo médií (obrázky, zvuk a video soubory). Blob Storage se taky může říkat Úložiště objektů.

- Úložiště souborů nabízí sdílené úložiště pro starší aplikace používající standardní protokol SMB. Virtuální počítače Azure a cloudové služby můžou sdílet data souborů napříč součástmi aplikací prostřednictvím připojených sdílených složek. Místní aplikace mohou přistupovat k datům souborů ve sdílené složce prostřednictvím rozhraní REST API souborové služby.

- Úložiště tabulek ukládá strukturované datové sady. Table storage je úložiště dat nosql key-attribute, které umožňuje rychlý vývoj a rychlý přístup k velkému množství dat.

**Relační databáze a NoSQL databáze.** Existuje mnoho možností pro externí databáze, z relačních databází, jako je SQL Server, PostgreSQL, Oracle nebo NoSQL databáze jako Azure Cosmos DB, MongoDB atd. Tyto databáze nebudou vysvětleny jako součást této příručky, protože se jedná o úplně jiné téma.

>[!div class="step-by-step"]
>[Předchozí](monolithic-applications.md)
>[další](soa-applications.md)
