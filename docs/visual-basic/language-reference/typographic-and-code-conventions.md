---
title: Typografická pravidla a pravidla vytváření kódu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
ms.openlocfilehash: 3255dff8268cd5500a1244716f37bf30f5b43cfb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698600"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Typografická pravidla a pravidla vytváření kódu (Visual Basic)
Dokumentace jazyka Visual Basic používá následující typografickém a pravidla týkající se kódu.  
  
## <a name="typographic-conventions"></a>Typografické konvence  
  
|Příklad|Popis|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Klíčová slova specifická pro jazyk a modulu runtime členy mají počáteční velká písmena a jsou ve formátu, jak je znázorněno v tomto příkladu.|  
|**SmallProject**, **ButtonCollection**|Jak je znázorněno v tomto příkladu jsou formátovány slova a slovní spojení, které nebudete vyzváni k zadání.|  
|[Příkaz Module](../../visual-basic/language-reference/statements/module-statement.md)|Jak je znázorněno v tomto příkladu jsou formátovány odkazů, které můžete kliknout a přejít na jinou stránku nápovědy.|  
|*objekt*, *NázevProměnné*, `argumentList`|Jak je znázorněno v tomto příkladu jsou formátovány zástupné symboly pro informace, které zadáte.|  
|[Stíny], [ *expressionList* ]|V syntaxi volitelné položky jsou uzavřeny v závorkách.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|V syntaxi když musíte rozhodnout mezi dvěma nebo více položek, položky jsou uzavřeny ve složených závorkách a oddělené svislé čáry.<br /><br /> Musíte vybrat jeden a pouze jeden položky.|  
|[ `Protected` &#124; `Friend` ]|V syntaxi až budete mít možnost výběru mezi dva nebo více položek, jsou položky v hranatých závorkách a odděleny svislé čáry.<br /><br /> Můžete vybrat libovolnou kombinaci položky nebo žádná položka.|  
|[{ `ByVal` &#124; `ByRef` }]|V syntaxi když vyberete více než jednu položku, ale také můžete vynechat položky úplně, jsou položky uzavřeny do hranatých závorek uzavřeny ve složených závorkách a odděleny svislé čáry.|  
|*memberName*1, *memberName*2, *memberName*3|Více instancí stejné zástupného symbolu jsou rozlišené pomocí dolních indexů, jak je znázorněno v příkladu.|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|V syntaxi třemi tečkami (...) se používá k označení nekonečný počet položek typu bezprostředně před na tři tečky.<br /><br /> V kódu symbol tří teček místo kódu vynechána přehlednosti.|  
|ESC, ENTER|Názvy klíčů a kláves na klávesnici zobrazí všechna velká písmena.|  
|ALT+F1|Jakmile se zobrazí znaménko plus (+) mezi názvy klíčů, musí při stisknutí klávesy druhé podržte stisknutou jeden klíč. ALT + F1 například znamená, podržte stisknutou klávesu ALT při stisknutí klávesy F1.|  
  
## <a name="code-conventions"></a>Pravidla týkající se kódu  
  
|Příklad|Popis|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Ukázky kódu se zobrazí v neproporcionální písmo a jsou ve formátu, jak je znázorněno v tomto příkladu.|  
|Předchozí příkaz nastaví hodnotu `sampleString` na "Hello, world!"|Prvky kódu v vysvětlující text se zobrazí v neproporcionální písmo, jak je znázorněno v tomto příkladu.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Komentáře kódu vznikají zavlečením apostrof (') nebo REM – klíčové slovo.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Mezerou následovanou podtržítka (_) na konci řádku označuje, zda příkaz bude pokračovat na následující řádek.|  
  
## <a name="see-also"></a>Viz také:

- [Referenční příručka jazyka Visual Basic](../../visual-basic/language-reference/index.md)
- [Klíčová slova](../../visual-basic/language-reference/keywords/index.md)
- [Členové knihovny modulu runtime jazyka Visual Basic](../../visual-basic/language-reference/runtime-library-members.md)
- [Zásady vytváření názvů jazyka Visual Basic](../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Postupy: Přerušení a kombinování příkazů v kódu](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Komentáře v kódu](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
