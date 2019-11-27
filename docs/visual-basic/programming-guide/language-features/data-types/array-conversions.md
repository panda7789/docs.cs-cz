---
title: Převody pole
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
ms.openlocfilehash: 622ebe8a77f2dfbeb35e0408be48622d93d409c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345862"
---
# <a name="array-conversions-visual-basic"></a>Převody pole (Visual Basic)
Typ pole můžete převést na jiný typ pole, pokud splňujete následující podmínky:  
  
- **Stejné pořadí.** Pořadí dvou polí musí být stejné, to znamená, že musí mít stejný počet rozměrů. Nicméně délky příslušných dimenzí nemusejí být stejné.  
  
- **Datový typ elementu.** Datové typy prvků obou polí musí být odkazové typy. Pole `Integer` nelze převést na `Long` pole, ani na pole `Object`, protože se jedná o alespoň jeden typ hodnoty. Další informace naleznete v tématu [typy hodnot a typy odkazů](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
- **Převoditelnosti.** Převod, buď rozšiřující nebo zúžený, musí být možný mezi typy prvků obou polí. Příklad, který tento požadavek neprojde, je pokus o převod mezi `String` polem a polem třídy odvozené z <xref:System.Attribute?displayProperty=nameWithType>. Tyto dva typy nemají nic společného a mezi nimi neexistují žádné konverze žádného druhu.  
  
 Převod jednoho typu pole na jiný je rozšiřující nebo zúžený v závislosti na tom, zda je převod odpovídajících prvků rozšiřující nebo zúžený. Další informace najdete v tématu [rozšiřování a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Převod na pole objektů  
 Při deklaraci pole `Object` bez jeho inicializace je jeho typ prvku `Object`, pokud zůstane Neinicializovaný. Když je nastavena na pole konkrétní třídy, převezme typ dané třídy. Jeho nadřízený typ je však stále `Object`a lze jej následně nastavit na jiné pole nesouvisející třídy. Vzhledem k tomu, že všechny třídy jsou odvozeny z `Object`, můžete změnit typ elementu pole z libovolné třídy na jakoukoliv jinou třídu.  
  
 V následujícím příkladu neexistuje žádný převod mezi typy `student` a `String`, ale obě jsou odvozeny z `Object`, takže všechna přiřazení jsou platná.  
  
```vb  
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
 Pokud jste původně deklarovali pole s určitou třídou, jeho základní typ prvku je tato třída. Pokud jste následně nastavili pole jiné třídy, musí být převod mezi těmito dvěma třídami.  
  
 V následujícím příkladu je `students` `student` poli. Vzhledem k tomu, že mezi `String` a `student`neexistuje žádný převod, poslední příkaz se nezdařil.  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Převody typu v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Převody mezi řetězci a ostatními typy](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Postupy: převod objektu na jiný typ v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
