---
title: Složené datové typy (Visual Basic)
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: c7243108d0b7c06f48a21f343321322bb2cc2946
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560279"
---
# <a name="composite-data-types-visual-basic"></a>Složené datové typy (Visual Basic)
Kromě základní datové typy jazyka Visual Basic nabízí, můžete také sestavit položky k vytvoření různých typů *složené datové typy* například třídy, struktury a pole. Složené datové typy můžete vytvořit ze základních typů a z dalších složené typy. Například můžete definovat pole prvky struktury nebo strukturu s členy pole.  
  
## <a name="data-types"></a>Datové typy  
 Složený typ se liší od typu dat jeho součástí. Například pole `Integer` prvky není `Integer` datového typu.  
  
 Datový typ pole se obvykle vyjadřuje typ elementu, závorek a čárky podle potřeby. Například jednorozměrné pole `String` elementů je vyjádřena jako `String()`a dvourozměrné pole `Boolean` elementů je vyjádřena jako `Boolean(,)`.  
  
## <a name="structure-types"></a>Typy struktur  
 Neexistuje žádný jednotlivý typ dat obsahující všechny struktury. Místo toho každá definice struktury představuje jedinečný datový typ, i v případě, že dvě struktury definují stejné prvky ve stejném pořadí. Nicméně pokud vytvoříte dvě nebo víc instancí se stejnou strukturou, Visual Basic je považuje za stejného datového typu.  
  
## <a name="tuples"></a>Řazené kolekce členů

Řazená kolekce členů je zjednodušené strukturu, která obsahuje dvě nebo více polí, jejichž typy jsou předdefinovány. Řazené kolekce členů jsou podporovány, počínaje rokem 2017 jazyka Visual Basic. Řazené kolekce členů se nejčastěji používají k vrácení více hodnot z jedné metody volání bez nutnosti předávat argumenty odkazem nebo balení pole vrácené ve více zobrazené třídy nebo struktury. Zobrazit [řazených kolekcí členů](tuples.md) tématu pro další informace o řazené kolekce členů.

## <a name="array-types"></a>Typy polí  
 Neexistuje žádný jednotlivý typ dat skládající se z aplikací všechna pole. Datový typ konkrétní instanci pole se určuje takto:  
  
-   Skutečnost, že se pole  
  
-   Pořadí (počet rozměrů) v poli  
  
-   Typ prvku pole  
  
 Délka dané dimenze zejména, není součástí instance datového typu. Toto dokládá následující příklad.  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 V předchozím příkladu pole proměnné `arrayA` a `arrayB` jsou považovány za stejný datový typ. – `Byte()` – i když jsou inicializovány na různých délek. Proměnné `arrayB` a `arrayC` nejsou stejného typu, protože jejich typy elementů se liší. Proměnné `arrayC` a `arrayD` nejsou stejného typu, protože jejich pořadí se liší. Proměnné `arrayD` a `arrayE` mají stejný typ – `Short(,)` – protože jejich pořadí a typy elementů jsou stejné, i když `arrayD` ještě není inicializovaná.  
  
 Další informace o polích naleznete v tématu [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="class-types"></a>Typy tříd  
 Neexistuje žádný jednotlivý typ dat obsahující všechny třídy. I když jedna třída může dědit z jiné třídy, každá je samostatná datová typu. Více instancí jedné třídy mají stejný datový typ. Pokud přiřadíte jednu proměnnou instance třídy na jiný, nejen mají stejný datový typ., ukazují na stejnou instanci třídy v paměti.  
  
 Další informace o třídách naleznete v tématu [objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="see-also"></a>Viz také:
- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Postupy: Uchování více než jedné hodnoty v proměnné](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
