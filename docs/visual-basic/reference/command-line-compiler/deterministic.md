---
title: -deterministic
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
ms.openlocfilehash: 95c9add0521208ef04ff47c071a2e04abc968f27
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480635"
---
# <a name="-deterministic"></a>-deterministic

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

## <a name="see-also"></a>Viz také:

- [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
