---
title: "Datové typy znaků (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1066444ba3a98f26fc2a35135a50b2954c6b992
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="character-data-types-visual-basic"></a>Datové typy znaků (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]poskytuje *znak datové typy* jak nakládat s tiskových a zobrazitelné znaků. Při obě řešit znaky znakové sady Unicode, `Char` obsahují jeden znak, zatímco `String` obsahuje nekonečný počet znaků.  
  
 Pro tabulku, která zobrazuje porovnání vedle sebe [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] datové typy, najdete v části [datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="char-type"></a>Znakový typ  
 `Char` Datový typ je jeden znak Unicode (16 bitů) dva bajtů. Pokud proměnnou vždy obsahuje přesně jeden znak, deklarujte ji jako `Char`. Příklad:  
  
 [!code-vb[VbVbalrCharTypes#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]  
  
 Každý možné hodnoty ve `Char` nebo `String` proměnná *code bodu*, nebo kód znaku ve znakové sadě Unicode. Znaky znakové sady Unicode obsahovat základní znakové sadě ASCII, různé další písmena abecedy, akcenty, tyto symboly, zlomků, znaky s diakritikou a matematické a technické symboly.  
  
> [!NOTE]
>  Znak Unicode nastavení rezervy kód ukazuje D800 prostřednictvím DFFF (55296 prostřednictvím 55551 decimal) pro *náhradního páry*, vyžadující dvě hodnoty 16bitové představuje jeden kód bod. A `Char` proměnné nemůže přidržet pár náhradní a `String` používá dvě místa k uložení těchto pár.  
  
 Další informace najdete v tématu [Char – datový typ](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>String – typ  
 `String` Datový typ je posloupnost nula nebo více znaků Unicode (16 bitů) dva bajtů. Pokud proměnná může obsahovat nekonečný počet znaků, deklarujte ji jako `String`. Příklad:  
  
 [!code-vb[VbVbalrCharTypes#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]  
  
 Další informace najdete v tématu [String – datový typ](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Viz také  
 [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Řešení potíží s datové typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
