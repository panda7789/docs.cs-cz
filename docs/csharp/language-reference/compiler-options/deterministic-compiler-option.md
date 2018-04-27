---
title: -deterministickou (možnosti kompilátoru C#)
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6dd597f726b5bbc40feb4cc6f5b03acabd92f4a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
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
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
