---
title: Znakové datové typy
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 33dd4c62776ae8c5ec0ce0a6d0858a7ed0d047fb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401989"
---
# <a name="character-data-types-visual-basic"></a>Datové typy znaků (Visual Basic)
Visual Basic poskytuje *znakové datové typy* pro práci s tisknutelnými a zobrazitelnými znaky. I když se zaměří se znaky Unicode, `Char` obsahuje jeden znak, který `String` obsahuje nekonečný počet znaků.  
  
 Tabulku, která zobrazuje souběžné porovnání Visual Basicch datových typů, najdete v tématu [datové typy](../../../language-reference/data-types/index.md).  
  
## <a name="char-type"></a>Typ znaku  
 `Char`Datový typ je jeden dvoubajtový (16bitový) znak Unicode. Pokud proměnná vždy ukládá přesně jeden znak, deklarujte ho jako `Char` . Příklad:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Každá možná hodnota v `Char` proměnné nebo `String` je *bod kódu*nebo kód znaku v sadě znaků Unicode. Mezi znaky Unicode patří základní znaková sada ASCII, různá další písmena abecedy, zvýraznění, symboly měn, zlomky, diakritická znaménka a matematické a technické symboly.  
  
> [!NOTE]
> Znaková sada Unicode rezervuje body kódu D800 prostřednictvím DFFF (55296 až 55551 desítk) pro *náhradní páry*, které vyžadují, aby hodnoty 2 16-bit představovaly jediný bod kódu. `Char`Proměnná nemůže obsahovat náhradní pár a k `String` uchování takového páru používá dvě pozice.  
  
 Další informace naleznete v tématu [char data Type](../../../language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Typ řetězce  
 `String`Datový typ je sekvence nula nebo více dvoubajtových (16 bitů) znaků Unicode. Pokud proměnná může obsahovat nekonečný počet znaků, deklarujte ji jako `String` . Příklad:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Další informace najdete v tématu [datový typ String](../../../language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Viz také

- [Základní datové typy](elementary-data-types.md)
- [Složené datové typy](composite-data-types.md)
- [Obecné typy v Visual Basic](generic-types.md)
- [Typy hodnot a typy odkazu](value-types-and-reference-types.md)
- [Převody typů v jazyce Visual Basic](type-conversions.md)
- [Řešení potíží s datovými typy](troubleshooting-data-types.md)
- [Znaky typu](type-characters.md)
