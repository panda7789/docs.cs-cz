---
title: Datové typy znaků (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 3b031c6e3dc04637128f95ca8e922d3298981287
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786934"
---
# <a name="character-data-types-visual-basic"></a>Datové typy znaků (Visual Basic)
Visual Basic poskytuje *znakové datové typy* řešit tisknutelný a zobrazitelný znaků. Přestože oba vypořádat se znaky Unicode, `Char` obsahuje jeden znak, zatímco `String` obsahuje nekonečný počet znaků.  
  
 Tabulka, která zobrazuje vedle sebe porovnání datových typů jazyka Visual Basic, naleznete v tématu [datové typy](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="char-type"></a>Znakový typ  
 `Char` Datový typ je jeden znak Unicode (16-bit) dva bajty. Pokud proměnná uchovává vždy přesně jeden znak, deklarujte ho jako `Char`. Příklad:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Jednotlivé možné vlastnosti v `Char` nebo `String` proměnná je *kódu bodu*, nebo kód znaku ve znakové sadě Unicode. Znaky Unicode obsahovat základní znakové sadě ASCII, různé jiné písmena abecedy, zvýraznění, symboly měny, zlomky, diakritiku a technické a matematické symboly.  
  
> [!NOTE]
>  Znaková sada Unicode rezervy kód odkazuje D800 prostřednictvím DFFF (55296 prostřednictvím 55551 decimal) pro *náhradní páry*, které vyžadují dvě hodnoty 16bitové představuje bod jeden kód. A `Char` proměnná nemůže obsahovat náhradní pár a `String` používá dvě místa k uložení těchto pár.  
  
 Další informace najdete v tématu [Char – datový typ](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>String – typ  
 `String` Datový typ je posloupnost nula nebo více znaků Unicode (16-bit) dva bajty. Pokud proměnná může obsahovat nekonečný počet znaků, deklarujte ho jako `String`. Příklad:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Další informace najdete v tématu [datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Viz také  
 [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
