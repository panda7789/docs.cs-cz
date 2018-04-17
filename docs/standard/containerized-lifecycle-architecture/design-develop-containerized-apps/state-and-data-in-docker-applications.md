---
title: Stav a data v aplikacích Docker
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 83094cd9a13d77f489df639096bb42b23ce152e7
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="state-and-data-in-docker-applications"></a>Stav a data v aplikacích Docker

Primitivní kontejnerů je neměnitelnosti. V porovnání se virtuální počítač, není jako běžné výskyt zmizí kontejnery. Virtuální počítač se nemusí podařit v různých formách z neaktivní procesy, přetížené procesoru nebo úplné nebo ve stavu selhání disku. Ještě Očekáváme, že virtuální počítač k dispozici a jednotky RAID jsou běžné, aby zajistil, že jednotka selhání udržovat data.

Kontejnery však jsou považované za instance procesů. Proces není zachována trvalého stavu. I když kontejner může zapsat do své místní úložiště, by ekvivalentní za předpokladu, že jedním kopírování paměti bude trvanlivý za předpokladu, že tato instance bude přibližně po neomezenou dobu. Byste měli počítat s kontejnery, stejně jako procesy, jsou duplicitní, byly ukončeny, nebo když spravovaná s nástrojem orchestrator kontejneru, může být přesunuta.

Docker používá funkci říká *překrytí systém souborů* implementovat proces kopírování při zápisu, který ukládá žádné aktualizované informace k systému souborů Kořenový kontejner, ve srovnání s původní bitové kopie, na kterých je založena. Tyto změny budou ztraceny, pokud je následně kontejneru ze systému odstraněn. Kontejner, proto nemá trvalé úložiště ve výchozím nastavení. Přestože je možné uložit stav kontejner, návrhu systému řešení bude v konfliktu se zásadou architektury kontejneru.

Ke správě dat v aplikacích Docker, jsou běžné řešení:

-   [**Datové svazky**](https://docs.docker.com/engine/tutorials/dockervolumes/) těchto připojení hostiteli, který je právě uvedené.

-   [**Kontejnery svazků data**](https://docs.docker.com/engine/tutorials/dockervolumes/#/creating-and-mounting-a-data-volume-container) tyto napříč kontejnery pomocí externí kontejneru, který můžete cyklicky přepínat vytvoření sdíleného úložiště.

-   [**Moduly plug-in svazku**](https://docs.docker.com/engine/tutorials/dockervolumes/#/mount-a-shared-storage-volume-as-a-data-volume) tyto svazky do vzdáleného umístění, poskytuje dlouhodobé trvalost připojte.

-   **Vzdálené zdroje dat.** mezi příklady patří databáze SQL a ne-SQL nebo služby, jako je Redis do mezipaměti.

-   [**Úložiště Azure**](https://docs.microsoft.com/azure/storage/) to poskytuje geograficky distribuovatelného platforma jako služba (PaaS) úložiště, poskytuje nejlepší kontejnery jako dlouhodobé trvalost.

Datové svazky jsou speciálně určené adresáře v rámci jednoho nebo více kontejnerů, které obcházejí [Union systém souborů](https://docs.docker.com/v1.8/reference/glossary#union-file-system). Datové svazky jsou navrženy pro zachování dat, nezávisle na kontejneru životního cyklu. Docker proto nikdy automaticky odstraní svazky při odebrat kontejner, ani se ji "paměti shromažďovat" svazky, které jsou již odkazuje kontejner. Hostitelský operační systém můžete procházet a upravit data v jakýkoli svazek, volně, který je právě dalším důvodem pro datové svazky používejte opatrně.

A [kontejneru svazků data](https://docs.docker.com/v1.8/userguide/dockervolumes/) představuje vylepšení regulární datové svazky. Je v podstatě spících kontejner, který má jeden nebo více svazků dat vytvořit v něm (jak je popsáno výše). Kontejner svazků dat poskytuje přístup k kontejnery z centrální přípojný bod. Výhodou této metody přístupu je, že ji abstrahuje umístění původního, data pro kontejner dat logické přípojný bod. Také umožňuje přístup k datové svazky kontejneru vytvořen a zničen při zachování dat trvalé v vyhrazené kontejneru kontejnery "aplikace".

Obrázek 4 – 5 ukazuje, že regulární Docker svazky mohou být umístěny na úložiště mimo kontejnery sami, ale v rámci hranic fyzické nebo virtuální počítač server hostitele. *Svazky docker nemáte možnost používat jeden hostitelský server nebo virtuální počítač svazek*.

![](./media/image5.png)

Obrázek 4 – 5: datové svazky a externí zdroje dat pro kontejnery aplikací nebo kontejnery

Z důvodu nemohou spravovat data sdílena mezi kontejnery, které běží na samostatné fyzické hostitele, je doporučeno používat svazky pro obchodní data není-li hostitelů Docker pevné hostitele nebo virtuálního počítače, protože při použití Docker kontejnerů v nástroji orchestrator, Očekává se, že kontejnery přesunout z jednoho do jiného hostitele, v závislosti na optimalizace provést clusteru.

Regulární datové svazky jsou tedy funkční mechanismus pro práci s trasovací soubory, dočasné soubory nebo všechny podobné konceptu, které neovlivní konzistenci dat firmy, nebo když kontejnerů přesunou ve více hostitelích.

Moduly plug-in svazek jako [Flocker](https://clusterhq.com/flocker/) poskytují data ve všech hostitelích v clusteru. I když ne všechny svazku moduly plug-in jsou vytvořené stejně, moduly plug-in svazku obvykle poskytují externalized trvalé spolehlivé úložiště z neměnné kontejnerů.

Vzdálené zdroje dat. a mezipaměti jako databáze SQL, DocumentDB nebo vzdálené mezipaměti jako Redis by být stejný jako vývoj bez kontejnery. Toto je jedním ze způsobů upřednostňovaných a principy, k ukládání dat obchodní aplikace.


>[!div class="step-by-step"]
[Předchozí] (monolitický applications.md) [Další] (soa-applications.md)
