---
title: Assembly
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 1385919a1205a60104125fff1bdd24f409a091df
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351638"
---
# <a name="assembly-visual-basic"></a>Sestavení (Visual Basic)
Určuje, že atribut na začátku zdrojového souboru se vztahuje na celé sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Mnoho atributů se vztahuje k jednotlivému programovacímu prvku, jako je třída nebo vlastnost. Tento atribut použijete připojením bloku atributu v rámci lomených závorek (`< >`) přímo k příkazu Declaration.  
  
 Pokud atribut nenáleží pouze k následujícímu prvku, ale k celému sestavení, umístěte blok atributů na začátek zdrojového souboru a Identifikujte atribut pomocí klíčového slova `Assembly`. Pokud se vztahuje na aktuální modul sestavení, použijte klíčové slovo [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) .  
  
 Můžete také použít atribut pro sestavení v souboru AssemblyInfo. vb, v takovém případě není nutné použít blok atributu v hlavním souboru zdrojového kódu.  
  
## <a name="see-also"></a>Viz také:

- [Klíčové slovo \<modulu >](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [Přehled atributů](../../../visual-basic/programming-guide/concepts/attributes/index.md)
