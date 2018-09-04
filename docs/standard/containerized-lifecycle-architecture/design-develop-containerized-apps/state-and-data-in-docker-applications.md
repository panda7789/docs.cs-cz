---
title: Stav a data v aplikacích Dockeru
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 78db191bdec4c25c11728d819d89eaaaff4bd7da
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564609"
---
# <a name="state-and-data-in-docker-applications"></a>Stav a data v aplikacích Dockeru

Primitivní kontejnerů je neměnnosti. Při porovnání k virtuálnímu počítači, není jako společného výskytu zmizí kontejnery. Virtuální počítač se nemusí podařit v různých formách z dead procesy, přetížené procesoru nebo úplné nebo selhání disku. Zatím Očekáváme, že virtuální počítač k dispozici a běžné, aby zajistil, že data udržovat selhání jednotky jsou jednotky RAID.

Ale kontejnerů jsou považované za instance procesů. Proces nemá udržovat trvalého stavu. I v případě, že kontejner může zapisovat do své místní úložiště, by ekvivalentní za předpokladu, že bude trvalé paměti jedné kopie za předpokladu, že tato instance bude kolem po neomezenou dobu. Byste měli předpokládat, že jsou kontejnery, jako jsou procesy, duplicitní, ukončeny, nebo když spravovaný pomocí orchestrátoru kontejneru, mohou být přesunuty.

Docker používá funkci označovanou jako *překryv systému souborů* k implementaci procesu na kopírování zápisů, která ukládá všechny aktualizované informace o kořenové systému souborů kontejneru ve srovnání s původní bitové kopie, na které je založená. Tyto změny budou ztraceny, pokud kontejner se pak odstraní ze systému. Kontejner, proto nemá trvalého úložiště ve výchozím nastavení. I když je možné uložit stav kontejneru, návrhu systému tomuto by konfliktu se zásadou architektury kontejneru.

Správa trvalých dat v aplikacích Dockeru, jsou běžná řešení:

-   [**Datové svazky**](https://docs.docker.com/engine/tutorials/dockervolumes/) těchto připojení k hostiteli, jak je právě uvedeno.

-   [**Kontejnery svazků data**](https://docs.docker.com/engine/tutorials/dockervolumes/#/creating-and-mounting-a-data-volume-container) poskytnout tyto sdílené úložiště napříč kontejnery pomocí externí kontejneru, který můžou cyklicky.

-   [**Moduly plug-in svazku**](https://docs.docker.com/engine/tutorials/dockervolumes/#/mount-a-shared-storage-volume-as-a-data-volume) tyto připojit svazky do vzdáleného umístění, poskytování dlouhodobé trvalosti.

-   **Vzdálené zdroje dat.** příklady zahrnují databáze SQL a ne SQL nebo službám, jako je Redis do mezipaměti.

-   [**Azure Storage**](https://docs.microsoft.com/azure/storage/) to poskytuje platformu Distribuovatelný geograficky jako služba (PaaS) úložiště, poskytuje tak to nejlepší z kontejnerů jako dlouhodobé trvalosti.

Datové svazky jsou speciálně určené adresáře v rámci jednoho nebo více kontejnerů, které obcházejí [sjednocení systému souborů](https://docs.docker.com/glossary/?term=Union%20file%20system). Datové svazky jsou navržené tak, zachovat data, nezávisle na kontejneru životního cyklu. Docker proto nikdy automaticky odstraní svazky při odstranit kontejner, ani bude "uvolňování paměti shromažďovat" svazky, které jsou již neodkazuje kontejneru. Hostitelský operační systém můžete procházet a upravovat data v žádné svazky volně, což je další důvod, proč použít datové svazky opatrně.

A [datový kontejner svazků](https://docs.docker.com/glossary/?term=volume) je vylepšením oproti regulární datové svazky. Je v podstatě neaktivní kontejner, který má jeden nebo více datových svazků vytvořených v rámci jeho (jak je popsáno dříve). Kontejner svazků dat z centrální přípojný bod poskytuje přístup k kontejnery. Výhodou této metody přístupu je, že abstrahuje umístění původní data provádění datový kontejner logické přípojného bodu. Umožňuje také přístup k datové svazky kontejneru na vytvořeno a zničeno při zachování dat trvalé v kontejneru vyhrazené kontejnery "aplikace".

Obrázek 4 až 5 ukazuje regulárních svazky Dockeru, můžete umístit na úložiště mimo kontejnery sami, ale v rámci hranic fyzický server nebo virtuální počítač hostitele. *Docker svazky nemají možnost používat jeden hostitelský server/VM svazku*.

![](./media/image5.png)

Obrázek 4 – 5: datové svazky a externích zdrojů dat pro kontejnery aplikací/kontejnery

Lokalizovat ke správě dat sdílet mezi kontejnery, které běží na samostatných fyzických hostitelů, doporučujeme je velmi riskantní používat svazky pro obchodní data není-li hostitele Docker pevnou hostitelů/virtuálních počítačů, protože při použití kontejneru Dockeru do orchestrator Očekává se, že kontejnery přesunout z jednoho do jiného hostitele, v závislosti na optimalizace, které se provádí clusteru.

Proto pravidelně datové svazky jsou mechanismus dobrý postup při trasovací soubory, dočasné soubory nebo žádné podobné informace, které nebudou by ovlivnily konzistenci dat obchodní Pokud nebo při přesunutí kontejnerů napříč více hostiteli.

[Moduly plug-in svazku](https://docs.docker.com/engine/extend/plugins_volume/) poskytují data na všech hostitelích v clusteru. I když ne všechny moduly plug-in svazku se vytvoří stejnou měrou, moduly plug-in svazku obvykle poskytují externalized trvalé spolehlivé úložiště z neměnné kontejnerů.

Vzdálené zdroje dat. a mezipamětí, jako je SQL Database, DocumentDB nebo vzdálené mezipaměti, jako jsou Redis by být stejný jako vývoj bez kontejnery. Toto je jedním ze způsobů upřednostňovaný a prověřených, k ukládání dat obchodní aplikace.


>[!div class="step-by-step"]
[Předchozí](monolithic-applications.md)
[další](soa-applications.md)
