---
title: Typy dat
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
ms.openlocfilehash: 928d7fb6a40873641ae3e91e057c272b946a0091
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393712"
---
# <a name="data-types-in-visual-basic"></a>Datové typy v jazyce Visual Basic
*Datový typ* programovacího prvku odkazuje na druh dat, která může obsahovat, a způsob, jakým tato data ukládají. Datové typy se vztahují na všechny hodnoty, které mohou být uloženy v paměti počítače nebo zapojeny do vyhodnocení výrazu. Každá proměnná, literál, konstanta, výčet, vlastnost, parametr procedury, argument procedury a návratová hodnota procedury mají datový typ.  
  
## <a name="declared-data-types"></a>Deklarované datové typy  
 Můžete definovat programový prvek pomocí příkazu deklarace a zadat jeho datový typ s `As` klauzulí. V následující tabulce jsou uvedeny příkazy, které slouží k deklaraci různých prvků.  
  
|Programovací element|Deklarace datového typu|  
|-------------------------|---------------------------|  
|Proměnná|V [příkazu Dim](../../../language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Literál|Literální znak typu; Viz "znaky typu literálu" v [znacích typu](type-characters.md)<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Trvalé|V [příkazu const](../../../language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Výčet|V [příkazu enum](../../../language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Vlastnost|V [příkazu Property](../../../language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Parametr procedury|V příkazu [Sub](../../../language-reference/statements/sub-statement.md), [příkazu Function](../../../language-reference/statements/function-statement.md)nebo [operátoru](../../../language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Argument procedury|V kódu volajícího; každý argument je programový prvek, který již byl deklarován, nebo výraz obsahující deklarované prvky<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Návratová hodnota procedury|V [příkazu funkce](../../../language-reference/statements/function-statement.md) nebo [příkazu operátoru](../../../language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Seznam datových typů Visual Basic najdete v tématu [datové typy](../../../language-reference/data-types/index.md).  
  
## <a name="see-also"></a>Viz také

- [Znaky typu](type-characters.md)
- [Základní datové typy](elementary-data-types.md)
- [Složené datové typy](composite-data-types.md)
- [Obecné typy v Visual Basic](generic-types.md)
- [Typy hodnot a typy odkazu](value-types-and-reference-types.md)
- [Převody typů v jazyce Visual Basic](type-conversions.md)
- [Struktury](structures.md)
- [N-tice](tuples.md)
- [Řešení potíží s datovými typy](troubleshooting-data-types.md)
- [Datové typy](../../../language-reference/data-types/index.md)
- [Účinné používání datových typů](efficient-use-of-data-types.md)
