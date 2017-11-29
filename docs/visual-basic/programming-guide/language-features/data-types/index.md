---
title: "Datové typy v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20a24c8632e1f2193cfa86319a824dfcc038d9d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="data-types-in-visual-basic"></a>Datové typy v jazyce Visual Basic
*Datový typ* programovací elementu odkazuje na jaký typ dat může uchovávat a jak ho uloží data. Datové typy platí pro všechny hodnoty, které můžou být uložené v paměti počítače nebo účastnit vyhodnocení výrazu. Všechny proměnné, literál, konstanta, – výčet, vlastnost, parametru procedury, argumentu procedury a návratová hodnota procedury má datový typ.  
  
## <a name="declared-data-types"></a>Deklarovaný datové typy  
 Můžete definovat programovací element s příkazem deklarace, a určit její datový typ s `As` klauzule. Následující tabulka uvádí příkazy, které použijete k deklarovat různé prvky.  
  
|Element programování|Datový typ deklarace|  
|-------------------------|---------------------------|  
|Proměnná|V [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md)<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Literál|S – znak typu literálu; najdete v části "Literálové znaky typu" v [– znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|Konstanta|V [Const – příkaz](../../../../visual-basic/language-reference/statements/const-statement.md)<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|Výčet|V [Enum – příkaz](../../../../visual-basic/language-reference/statements/enum-statement.md)<br /><br /> `Public`   `Enum`   `colors`|  
|Vlastnost|V [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md)<br /><br /> `Property`   `region() As String`|  
|Parametr postupu|V [Sub příkaz](../../../../visual-basic/language-reference/statements/sub-statement.md), [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md), nebo [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|Argumentu procedury|V kódu volání; Každý argument je programovací element, který již byl deklarován nebo výraz obsahující deklarované elementy<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|Návratová hodnota procedury|V [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md) nebo [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md)<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Seznam Visual Basic – datové typy, naleznete v části [datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="see-also"></a>Viz také  
 [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Řazené kolekce členů](tuples.md)     
 [Řešení potíží s datové typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Účinné používání datových typů](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
