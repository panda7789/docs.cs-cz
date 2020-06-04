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
ms.openlocfilehash: 0e36d9d61b0dd2701210ce614d15fd38f08f5401
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401352"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Typografická pravidla a pravidla vytváření kódu (Visual Basic)

Dokumentace Visual Basic používá následující typografické a kódové konvence.  
  
## <a name="typographic-conventions"></a>Typografické konvence  
  
|Příklad|Description|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Klíčová slova specifická pro jazyk a členy modulu runtime mají počáteční velká písmena a jsou formátovány, jak je znázorněno v tomto příkladu.|  
|**SmallProject**, **tlačítkocollection**|Slova a fráze, které jste zadali jako text, jsou formátovány, jak je uvedeno v tomto příkladu.|  
|[Module – příkaz](statements/module-statement.md)|Odkazy, které můžete kliknutím přejít na jinou stránku, jsou formátovány, jak je uvedeno v tomto příkladu.|  
|*objekt*, *Proměnná*,`argumentList`|Zástupné symboly pro informace, které zadáte, jsou formátovány, jak je znázorněno v tomto příkladu.|  
|[Stíny], [ *expressionlist* ]|V syntaxi jsou volitelné položky uzavřeny v závorkách.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|V syntaxi, pokud je třeba provést volbu mezi dvěma nebo více položkami, jsou položky uzavřeny ve složených závorkách a odděleny svislými panely.<br /><br /> Musíte vybrat jednu a jenom jednu z položek.|  
|[ `Protected` &#124; `Friend` ]|Pokud máte v syntaxi možnost výběru dvou nebo více položek, položky jsou uzavřeny do hranatých závorek a odděleny svislými panely.<br /><br /> Můžete vybrat libovolnou kombinaci položek nebo žádnou položku.|  
|[{ `ByVal` &#124; `ByRef` }]|Pokud v syntaxi můžete vybrat maximálně jednu položku, ale můžete také položky vynechat, položky jsou uzavřeny do hranatých závorek, které jsou obklopeny závorkami a odděleny svislými panely.|  
|*Member*-1, *Member*2, *Member*3|Více instancí stejné zástupné symboly jsou odlišeny pomocí dolních indexů, jak je znázorněno v příkladu.|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|V syntaxi se tři tečky (...) používají k označení nekonečného počtu položek typu bezprostředně před třemi tečkami.<br /><br /> V kódu označují tři tečky kód vynechaný v zájmu srozumitelnosti.|  
|ESC ZADEJTE|Názvy klíčů a posloupnosti kláves na klávesnici se zobrazují velkými písmeny.|  
|ALT + F1|Pokud se mezi názvy kláves objeví znaménko plus (+), je nutné při stisknutí klávesy One stisknout klávesu One. Například ALT + F1 znamená při stisknutí klávesy F1 stisknutou klávesu ALT.|  
  
## <a name="code-conventions"></a>Konvence kódu  
  
|Příklad|Description|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Ukázky kódu se zobrazí ve formátu s pevnou roztečí a jsou formátovány, jak je znázorněno v tomto příkladu.|  
|Předchozí příkaz nastaví hodnotu `sampleString` na Hello, World!.|Prvky kódu v vysvětlujícím textu se zobrazí v neproporcionálním písmu, jak je znázorněno v tomto příkladu.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Komentáře kódu jsou představeny apostrofem (') nebo klíčovým slovem REM.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Mezera následovaná podtržítkem (_) na konci řádku označuje, že příkaz pokračuje na následujícím řádku.|  
  
## <a name="see-also"></a>Viz také

- [Reference jazyka Visual Basic](index.md)
- [Klíčová slova](keywords/index.md)
- [Členové knihovny prostředí Runtime jazyka Visual Basic](runtime-library-members.md)
- [Zásady vytváření názvů jazyka Visual Basic](../programming-guide/program-structure/naming-conventions.md)
- [Postupy: Přerušení a kombinování příkazů v kódu](../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Komentáře v kódu](../programming-guide/program-structure/comments-in-code.md)
