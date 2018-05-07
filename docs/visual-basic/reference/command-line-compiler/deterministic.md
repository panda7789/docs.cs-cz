---
title: -deterministickou
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffb1d27f614afc3b07f9d663831fc2071535236f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-deterministic"></a>-deterministickou

Způsobí, že kompilátoru vytvoření sestavení jejichž bajtů pro bajtový výstup je stejný jako napříč kompilace pro identické vstupy. 

## <a name="syntax"></a>Syntaxe

```
-deterministic
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je výstup kompilátoru danou sadu vstupy jedinečné, vzhledem k tomu, že kompilátor přidá časovým razítkem a identifikátor GUID, který se generují z náhodných čísel. Použijete `-deterministic` možnost k vytvoření *deterministickou sestavení*, jeden jejichž binární obsah je stejný jako napříč kompilace vstup zůstává stejné.

Kompilátor zvažuje následující vstupy pro účely determinism:

- Pořadí parametrů příkazového řádku.
- Obsah souboru kompilátoru .rsp odezvy.
- Přesné verze kompilátoru použít a jeho odkazované sestavení.
- Cesty k aktuálnímu adresáři.
- Binární obsah všech souborů explicitně předaný kompilátor přímo ani nepřímo, včetně: 
    - Zdrojové soubory
    - Odkazovaná sestavení
    - Odkazovaná moduly
    - Prostředky
    - Soubor klíče silným názvem
    - @ soubory odezvy
    - Analyzátory
    - Sady pravidel
    - Další soubory, které může být používán analyzátory
- Aktuální jazykové verze (pro jazyk, ve které diagnostiky a výjimky zprávy vytváří).
- Výchozí kódování (nebo aktuální znakovou stránku) Pokud není zadán kódování.
- Existence, neexistence a obsah souborů na cesty hledání kompilátoru (zadaný, například `/lib` nebo `/recurse`).
- Platforma CLR, na kterém je spuštěna kompilátoru.
- Hodnota `%LIBPATH%`, což může ovlivnit načítání závislostí analyzátor.

Pokud jsou veřejně dostupné zdroje, deterministickou kompilace lze použít pro stanovení, zda se binární kompiluje z důvěryhodného zdroje. Také může být užitečné v systému průběžné sestavení pro určení, jestli není potřeba provést kroky sestavení, které jsou závislé na změny binární. 

## <a name="see-also"></a>Viz také
[Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
[Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
