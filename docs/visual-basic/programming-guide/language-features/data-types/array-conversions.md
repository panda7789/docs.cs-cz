---
title: "Převody pole (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 40dc9805157dd0bc991ca2375c3436aa6b6e09a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="array-conversions-visual-basic"></a>Převody pole (Visual Basic)
Typ pole můžete převést na typ různých pole zadaný splňovat následující podmínky:  
  
-   **Stejné pořadí.** Pořadí dvě polí musí být stejná, to znamená, musí mít stejný počet dimenzí. Ale délek příslušných dimenzí, nemusíte být stejné.  
  
-   **Datový typ elementu.** Datové typy elementů obě pole musí být typu odkaz. Nelze převést `Integer` pole k `Long` pole nebo dokonce na `Object` pole, protože nejméně jedna hodnota typu je zahrnuta. Další informace najdete v tématu [typy hodnot a typy odkazu](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
-   **Konvertibility.** Převod, rozšiřující nebo zužující, musí být možné mezi typy element dvěma poli. Příklad, který selže tento požadavek je pokusu o převod mezi `String` pole a pole třídy odvozené od <xref:System.Attribute?displayProperty=nameWithType>. Tyto dva typy mají nic společné a mezi nimi existuje žádný převod jakéhokoli druhu.  
  
 Převod typu jedno pole do jiné rozšíření nebo zužující podle toho, jestli rozšiřující nebo zužující převod příslušných elementů. Další informace najdete v tématu [Widening a zužující převody](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Převod na pole objektů  
 Když je deklarovat `Object` pole nebyl zadán, je její typ elementu je `Object` tak dlouho, dokud zůstává Neinicializovaný. Když je nastavena na pole určité třídy, dojde na typu třídy. Základní typ je však stále `Object`, a můžete ho nastavit následně ke druhému nesouvisejícími třídy. Vzhledem k tomu, že všechny třídy jsou odvozeny od `Object`, můžete změnit typ elementu pole z libovolné třídy na jiná třída.  
  
 V následujícím příkladu, neexistuje žádný převod mezi typy `student` a `String`, ale i odvozena od `Object`, takže všechny jsou platná.  
  
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
 Pokud je původně deklarovat pole s určité třídy, je jeho zdrojovým typem elementu třídy. Pokud je následně nastavena na pole jinou třídu, musí být převod mezi dvěma třídami.  
  
 V následujícím příkladu `students` je `student` pole. Vzhledem k tomu, že neexistuje žádný převod mezi `String` a `student`, poslední příkaz se nezdaří.  
  
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
 [Datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
