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
ms.openlocfilehash: d29e8771d61c04cf35aa71b5ba7fbba0d308c730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965681"
---
# <a name="character-data-types-visual-basic"></a>Datové typy znaků (Visual Basic)
Visual Basic poskytuje *znakové datové typy* pro práci s tisknutelnými a zobrazitelnými znaky. I když se zaměří se znaky Unicode `Char` , `String` obsahuje jeden znak, který obsahuje nekonečný počet znaků.  
  
 Tabulku, která zobrazuje souběžné porovnání Visual Basicch datových typů, najdete v tématu [datové typy](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="char-type"></a>Typ znaku  
 `Char` Datový typ je jeden dvoubajtový (16bitový) znak Unicode. Pokud proměnná vždy ukládá přesně jeden znak, deklarujte ho jako `Char`. Příklad:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Každá možná hodnota v `Char` proměnné nebo `String` je *bod kódu*nebo kód znaku v sadě znaků Unicode. Mezi znaky Unicode patří základní znaková sada ASCII, různá další písmena abecedy, zvýraznění, symboly měn, zlomky, diakritická znaménka a matematické a technické symboly.  
  
> [!NOTE]
> Znaková sada Unicode rezervuje body kódu D800 prostřednictvím DFFF (55296 až 55551 desítk) pro *náhradní páry*, které vyžadují, aby hodnoty 2 16-bit představovaly jediný bod kódu. Proměnná nemůže obsahovat náhradní pár `String` a k uchování takového páru používá dvě pozice. `Char`  
  
 Další informace naleznete v tématu [char data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Typ řetězce  
 `String` Datový typ je sekvence nula nebo více dvoubajtových (16 bitů) znaků Unicode. Pokud proměnná může obsahovat nekonečný počet znaků, deklarujte ji jako `String`. Příklad:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Další informace najdete v tématu [datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Viz také:

- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Obecné typy v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Převody typu v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
