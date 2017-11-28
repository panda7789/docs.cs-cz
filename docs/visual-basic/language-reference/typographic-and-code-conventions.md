---
title: "Typografická pravidla a pravidla vytváření kódu (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7b6db5c223b0548e308b49a686cff72eaaf8da36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Typografická pravidla a pravidla vytváření kódu (Visual Basic)
Dokumentace jazyka Visual Basic používá následující typografická pravidla a pravidla týkající se kódu.  
  
## <a name="typographic-conventions"></a>Typografické konvence  
  
|Příklad|Popis|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Klíčová slova specifická pro jazyk a runtime členů mají počáteční velká písmena a zda jsou formátovány jak je znázorněno v tomto příkladu.|  
|**SmallProject**, **ButtonCollection**|Jak je znázorněno v tomto příkladu jsou formátovaná slova a slovní spojení, nebudete vyzváni k zadání.|  
|[Module – příkaz](../../visual-basic/language-reference/statements/module-statement.md)|Odkazy, které lze klepnout a přejít na jinou stránku nápovědy jsou formátovaná, jak je znázorněno v tomto příkladu.|  
|*objekt*, *NázevProměnné*,`argumentList`|Zástupné symboly pro informace, které zadáte jsou formátovaná, jak je znázorněno v tomto příkladu.|  
|[Stínů], [ *expressionList* ]|V syntaxi jsou volitelné položky uzavřený v závorkách.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|V syntaxi když je nutné vybrat mezi dva nebo více položek, jsou uzavřené do složených závorek a položky oddělených svislých pruhů.<br /><br /> Je nutné vybrat jeden a pouze jeden položky.|  
|[ `Protected` &#124; `Friend` ]|V syntaxi když máte možnost výběru mezi dva nebo více položek, jsou uzavřeny do hranatých závorek a položky oddělených svislých pruhů.<br /><br /> Můžete vybrat libovolnou kombinaci položky nebo žádná položka.|  
|[{ `ByVal` &#124; `ByRef` }]|V syntaxi když vyberete více než jednu položku, ale položky můžete vypustit úplně, jsou položky uzavřeny do hranatých závorek obklopená složené závorky a oddělených svislých pruhů.|  
|*memberName*1, *memberName*2, *memberName*3|Více instancí stejné zástupný symbol jsou rozlišené pomocí dolní indexy, jak je znázorněno v příkladu.|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|V syntaxi, třemi tečkami (...) slouží k označení nekonečný počet položek typu bezprostředně před se třemi tečkami.<br /><br /> V kódu symbol tří teček označily kód vynechání v zájmu přehlednosti.|  
|ESC, ZADEJTE|Názvy klíčů a posloupnosti kláves na klávesnici zobrazí velkými písmeny.|  
|ALT + F1|Jakmile se zobrazí znak plus (+) mezi názvy klíčů, můžete při dalších stisknutím stisknutou jeden klíč. ALT + F1 například znamená, podržte klávesu ALT a stisknutím klávesy F1.|  
  
## <a name="code-conventions"></a>Pravidla týkající se kódu  
  
|Příklad|Popis|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Ukázky kódu se zobrazí v neproporcionální písmo a zda jsou formátovány jak je znázorněno v tomto příkladu.|  
|Předchozí příkaz nastaví hodnotu `sampleString` na "Hello, world!"|Elementy kódu v vysvětlující text se zobrazí v neproporcionální písmo, jak je uvedeno v tomto příkladu.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Komentáře kódu jsou zavedené službou apostrof (') nebo klíčové slovo REM.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Mezeru a podtržítko (_) na konci řádku označuje, zda příkaz bude pokračovat na následující řádek.|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka Visual Basic](../../visual-basic/language-reference/index.md)  
 [Klíčová slova](../../visual-basic/language-reference/keywords/index.md)  
 [Členové knihovny prostředí Runtime jazyka Visual Basic](../../visual-basic/language-reference/runtime-library-members.md)  
 [Zásady vytváření názvů jazyka Visual Basic](../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Postupy: přerušení a kombinace příkazů v kódu](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [Komentáře v kódu](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
