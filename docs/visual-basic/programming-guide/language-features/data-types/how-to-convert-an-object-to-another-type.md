---
title: 'Postupy: převod objektu na jiný typ'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 6d16e0eafc3fa9233037abe0c92dcb1945ca8da9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341577"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>Postupy: Převedení objektu na jiný typ v jazyce Visual Basic
Převedete `Object` proměnnou na jiný datový typ pomocí klíčového slova převodu, jako je [CType funkce](../../../../visual-basic/language-reference/functions/ctype-function.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad převede `Object` proměnnou na `Integer` a `String`.  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 Pokud víte, že obsah `Object` proměnné jsou konkrétního datového typu, je lepší převést proměnnou na tento datový typ. Pokud budete nadále používat `Object` proměnnou, bude se vám účtovat *zabalení* a *rozbalení* (pro typ hodnoty) nebo *pozdní vazba* (pro typ odkazu). Tyto operace vybírají delší dobu spuštění a zpomalují výkon.  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkaz na obor názvů <xref:System?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Object>
- [Převody typu v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Převody mezi řetězci a ostatními typy](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Převody polí](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
