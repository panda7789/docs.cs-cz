---
title: Složené datové typy
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
ms.openlocfilehash: 1c099c5082f1c4173a50c70998c99135c94821e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346379"
---
# <a name="composite-data-types-visual-basic"></a>Složené datové typy (Visual Basic)
Kromě základních datových typů Visual Basic dodávek můžete také sestavit položky různých typů pro vytváření *složených datových typů* , jako jsou struktury, pole a třídy. Můžete sestavit složené datové typy z základních typů a z jiných složených typů. Například můžete definovat pole prvků struktury nebo strukturu s členy pole.  
  
## <a name="data-types"></a>Datové typy  
 Složený typ se liší od datového typu kterékoli z jeho komponent. Například pole `Integer` prvků není datový typ `Integer`.  
  
 Datový typ pole je obvykle reprezentován pomocí typu prvku, závorek a čárek podle potřeby. Například jednorozměrné pole `String` prvků je reprezentované jako `String()`a dvourozměrné pole `Boolean` prvků je reprezentované jako `Boolean(,)`.  
  
## <a name="structure-types"></a>Typy struktury  
 Neexistuje žádný jediný datový typ, který by zahrnoval všechny struktury. Místo toho každá definice struktury představuje jedinečný datový typ, a to i v případě, že dvě struktury definují identické prvky ve stejném pořadí. Pokud však vytvoříte dvě nebo více instancí stejné struktury, Visual Basic považují být za stejný datový typ.  
  
## <a name="tuples"></a>N-tice

Řazená kolekce členů je odlehčená struktura, která obsahuje dvě nebo více polí, jejichž typy jsou předdefinované. Řazené kolekce členů jsou podporované od Visual Basic 2017. Řazené kolekce členů se nejčastěji používají pro vracení více hodnot z jednoho volání metody bez nutnosti předávat argumenty odkazem nebo zabalení vrácených polí v rozsáhlejší třídě nebo struktuře. Další informace o řazených kolekcích členů najdete v tématu [řazené kolekce členů](tuples.md) .

## <a name="array-types"></a>Typy polí  
 Neexistuje žádný jediný datový typ, který by zahrnoval všechna pole. Datový typ konkrétní instance pole je určen následujícím způsobem:  
  
- Fakt, že se jedná o pole  
  
- Pořadí (počet rozměrů) pole  
  
- Typ prvku pole  
  
 Konkrétně délka dané dimenze není součástí datového typu instance. Toto dokládá následující příklad.  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 V předchozím příkladu jsou proměnné pole `arrayA` a `arrayB` považovány za stejný datový typ – `Byte()`, i když jsou inicializovány na jinou délku. Proměnné `arrayB` a `arrayC` nejsou stejného typu, protože jejich typy elementů se liší. Proměnné `arrayC` a `arrayD` nejsou stejného typu, protože se liší jejich pořadí. Proměnné `arrayD` a `arrayE` mají stejný typ – `Short(,)`, protože jejich typy pořadí a elementů jsou stejné, i když `arrayD` ještě není inicializovaný.  
  
 Další informace o polích naleznete v tématu [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="class-types"></a>Typy tříd  
 Neexistuje žádný jediný datový typ obsahující všechny třídy. I když jedna třída může dědit z jiné třídy, každý z nich je samostatný datový typ. Více instancí stejné třídy je stejného datového typu. Pokud přiřadíte jednu proměnnou instance třídy k druhému, nikoli pouze stejný datový typ, nasměrují na stejnou instanci třídy v paměti.  
  
 Další informace o třídách naleznete v tématu [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Obecné typy v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Převody typu v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Postupy: Do proměnné umístit více než jednu hodnotu](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
