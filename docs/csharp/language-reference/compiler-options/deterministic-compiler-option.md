---
title: -deterministické (možnosti kompilátoru C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f9aca20a3ff65d061c04a21e31db3fb5eab62ba
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584062"
---
# <a name="-deterministic"></a>-deterministické

Způsobí, že kompilátor vytvoří sestavení, jehož výstup bajt po bajtu je identické napříč kompilace identické vstupů. 

## <a name="syntax"></a>Syntaxe

```
-deterministic
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je výstup kompilátoru z danou sadu vstupů jedinečná, vzhledem k tomu, že kompilátor přidává časové razítko a identifikátor GUID, který je generován z náhodných čísel. Můžete použít `-deterministic` možnost vytvářet *deterministické sestavení*, jehož binární obsah identické napříč kompilace jako vstup zůstává stejná.

Kompilátor bere v úvahu následující vstupy pro účely determinismus:

- Pořadí parametrů příkazového řádku.
- Obsah souboru odezvy kompilátoru .rsp.
- Přesné verze kompilátoru použít a jeho odkazované sestavení.
- Aktuální cesta k adresáři.
- Binární obsah všech souborů explicitně předány kompilátoru přímo nebo nepřímo, včetně:
    - Zdrojové soubory
    - Odkazovaná sestavení
    - Odkazované moduly
    - Prostředky
    - Soubor klíče se silným názvem
    - @ soubory odpovědí
    - Analyzátory
    - Sady pravidel
    - Další soubory, které mohou být využívána analyzátory
- Aktuální jazykové verze (pro jazyk, v které diagnostiky a výjimky se budou vytvářet zprávy).
- Výchozí kódování (nebo aktuální znakové stránce) Pokud kódování není zadán.
- Existence, neexistence a obsah souborů na vyhledávací cesty kompilátoru (například tím, že zadaný `/lib` nebo `/recurse`).
- Platforma CLR, na kterém je spuštěna kompilátor.
- Hodnota `%LIBPATH%`, což může ovlivnit načítání analyzátoru závislostí.

Když jsou veřejně dostupné zdroje, deterministickou kompilaci lze použít pro stanovení, zda je zkompilován do binárního souboru z důvěryhodného zdroje. Může být také užitečné v systému průběžného sestavení pro určení, jestli je potřeba spustit kroky sestavení, které jsou závislé na změny do binárního souboru. 

## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
