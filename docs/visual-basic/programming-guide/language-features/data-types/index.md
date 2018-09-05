---
title: Datové typy v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
ms.openlocfilehash: 83c3d9976f61513165e917da73dd50e846db3e83
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747347"
---
# <a name="data-types-in-visual-basic"></a>Datové typy v jazyce Visual Basic
*Datový typ* programovací element odkazuje na druhu dat může obsahovat a způsobu, jakým ukládá tato data. Datové typy platí pro všechny hodnoty, které mohou být uloženy v paměti počítače či k účasti na vyhodnocení výrazu. Každou proměnnou, literal, – konstanta, výčtu, vlastnost, parametr procedury, argumentu procedury a návratová hodnota procedury má datový typ.  
  
## <a name="declared-data-types"></a>Deklarované typy dat  
 Můžete definovat programovací element s příkazu deklarace, a určit její datový typ s `As` klauzuli. Následující tabulka uvádí příkazy, které používáte pro deklarování jednotlivých prvků.  
  
|Programování – element|Deklarace datového typu|  
|-------------------------|---------------------------|  
|Proměnná|V [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|literál|Znak typu literálu; Viz "Typ literály" v [znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Konstanta|V [Const – příkaz](../../../../visual-basic/language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Výčet|V [Enum – příkaz](../../../../visual-basic/language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Vlastnost|V [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Parametr procedury|V [dílčí příkaz](../../../../visual-basic/language-reference/statements/sub-statement.md), [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md), nebo [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Argumentu procedury|Ve volajícím kódu; Každý argument je programovací element, který již byl deklarován nebo výrazu obsahujícího deklarované elementy<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Návratová hodnota procedury|V [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md) nebo [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Seznam datových typů jazyka Visual Basic najdete v tématu [datové typy](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="see-also"></a>Viz také  
 [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Řazené kolekce členů](tuples.md)     
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)  
 [Účinné používání datových typů](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
