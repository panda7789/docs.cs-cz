---
title: 'Postupy: Převedení objektu na jiný typ'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: cdb78bc66867ce27076d7b7e42de6a2880cb3a8c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393958"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>Postupy: Převedení objektu na jiný typ v jazyce Visual Basic
Proměnnou převedete `Object` na jiný datový typ pomocí klíčového slova pro převod, jako je například [CType funkce](../../../language-reference/functions/ctype-function.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad převede `Object` proměnnou na `Integer` a `String` .  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 Pokud víte, že obsah `Object` proměnné je určitého datového typu, je lepší převést proměnnou na tento datový typ. Pokud budete nadále používat `Object` proměnnou, získáte buď *zabalení* a *rozbalení* (pro typ hodnoty) nebo *pozdní vazba* (pro typ odkazu). Tyto operace vybírají delší dobu spuštění a zpomalují výkon.  
  
## <a name="compile-the-code"></a>Kompilovat kód  
 Tento příklad vyžaduje:  
  
- Odkaz na <xref:System?displayProperty=nameWithType> obor názvů.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Object>
- [Převody typů v jazyce Visual Basic](type-conversions.md)
- [Rozšíření a zúžení převodů](widening-and-narrowing-conversions.md)
- [Implicitní a explicitní převody](implicit-and-explicit-conversions.md)
- [Převody mezi řetězci a ostatními typy](conversions-between-strings-and-other-types.md)
- [Převody polí](array-conversions.md)
- [Struktury](structures.md)
- [Datové typy](../../../language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../language-reference/functions/type-conversion-functions.md)
