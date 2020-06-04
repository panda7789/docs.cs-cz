---
title: Čipu<keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: 0cb009c22dada7b92956e113d33505923a92f2b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362421"
---
# <a name="module-keyword-visual-basic"></a>\<keyword> – modul (Visual Basic)
Určuje, že atribut na začátku zdrojového souboru se vztahuje na aktuální modul sestavení.  
  
## <a name="remarks"></a>Poznámky  
 Mnoho atributů se vztahuje k jednotlivému programovacímu prvku, jako je třída nebo vlastnost. Tento atribut lze uplatnit připojením bloku atributu v rámci lomených závorek ( `< >` ) přímo k příkazu Declaration.  
  
 Pokud atribut nenáleží pouze k následujícímu elementu, ale k aktuálnímu modulu sestavení, umístěte blok atributu na začátek zdrojového souboru a Identifikujte atribut pomocí `Module` klíčového slova. Pokud platí pro celé sestavení, použijte klíčové slovo [Assembly](assembly.md) .  
  
 `Module`Modifikátor není stejný jako [příkaz Module](../statements/module-statement.md).  
  
## <a name="see-also"></a>Viz také

- [Sestavení](assembly.md)
- [Module – příkaz](../statements/module-statement.md)
- [Přehled atributů](../../programming-guide/concepts/attributes/index.md)
