---
title: -deterministické (C# možnosti kompilátoru)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e77c14a1c3a4ba11b8ae6556be4f1c3c0cd42788
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202917"
---
# <a name="-deterministic"></a>-deterministic

Způsobí, že kompilátor sestaví sestavení, jejichž výstup Byte-byte je stejný v rámci kompilací pro stejné vstupy.

## <a name="syntax"></a>Syntaxe

```console
-deterministic
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je výstup kompilátoru z dané sady vstupů jedinečný, protože kompilátor přidá časové razítko a identifikátor GUID, který je vygenerován z náhodných čísel. Použijete `-deterministic` možnost k vytvoření deterministického *sestavení*, jehož binární obsah je identický v rámci kompilací, pokud vstup zůstává stejný.

Kompilátor považuje za účel determinismem následující vstupy:

- Sekvence parametrů příkazového řádku.
- Obsah souboru odpovědí kompilátoru. rsp
- Byla použita přesná verze kompilátoru a jejich odkazovaná sestavení.
- Cesta k aktuálnímu adresáři.
- Binární obsah všech souborů explicitně předaných kompilátoru buď přímo, nebo nepřímo, včetně:
  - Zdrojové soubory
  - Odkazovaná sestavení
  - Odkazované moduly
  - Prostředky
  - Soubor klíče se silným názvem
  - soubory @ Response
  - Analyzátory
  - Rulesets
  - Další soubory, které mohou používat analyzátory
- Aktuální jazyková verze (pro jazyk, ve kterém se vytvářejí zprávy o diagnostice a výjimkách).
- Výchozí kódování (nebo aktuální znaková stránka), pokud kódování není zadáno.
- Existence, neexistence a obsah souborů v cestách pro hledání kompilátoru (určené například pomocí `/lib` nebo `/recurse`).
- Platforma CLR, na které je kompilátor spuštěn.
- Hodnota `%LIBPATH%`, která může ovlivnit načítání závislostí analyzátoru.

Pokud jsou zdroje veřejně dostupné, lze použít deterministické kompilace k určení, zda binární soubor je zkompilován z důvěryhodného zdroje. Může být také užitečné v souvislém systému sestavení pro určení, zda jsou kroky sestavení závislé na změnách binárních souborů nutné provést.

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
