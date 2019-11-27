---
title: Datové typy
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
ms.openlocfilehash: 01529b36a68b8db6febb80b69a7bd81486a47087
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346353"
---
# <a name="data-types-in-visual-basic"></a>Datové typy v jazyce Visual Basic
*Datový typ* programovacího prvku odkazuje na druh dat, která může obsahovat, a způsob, jakým tato data ukládají. Datové typy se vztahují na všechny hodnoty, které mohou být uloženy v paměti počítače nebo zapojeny do vyhodnocení výrazu. Každá proměnná, literál, konstanta, výčet, vlastnost, parametr procedury, argument procedury a návratová hodnota procedury mají datový typ.  
  
## <a name="declared-data-types"></a>Deklarované datové typy  
 Definujete programový prvek pomocí příkazu deklarace a zadáte jeho datový typ s klauzulí `As`. V následující tabulce jsou uvedeny příkazy, které slouží k deklaraci různých prvků.  
  
|Programovací element|Deklarace datového typu|  
|-------------------------|---------------------------|  
|Proměnná|V [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Doslovný|Literální znak typu; Viz "znaky typu literálu" v [znacích typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Konstanta|V [příkazu const](../../../../visual-basic/language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Výčet|V [příkazu enum](../../../../visual-basic/language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Vlastnost|V [příkazu Property](../../../../visual-basic/language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Parametr procedury|V příkazu [Sub](../../../../visual-basic/language-reference/statements/sub-statement.md), [příkazu Function](../../../../visual-basic/language-reference/statements/function-statement.md)nebo [operátoru](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Argument procedury|V kódu volajícího; každý argument je programový prvek, který již byl deklarován, nebo výraz obsahující deklarované prvky<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Návratová hodnota procedury|V [příkazu funkce](../../../../visual-basic/language-reference/statements/function-statement.md) nebo [příkazu operátoru](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Seznam datových typů Visual Basic najdete v tématu [datové typy](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="see-also"></a>Viz také:

- [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Obecné typy v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Převody typu v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Řazené kolekce členů](tuples.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
- [Účinné používání datových typů](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
