---
title: Sestavení
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
ms.openlocfilehash: 7d313dee1015362bd0215ed98ab7e898312cfbcd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373157"
---
# <a name="assembly-visual-basic"></a>Sestavení (Visual Basic)
Určuje, že atribut na začátku zdrojového souboru se vztahuje na celé sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Mnoho atributů se vztahuje k jednotlivému programovacímu prvku, jako je třída nebo vlastnost. Tento atribut lze uplatnit připojením bloku atributu v rámci lomených závorek ( `< >` ) přímo k příkazu Declaration.  
  
 Pokud atribut nenáleží pouze k následujícímu prvku, ale k celému sestavení, umístěte blok atributů na začátek zdrojového souboru a Identifikujte atribut pomocí `Assembly` klíčového slova. Pokud se vztahuje na aktuální modul sestavení, použijte klíčové slovo [Module](module-keyword.md) .  
  
 Můžete také použít atribut pro sestavení v souboru AssemblyInfo. vb, v takovém případě není nutné použít blok atributu v hlavním souboru zdrojového kódu.  
  
## <a name="see-also"></a>Viz také

- [Čipu\<keyword>](module-keyword.md)
- [Přehled atributů](../../programming-guide/concepts/attributes/index.md)
