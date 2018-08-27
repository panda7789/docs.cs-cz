---
title: 'Postupy: Převedení objektu na jiný typ v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: f168b3021ee1dbe3c82edc22fc779767c30446b8
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2018
ms.locfileid: "42912010"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>Postupy: Převedení objektu na jiný typ v jazyce Visual Basic
Převedete `Object` proměnné na jiný datový typ. pomocí klíčového slova převodu [funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad převádí `Object` proměnné `Integer` a `String`.  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 Pokud víte, že obsah `Object` proměnné jsou konkrétní datového typu, je vhodnější převést proměnnou datového typu. Pokud budete nadále používat `Object` proměnné, se vám účtovat buď *zabalení* a *rozbalení* (pro typ hodnoty) nebo *pozdní vazby* (pro odkazový typ). Tyto operace všechny trvat delší dobu spuštění a provést pomalejší výkon.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkaz na <xref:System?displayProperty=nameWithType> oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Object>  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Převody mezi řetězci a ostatními typy](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Převody polí](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)  
 [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
