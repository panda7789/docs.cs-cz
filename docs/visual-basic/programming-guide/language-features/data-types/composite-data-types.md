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
ms.openlocfilehash: 3e8df5ccfeca4bc0a19237ba6d59e9d0747080ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394295"
---
# <a name="composite-data-types-visual-basic"></a>Složené datové typy (Visual Basic)
Kromě základních datových typů Visual Basic dodávek můžete také sestavit položky různých typů pro vytváření *složených datových typů* , jako jsou struktury, pole a třídy. Můžete sestavit složené datové typy z základních typů a z jiných složených typů. Například můžete definovat pole prvků struktury nebo strukturu s členy pole.  
  
## <a name="data-types"></a>Typy dat  
 Složený typ se liší od datového typu kterékoli z jeho komponent. Například pole `Integer` prvků není `Integer` datového typu.  
  
 Datový typ pole je obvykle reprezentován pomocí typu prvku, závorek a čárek podle potřeby. Například jednorozměrné pole `String` elementů je reprezentované jako `String()` a dvojrozměrné pole `Boolean` prvků je reprezentované jako `Boolean(,)` .  
  
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
  
 V předchozím příkladu proměnné pole `arrayA` a `arrayB` jsou považovány za stejný datový typ –, a to i v případě, že `Byte()` jsou inicializovány na jinou délku. Proměnné `arrayB` a `arrayC` nejsou stejného typu, protože jejich typy elementů se liší. Proměnné `arrayC` a `arrayD` nejsou stejného typu, protože jejich pořadí se liší. Proměnné `arrayD` a `arrayE` mají stejný typ – `Short(,)` – protože jejich pořadí a typy prvků jsou stejné, přestože `arrayD` ještě není inicializovaná.  
  
 Další informace o polích naleznete v tématu [Arrays](../arrays/index.md).  
  
## <a name="class-types"></a>Typy tříd  
 Neexistuje žádný jediný datový typ obsahující všechny třídy. I když jedna třída může dědit z jiné třídy, každý z nich je samostatný datový typ. Více instancí stejné třídy je stejného datového typu. Pokud přiřadíte jednu proměnnou instance třídy k druhému, nikoli pouze stejný datový typ, nasměrují na stejnou instanci třídy v paměti.  
  
 Další informace o třídách naleznete v tématu [Objects and Classes](../objects-and-classes/index.md).  
  
## <a name="see-also"></a>Viz také

- [Datové typy](index.md)
- [Základní datové typy](elementary-data-types.md)
- [Obecné typy v Visual Basic](generic-types.md)
- [Typy hodnot a typy odkazu](value-types-and-reference-types.md)
- [Převody typů v jazyce Visual Basic](type-conversions.md)
- [Struktury](structures.md)
- [Řešení potíží s datovými typy](troubleshooting-data-types.md)
- [Postupy: Uchování více než jedné hodnoty v proměnné](how-to-hold-more-than-one-value-in-a-variable.md)
