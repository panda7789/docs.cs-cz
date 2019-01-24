---
title: Kompatibilita aplikací v rozhraní .NET Framework
ms.date: 05/19/2017
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1939666b3dd271959c418e3d714b177e170fcd04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595978"
---
# <a name="application-compatibility-in-the-net-framework"></a>Kompatibilita aplikací v rozhraní .NET Framework

## <a name="introduction"></a>Úvod
Kompatibilita je velmi důležité cílem každé vydané verze rozhraní .NET. Kompatibilita se zajistí, že každá verze sčítání, takže předchozí verze budou i nadále fungovat. Změny v předchozí funkci (pro zlepšení výkonu, problémů zabezpečení nebo opravovat chyby) na druhé straně může způsobit problémy s kompatibilitou v existujícím kódu nebo existující aplikace, které běží v novější verzi. Rozhraní .NET Framework rozpoznává změny cíle a změny v modulu runtime. Změny cíle ovlivňují aplikace, které cílení na konkrétní verzi rozhraní .NET Framework, ale jsou spuštěny na novější verzi. Změny v modulu runtime ovlivňují všechny aplikace spuštěné na konkrétní verzi.

Každé aplikaci, která cílí na určitou verzi rozhraní .NET Framework, která je možné zadat tak:

* Definování cílové rozhraní v sadě Visual Studio.
* Určení cílové rozhraní v souboru projektu.
* Použití <xref:System.Runtime.Versioning.TargetFrameworkAttribute> ke zdrojovému kódu.

Při spuštění na novější verzi, než jaké byla cílem rozhraní .NET Framework použije quirked chování tak, aby napodoboval starší cílených verzích. Jinými slovy aplikace bude v novější verzi rozhraní Framework, ale fungovat jako, pokud je spuštěn na starší verzi. Mnohé z problémů s kompatibilitou mezi verzemi rozhraní .NET Framework jsou zmírnit prostřednictvím této quirking modelu. Verze rozhraní .NET Framework, která je určena cílová verze sestavení položka aplikační domény, na kterém kód běží v aplikace cílena. Všechny další sestavení v určené doméně aplikace načíst tuto verzi rozhraní .NET Framework. Například v případě spustitelného souboru, rozhraní framework spustitelný cíle je režim kompatibility všechna sestavení v dané doméně aplikace bude spuštěna pod.

## <a name="runtime-changes"></a>Změny v modulu runtime

Problémy za běhu jsou ty, které vznikají při nový modul runtime je umístěn na počítači a jsou spouštěny stejné binární soubory, ale zobrazuje různé chování. Pokud byl zkompilován do binárního souboru pro rozhraní .NET Framework 4.0, poběží v rozhraní .NET Framework 4.0 režimu kompatibility na verze 4.5 nebo novější. Mnoho změn, které ovlivňují 4.5 nebude mít vliv na binární soubor pro 4.0. To je specifická pro domény aplikace a závisí na nastavení vstupní sestavení.

## <a name="retargeting-changes"></a>Změny cíle

Změna cílení problémy jsou ty, které vznikají při sestavení, které se cílí na 4.0 je nyní nastaveno na cíl 4.5. Teď do nové funkce, jakož i potenciální problémy s kompatibilitou na staré funkce požádá o sestavení. Znovu, to závisí na vstupní sestavení tak, která používá sestavení aplikace konzoly nebo web, na který odkazuje na sestavení.

## <a name="net-compatibility-diagnostics"></a>Diagnostika Kompatibilita rozhraní .NET

Diagnostika kompatibility .NET jsou s využitím Roslynu analyzátory, které pomáhají identifikovat problémy s kompatibilitou aplikace mezi verzemi rozhraní .NET Framework. Tento seznam obsahuje všechny analyzátory, které jsou k dispozici, i když pouze podmnožinu budou platit pro všechny konkrétní migrace. Analyzátory určí problémy, které se dají použít pro plánované migrace a bude pouze přinášet ty.

Všechny problémy obsahuje následující informace:

-   Popis co se změnilo z předchozí verze.

-   Změna ovlivní jak zákazníky a určuje, zda je možné zachovat kompatibilitu mezi verzemi žádné alternativní řešení.

-   Posouzení jak důležité je změnu. Potíže s kompatibilitou aplikace jsou rozdělené následujícím způsobem:

    |   |   |
    |---|---|
    |Hlavní|Významnou změnu, která ovlivňuje mnoho aplikací nebo vyžaduje podstatné změny kódu.|
    |Vedlejší|Změna, která ovlivňuje menší počet aplikací nebo která vyžaduje méně závažnou změnu kódu.|
    |Okrajový případ|Změna, která ovlivňuje aplikace v rámci velmi specifický, běžné scénáře.|
    |Transparentní|K změně znatelný vliv na uživatele nebo vývojáře aplikace.|

-   Verze označuje, jakmile změny nejprve se zobrazí v rámci. Některé změny zavedené v konkrétní verzi a vrátit v novější verzi který je označen jako dobře.

-   Typ změny:

    |   |   |
    |---|---|
    |Změna cílení|Změna ovlivní aplikace, které jsou rekompilovány cílit na novou verzi rozhraní .NET Framework.|
    |Modul runtime|Tato změna má vliv na existující aplikaci, která cílí na předchozí verzi rozhraní .NET Framework, ale funguje na novější verzi.|

-   Ovlivněné API, pokud existuje.

-   ID dostupné diagnostiky

## <a name="usage"></a>Použití
Pokud chcete začít, vyberte typ kompatibility změny níže:

* [Odlišnosti ve změnách cílení](./retargeting/index.md)
* [Změny v modulu runtime](./runtime/index.md)


## <a name="see-also"></a>Viz také:

- [Verze a závislosti](../../../docs/framework/migration-guide/versions-and-dependencies.md)
- [Co je nového](../../../docs/framework/whats-new/index.md)
- [Zastaralé položky v knihovně tříd](../../../docs/framework/whats-new/whats-obsolete.md)
