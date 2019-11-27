---
title: Typografická pravidla a pravidla vytváření kódu
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
ms.openlocfilehash: 4906c5ebadb7ce77f2d0e53b2fc5dbab69c5b41f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352703"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Typografická pravidla a pravidla vytváření kódu (Visual Basic)

Dokumentace Visual Basic používá následující typografické a kódové konvence.  
  
## <a name="typographic-conventions"></a>Typografické konvence  
  
|Příklad|Popis|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True``Debug`|Klíčová slova specifická pro jazyk a členy modulu runtime mají počáteční velká písmena a jsou formátovány, jak je znázorněno v tomto příkladu.|  
|**SmallProject**, **tlačítkocollection**|Slova a fráze, které jste zadali jako text, jsou formátovány, jak je uvedeno v tomto příkladu.|  
|[Příkaz Module](../../visual-basic/language-reference/statements/module-statement.md)|Odkazy, které můžete kliknutím přejít na jinou stránku, jsou formátovány, jak je uvedeno v tomto příkladu.|  
|*objekt*, *Proměnná*, `argumentList`|Zástupné symboly pro informace, které zadáte, jsou formátovány, jak je znázorněno v tomto příkladu.|  
|[Stíny], [ *expressionlist* ]|V syntaxi jsou volitelné položky uzavřeny v závorkách.|  
|{`Public` &#124; `Friend` &#124; `Private`}|V syntaxi, pokud je třeba provést volbu mezi dvěma nebo více položkami, jsou položky uzavřeny ve složených závorkách a odděleny svislými panely.<br /><br /> Musíte vybrat jednu a jenom jednu z položek.|  
|[`Protected` &#124; `Friend`]|Pokud máte v syntaxi možnost výběru dvou nebo více položek, položky jsou uzavřeny do hranatých závorek a odděleny svislými panely.<br /><br /> Můžete vybrat libovolnou kombinaci položek nebo žádnou položku.|  
|[{`ByVal` &#124; `ByRef`}]|Pokud v syntaxi můžete vybrat maximálně jednu položku, ale můžete také položky vynechat, položky jsou uzavřeny do hranatých závorek, které jsou obklopeny závorkami a odděleny svislými panely.|  
|*Member*-1, *Member*2, *Member*3|Více instancí stejné zástupné symboly jsou odlišeny pomocí dolních indexů, jak je znázorněno v příkladu.|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|V syntaxi se tři tečky (...) používají k označení nekonečného počtu položek typu bezprostředně před třemi tečkami.<br /><br /> V kódu označují tři tečky kód vynechaný v zájmu srozumitelnosti.|  
|ESC ZADEJTE|Názvy klíčů a posloupnosti kláves na klávesnici se zobrazují velkými písmeny.|  
|ALT+F1|Pokud se mezi názvy kláves objeví znaménko plus (+), je nutné při stisknutí klávesy One stisknout klávesu One. Například ALT + F1 znamená při stisknutí klávesy F1 stisknutou klávesu ALT.|  
  
## <a name="code-conventions"></a>Konvence kódu  
  
|Příklad|Popis|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Ukázky kódu se zobrazí ve formátu s pevnou roztečí a jsou formátovány, jak je znázorněno v tomto příkladu.|  
|Předchozí příkaz nastaví hodnotu `sampleString` "Hello, World!"|Prvky kódu v vysvětlujícím textu se zobrazí v neproporcionálním písmu, jak je znázorněno v tomto příkladu.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Komentáře kódu jsou představeny apostrofem (') nebo klíčovým slovem REM.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Mezera následovaná podtržítkem (_) na konci řádku označuje, že příkaz pokračuje na následujícím řádku.|  
  
## <a name="see-also"></a>Viz také:

- [Referenční příručka jazyka Visual Basic](../../visual-basic/language-reference/index.md)
- [Klíčová slova](../../visual-basic/language-reference/keywords/index.md)
- [Členové knihovny modulu runtime jazyka Visual Basic](../../visual-basic/language-reference/runtime-library-members.md)
- [Visual Basic konvence pojmenování](../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Postupy: Přerušení a kombinace příkazů v kódu](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Komentáře v kódu](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
