---
title: Převody polí
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
ms.openlocfilehash: 1d20b01200d3f967e3355dc6e9651291003d140e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402002"
---
# <a name="array-conversions-visual-basic"></a>Převody pole (Visual Basic)
Typ pole můžete převést na jiný typ pole, pokud splňujete následující podmínky:  
  
- **Stejné pořadí.** Pořadí dvou polí musí být stejné, to znamená, že musí mít stejný počet rozměrů. Nicméně délky příslušných dimenzí nemusejí být stejné.  
  
- **Datový typ elementu.** Datové typy prvků obou polí musí být odkazové typy. Pole nelze převést `Integer` na `Long` pole nebo dokonce na `Object` pole, protože je zapojen alespoň jeden typ hodnoty. Další informace naleznete v tématu [typy hodnot a typy odkazů](value-types-and-reference-types.md).  
  
- **Převoditelnosti.** Převod, buď rozšiřující nebo zúžený, musí být možný mezi typy prvků obou polí. Příklad, který tento požadavek neprojde, je pokus o převod mezi `String` polem a polem třídy odvozené z <xref:System.Attribute?displayProperty=nameWithType> . Tyto dva typy nemají nic společného a mezi nimi neexistují žádné konverze žádného druhu.  
  
 Převod jednoho typu pole na jiný je rozšiřující nebo zúžený v závislosti na tom, zda je převod odpovídajících prvků rozšiřující nebo zúžený. Další informace najdete v tématu [rozšiřování a zúžení převodů](widening-and-narrowing-conversions.md).  
  
## <a name="conversion-to-an-object-array"></a>Převod na pole objektů  
 Při deklaraci `Object` pole bez jeho inicializace je jeho typ prvku `Object` tak dlouho, dokud zůstává Neinicializovaný. Když je nastavena na pole konkrétní třídy, převezme typ dané třídy. Jeho nadřízený typ je však stále nadále `Object` a lze jej následně nastavit na jiné pole nesouvisející třídy. Vzhledem k tomu, že všechny třídy jsou odvozeny z `Object` , můžete změnit typ elementu pole z libovolné třídy na jinou třídu.  
  
 V následujícím příkladu neexistuje žádný převod mezi typy `student` a `String` , ale obě jsou odvozeny z `Object` , takže všechna přiřazení jsou platná.  
  
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
  
 V následujícím příkladu `students` je `student` pole. Vzhledem k tomu, že mezi a neexistuje žádný převod `String` `student` , poslední příkaz se nezdařil.  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>Viz také

- [Datové typy](index.md)
- [Převody typů v jazyce Visual Basic](type-conversions.md)
- [Implicitní a explicitní převody](implicit-and-explicit-conversions.md)
- [Převody mezi řetězci a ostatními typy](conversions-between-strings-and-other-types.md)
- [Postupy: Převedení objektu na jiný typ v jazyce Visual Basic](how-to-convert-an-object-to-another-type.md)
- [Datové typy](../../../language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../language-reference/functions/type-conversion-functions.md)
- [Pole](../arrays/index.md)
