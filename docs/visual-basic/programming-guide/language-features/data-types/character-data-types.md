---
title: Datové typy znaků (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: afd368c00444f136c6d69b02a733c82f0c8eafe0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="character-data-types-visual-basic"></a>Datové typy znaků (Visual Basic)
Visual Basic poskytuje *znak datové typy* jak nakládat s tiskových a zobrazitelné znaků. Při obě řešit znaky znakové sady Unicode, `Char` obsahují jeden znak, zatímco `String` obsahuje nekonečný počet znaků.  
  
 Tabulka, která zobrazuje porovnání vedle sebe Visual Basic – datové typy, najdete v části [datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="char-type"></a>Znakový typ  
 `Char` Datový typ je jeden znak Unicode (16 bitů) dva bajtů. Pokud proměnnou vždy obsahuje přesně jeden znak, deklarujte ji jako `Char`. Příklad:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Každý možné hodnoty ve `Char` nebo `String` proměnná *code bodu*, nebo kód znaku ve znakové sadě Unicode. Znaky znakové sady Unicode obsahovat základní znakové sadě ASCII, různé další písmena abecedy, akcenty, tyto symboly, zlomků, znaky s diakritikou a matematické a technické symboly.  
  
> [!NOTE]
>  Znak Unicode nastavení rezervy kód ukazuje D800 prostřednictvím DFFF (55296 prostřednictvím 55551 decimal) pro *náhradního páry*, vyžadující dvě hodnoty 16bitové představuje jeden kód bod. A `Char` proměnné nemůže přidržet pár náhradní a `String` používá dvě místa k uložení těchto pár.  
  
 Další informace najdete v tématu [Char – datový typ](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>String – typ  
 `String` Datový typ je posloupnost nula nebo více znaků Unicode (16 bitů) dva bajtů. Pokud proměnná může obsahovat nekonečný počet znaků, deklarujte ji jako `String`. Příklad:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Další informace najdete v tématu [String – datový typ](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Viz také  
 [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
