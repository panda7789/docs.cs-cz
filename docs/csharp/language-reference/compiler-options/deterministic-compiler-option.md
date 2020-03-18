---
title: -deterministický (Možnosti kompilátoru Jazyka C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: ed5d1db4618649391f88affad67e62dd9fc95925
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73455183"
---
# <a name="-deterministic"></a>-deterministic

Způsobí, že kompilátor k vytvoření sestavení, jehož bajt za bajt výstup je shodný napříč kompilace pro identické vstupy.

## <a name="syntax"></a>Syntaxe

```console
-deterministic
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je výstup kompilátoru z dané sady vstupů jedinečný, protože kompilátor přidá časové razítko a identifikátor GUID generovaný z náhodných čísel. Tuto `-deterministic` možnost použijete k vytvoření *deterministického sestavení*, jehož binární obsah je napříč kompilacemi shodný, pokud vstup zůstane stejný.

Kompilátor považuje následující vstupy pro účely determinismu:

- Posloupnost parametrů příkazového řádku.
- Obsah souboru odpovědi RSP kompilátoru.
- Přesná verze použitého kompilátoru a jeho odkazovaná sestavení.
- Aktuální cesta k adresáři.
- Binární obsah všech souborů explicitně předán kompilátoru přímo nebo nepřímo, včetně:
  - Zdrojové soubory
  - Odkazovaná sestavení
  - Odkazované moduly
  - Zdroje informací
  - Soubor klíče silného názvu
  - @ odpovědi soubory
  - Analyzátory
  - Rulesets
  - Další soubory, které mohou být použity analyzátory
- Aktuální jazyková verze (pro jazyk, ve kterém jsou vytvářeny zprávy diagnostiky a výjimky).
- Výchozí kódování (nebo aktuální znaková stránka), pokud kódování není zadáno.
- Existence, neexistence a obsah souborů v cestách hledání kompilátoru (zadáno `-lib` například podle nebo `-recurse`).
- Clr platformu, na kterém je spuštěn kompilátor.
- Hodnota `%LIBPATH%`, která může ovlivnit načítání závislostí analyzátoru.

Pokud jsou zdroje veřejně dostupné, deterministické kompilace lze použít pro určení, zda binární je kompilován z důvěryhodného zdroje. Může být také užitečné v systému průběžnésestavení pro určení, zda kroky sestavení, které jsou závislé na změny binární musí být provedeny.

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
