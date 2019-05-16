---
title: Stav a data v aplikacích Dockeru
description: Stav a správu dat v aplikacích Dockeru. Instance Mikroslužeb jsou postradatelnými, ale DATA nejsou, jak o to postarají s využitím mikroslužeb.
ms.date: 09/20/2018
ms.openlocfilehash: 9d7b0ff0e73267c6b80be2f1c956c3b4eae140e2
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641368"
---
# <a name="state-and-data-in-docker-applications"></a>Stav a data v aplikacích Dockeru

Ve většině případů si můžete představit kontejneru jako instance procesu. Proces nemá udržovat trvalý stav. Zatímco kontejner může zapisovat do své místní úložiště, za předpokladu, že instance bude po neomezeně dlouho by například za předpokladu, že bude trvalý jednoho umístění v paměti. Byste měli předpokládat, že Image kontejneru, jako jsou procesy, máte více instancí nebo nakonec budou ukončeny. Pokud jsou spravovaná pomocí orchestrátoru kontejneru byste měli předpokládat, že se může získat přesouvat z jednoho uzlu nebo virtuální počítač do druhého.

Následující řešení se používají ke správě trvalá data v aplikacích Dockeru:

Z hostitele Docker jako [Docker svazky](https://docs.docker.com/engine/admin/volumes/):

- **Svazky** jsou uloženy v oblasti systému souborů hostitele, který je spravovaný nástrojem Docker.

- **Navázat připojení** můžete namapovat na libovolnou složku v systému souborů hostitele, takže nemůže být řízený z procesu Docker přístup a může představovat bezpečnostní riziko, protože kontejner může přístup ke složkám na citlivé operačního systému.

- **připojí tmpfs** jsou například virtuální složky, které jenom v paměti hostiteli existují a nikdy se zapisují do systému souborů.

Ze vzdáleného úložiště:

- [Azure Storage](https://azure.microsoft.com/documentation/services/storage/), který poskytuje geo Distribuovatelný storage, která poskytuje dobré dlouhodobým řešením trvalosti pro kontejnery.

- Vzdálené relační databáze, jako jsou [Azure SQL Database](https://azure.microsoft.com/services/sql-database/) nebo databáze NoSQL, jako jsou [služby Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction), nebo službám, jako je do mezipaměti [Redis](https://redis.io/).

Z kontejneru Dockeru:

> Docker nabízí funkci s názvem *překryv systému souborů*. To implementuje úlohu kopírování na zápis, že úložiště aktualizované informace o kořenové systému souborů kontejneru. Tyto informace je navíc k původní bitové kopie, na kterých je založena kontejner. Pokud kontejner je ze systému odstraněn, tyto změny budou ztraceny. Proto i když je možné uložit stav kontejneru v rámci své místní úložiště, návrhu systému tomuto by vznikl konflikt se místní kontejner návrh, který ve výchozím nastavení jsou bezstavové.
>
> Dříve uvedených svazky Dockeru je však nyní preferovaný způsob, jak zpracování místních dat Dockeru. Pokud potřebujete další informace o službě storage v kontejnerech, zkontrolujte na [ovladačů úložiště Dockeru](https://docs.docker.com/storage/storagedriver/select-storage-driver/) a [o ovladačích úložiště](https://docs.docker.com/storage/storagedriver/).

Následují další podrobnosti o těchto možnostech:

**Svazky** jsou adresáře, které jsou namapované na adresáře v kontejnerech z hostitelského operačního systému. Pokud má kód v kontejneru přístup k adresáři, který ve skutečnosti je přístup k adresáři na hostitelském operačním systému. Tento adresář se neváže k době života kontejner sám o sobě, a adresář je spravovaný nástrojem Docker a izolovaně od základní funkce hostitelského počítače. Proto datové svazky jsou navržené k uchování dat bez ohledu na jejich životnosti kontejneru. Pokud odstraníte kontejner nebo bitové kopie z hostitele Docker dat uchovávaných v objem dat se neodstraní.

Svazky mohou být pojmenované a anonymní (výchozí). Vývoj jsou pojmenované svazky **kontejnery svazků Data** a usnadňují sdílení dat mezi kontejnery. Svazky také podporu ovladačů svazků, které vám umožňují ukládat data na vzdáleného hostitele, mezi další možnosti.

**Navázat připojení** jsou k dispozici od dlouhou dobou a umožňují mapování všechny složky přípojný bod v kontejneru. Vazby připojení mít další omezení než svazky a některé problémy se zabezpečením důležité, proto doporučujeme jsou svazky.

**připojí tmpfs** jsou v podstatě virtuální složky, které live pouze v paměti hostitele a nikdy se zapisují do systému souborů. Jsou rychlé a zabezpečené, ale používají paměti a jsou určeny pouze pro dočasné data.

Jak ukazuje obrázek 4 – 5, pravidelné Docker svazky mohou být uloženy mimo kontejnery sami, ale v rámci fyzické hranice hostitelský server nebo virtuální počítač. Ale kontejnerů Dockeru od nemají přístup k svazku jeden hostitelský server nebo virtuální počítač do jiného. Jinými slovy tyto svazky, není možné spravovat data sdílena mezi kontejnerů, které běží na různých hostitelích, Docker, i když ho lze dosáhnout pomocí ovladače svazku, který podporuje vzdáleného hostitele.

![Svazky lze sdílet mezi kontejnery, ale jenom do stejného hostitele, pokud nechcete použít vzdálené ovladač, který podporuje vzdálené hostitele. ](./media/image5.png)

**Obrázek 4 až 5**. Svazky a externích zdrojů dat pro aplikace založené na kontejnerech

Navíc když kontejnery Dockeru jsou spravovaná pomocí orchestrátoru, kontejnery může "Přesun" mezi hostiteli, v závislosti na optimalizace prováděné v clusteru. Proto se nedoporučuje používat datové svazky pro obchodní data. Ale jsou dobrým mechanismus pro práci se soubory trasování, dočasné soubory, nebo podobné neovlivní konzistence obchodní data.

**Vzdálené zdroje dat. a mezipaměti** nástrojů, jako je Azure SQL Database, Azure Cosmos DB nebo vzdálené mezipaměti, jako jsou Redis je možné v stejným způsobem se používají při vývoji bez kontejnery kontejnerizovaných aplikací. Toto je což je osvědčený způsob k ukládání dat obchodní aplikace.

**Azure Storage.** Obchodní data obvykle je nutné umístit do externího zdroje nebo databáze, jako je Azure Storage. Služba Azure Storage v konkrétní, poskytuje tyto služby v cloudu:

- BLOB storage ukládá nestrukturované datové objekty. Objekt blob může být jakýkoli typ textových nebo binárních dat, jako je například dokumentu nebo média (soubory obrázků, zvuku a videa). Úložiště objektů blob se taky označuje jako úložiště objektů.

- File storage nabízí sdílené úložiště pro starší verze aplikace používající standardní protokol SMB. Virtuální počítače Azure a cloudové služby můžou sdílet souborová data mezi komponentami aplikace přes sdílené složky. Místní aplikace můžou k souborovým datům ve sdílené složce, prostřednictvím rozhraní REST API služby File.

- Table storage ukládá strukturované datové sady. Úložiště Table je úložiště dat klíč atribut NoSQL, která umožňuje rychlý vývoj a přístup k velkým objemům dat.

**Relační databáze a databáze NoSQL.** Existuje mnoho možností pro externí databáze, od relačních databází, jako jsou SQL Server, PostgreSQL, Oracle nebo NoSQL databáze jako služby Azure Cosmos DB, MongoDB atd. Tyto databáze nebudou vysvětlené v rámci tohoto průvodce, protože jsou v úplně jiných předmětu.

>[!div class="step-by-step"]
>[Předchozí](containerize-monolithic-applications.md)
>[další](service-oriented-architecture.md)
