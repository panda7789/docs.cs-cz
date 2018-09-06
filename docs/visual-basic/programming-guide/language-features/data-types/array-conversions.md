---
title: Převody pole (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 93e6365a70f52f730b016cd4d4ac9382baeeba55
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43784878"
---
# <a name="array-conversions-visual-basic"></a>Převody pole (Visual Basic)
Typ pole lze převést na typ jiné pole, za předpokladu splnění následujících podmínek:  
  
-   **Stejné pořadí.** Rozměry dvě pole musí být stejná, to znamená, že musí mít stejný počet rozměrů. Délky příslušných dimenzí nemusí však být stejné.  
  
-   **Typ dat prvku.** Datové typy prvky obou polí musí být typy odkazů. Nelze převést `Integer` pole k `Long` pole, nebo dokonce k `Object` pole, protože se účastní alespoň jednu hodnotu typu. Další informace najdete v tématu [typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
-   **Převoditelnosti.** Převod, rozšíření ani zúžení při, musí být mezi typy prvků dvou polí. Je příklad, který tento požadavek se nezdaří pokus o převod mezi `String` pole a pole třídy odvozené z <xref:System.Attribute?displayProperty=nameWithType>. Tyto dva typy nemají co v běžných a neexistuje žádný převod jakéhokoli druhu mezi nimi.  
  
 Převod jednoho pole typu na jiný je rozšíření ani zúžení v závislosti na tom, jestli je převod odpovídajících prvků rozšíření ani zúžení při. Další informace najdete v tématu [Widening a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Převod na pole objektů  
 Pokud deklarujete `Object` pole bez inicializuje, jeho typ elementu je `Object` dlouho, dokud zůstává Neinicializovaný. Pokud ji nastavíte na pole určité třídy, převezme typu třídy. Jeho základní typ je však stále `Object`, a můžete ho nastavit následně do jiného objektu array nesouvisejících třídy. Protože všechny třídy odvozovat z `Object`, typ elementu pole z jiné třídy, můžete změnit na jiné třídy.  
  
 V následujícím příkladu, neexistuje žádný převod mezi typy `student` a `String`, ale oba jsou odvozeny z `Object`, takže platí všechna přiřazení.  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a>Základní typ pole  
 Pokud deklarujete původně pole s konkrétní třídou, je jeho základní typ elementu třídy. Pokud následně ji nastavíte na pole jiné třídy, musí být převod mezi dvěma třídami.  
  
 V následujícím příkladu `students` je `student` pole. Protože neexistuje žádný převod mezi `String` a `student`, poslední příkaz se nezdaří.  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Převody mezi řetězci a ostatními typy](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Postupy: převedení objektu na jiný typ v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)  
 [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
