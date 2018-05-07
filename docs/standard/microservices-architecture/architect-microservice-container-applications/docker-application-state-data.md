---
title: Stav a data v aplikacích Docker
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Stav a data v aplikacích Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: c5cfe617335d8150d069149ac87f79206b1b5eca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="state-and-data-in-docker-applications"></a>Stav a data v aplikacích Docker

Ve většině případů si můžete představit kontejneru jako instance procesu. Proces neudržuje trvalý stav. Při kontejner může zapsat do své místní úložiště, za předpokladu, že instance bude přibližně po neomezenou dobu bude třeba za předpokladu, že bude jedno umístění v paměti trvanlivý. Kontejner imagí, stejně jako procesy, by měl být předpokládá, že mít více instancí nebo které se budou nakonec ukončeny; Pokud jste se spravovat s nástrojem orchestrator kontejneru, by měl předpokládá, že se může získat z jednoho uzlu nebo virtuální počítač na jiný přesunout.

Docker nabízí funkci s názvem *překrytí systém souborů*. To implementuje úlohu kopírování při zápisu, že úložiště aktualizované informace k systému souborů kořenovém kontejneru. Tyto informace je navíc k původní bitové kopie, na kterých je založena kontejneru. Pokud je ze systému odstraněn kontejneru, tyto změny budou ztraceny. Proto i když je možné uložit stav kontejneru v rámci své místní úložiště, návrhu systému řešení by byl v konfliktu s místní návrhu kontejneru, který ve výchozím nastavení je bezstavové.

Následující řešení se používají ke správě dat v aplikacích Docker:

-   [Datové svazky](https://docs.docker.com/engine/tutorials/dockervolumes/) , připojit k hostiteli.

-   [Kontejnery svazků data](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container) , poskytovat sdílené úložiště mezi kontejnery pomocí externí kontejneru.

-   [Moduly plug-in svazku](https://docs.docker.com/engine/tutorials/dockervolumes/) , připojte svazky, které mají vzdálené poskytuje dlouhodobé trvalost.

-   [Úložiště Azure](https://docs.microsoft.com/azure/storage/), který poskytuje geograficky distribuovatelného úložiště, poskytuje dobrým řešením dlouhodobé trvalosti pro kontejnery.

-   Vzdálené relační databáze jako [Azure SQL Database](https://azure.microsoft.com/services/sql-database/) nebo jako databáze NoSQL [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction), nebo do mezipaměti služby, jako je [Redis](https://redis.io/).

Následují další podrobnosti o těchto možnostech.

**Datové svazky** jsou adresáře mapovat z hostitelský operační systém na adresáře v kontejnerech. Když kód v kontejneru má přístup k adresáři, který je ve skutečnosti přístup k adresáři na hostitelský operační systém. Tento adresář není vázaný na dobu životnosti kontejneru samostatně a adresář je přístupná z kód spuštěný přímo na operační systém hostitele nebo v jiném kontejneru který mapuje stejný adresář hostitele na sebe sama. Proto vám datové svazky mají zachovat data nezávisle na dobu životnosti kontejneru. Pokud odstraníte kontejner nebo bitové kopie z hostitelů Docker, data uchovávané v datový svazek se neodstraní. Data na svazku je přístupná z hostitele operačního systému a.

**Kontejnery svazků data** jsou vývoje regulární datové svazky. Kontejner svazků dat je jednoduchý kontejner, který má jeden nebo více svazků dat v něm. Kontejner svazků dat poskytuje přístup k kontejnery z centrální přípojný bod. Tato metoda přístup k datům je vhodné, protože ho abstrahuje umístění původní data. Než tu, která je podobná regulární datový svazek, své chování, takže data přetrvají v tomto kontejneru vyhrazené nezávisle na životního cyklu aplikace kontejnerů.

Jak ukazuje obrázek 4-5, regulární Docker svazky mohou být uloženy mimo kontejnery sami, ale v rámci fyzické hranic hostitelský server nebo virtuální počítač. Však nelze Docker kontejnery přístup svazku z jeden hostitelský server nebo virtuální počítač do jiného. Jinými slovy tyto svazky clusteru, není možné spravovat data sdílena mezi kontejnery, které běží na různých hostitelích Docker

![](./media/image5.png)

**Obrázek 4 – 5**. Datové svazky a externí zdroje dat pro aplikace založené na kontejneru

Kromě toho když Docker kontejnery spravuje orchestrator, kontejnery může "přesunout" mezi hostiteli, v závislosti na optimalizace provádí clusteru. Proto není doporučeno, abyste používali datové svazky pro obchodní data. Ale jsou dobrou mechanismus pro práci s trasovací soubory dočasné soubory, nebo podobný, nebude mít vliv na konzistenci dat firmy.

**Moduly plug-in svazku** jako [Flocker](https://clusterhq.com/flocker/) poskytovat přístup k datům ve všech hostitelích v clusteru. Zatímco všechny moduly plug-in svazku vytvářejí stejně, moduly plug-in svazku obvykle poskytují externalized trvalé spolehlivé úložiště z neměnné kontejnerů.

**Vzdálené zdroje dat. a mezipaměti** nástroje, například Azure SQL Database, Azure Cosmos DB nebo vzdálené mezipaměti jako mohou být používány Redis kontejnerizované aplikace stejným způsobem jako se používají při vývoji bez kontejnery. Toto je Principy sloužit k ukládání dat obchodní aplikace.

**Úložiště Azure.** Obchodní data obvykle nutné umístit do externích zdrojů nebo databáze, jako je Azure Storage. Úložiště Azure v konkrétních, poskytuje tyto služby v cloudu:

-   BLOB storage ukládá nestrukturované datové objekty. Objekt blob mohou být jakéhokoli typu textu nebo binárních dat, například dokumentu nebo médium (soubory obrázků, audio a video). Úložiště objektů blob se také označuje jako úložiště objektů.

-   File storage nabízí sdílené úložiště pro starší verze aplikace pomocí standardního protokol SMB. Cloudových služeb a virtuálních počítačích Azure můžou sdílet souborová data mezi komponentami aplikace přes sdílené složky. Místní aplikace můžou k souborovým datům ve sdílené složce prostřednictvím REST API služby File.

-   Table storage ukládá strukturované datové sady. Úložiště Table je úložiště dat klíč atribut typu NoSQL, která umožňuje rychlý vývoj a rychlý přístup k velkým objemům dat.

**Relační databáze a databáze NoSQL.** Existuje mnoho možností pro externí databáze, z relační databáze jako jsou databáze systému SQL Server, PostgreSQL, Oracle nebo NoSQL Azure Cosmos DB, MongoDB, atd. Tyto databáze nejsou chystáte vysvětlit v rámci tohoto průvodce vzhledem k tomu, že jsou v úplně jiných předmětu.


>[!div class="step-by-step"]
[Předchozí] (containerize-monolithic-applications.md) [Další] (service-oriented-architecture.md)
