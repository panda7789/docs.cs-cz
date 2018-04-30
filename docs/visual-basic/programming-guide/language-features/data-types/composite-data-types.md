---
title: Složené datové typy (Visual Basic)
ms.custom: ''
ms.date: 04/25/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: caa832fc191ad925674e21b1237ac98328ce0bd7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="composite-data-types-visual-basic"></a>Složené datové typy (Visual Basic)
Kromě základní datové typy jazyka Visual Basic dodávek, je možné sestavit položkami různých typů vytvořit *složené datové typy* například struktury, pole a třídy. Složené datové typy můžete vytvořit z základní typy a z jiných složené typy. Můžete například definovat pole elementy struktury nebo strukturu se členy pole.  
  
## <a name="data-types"></a>Datové typy  
 Složeného typu se liší od datového typu všech jeho součástí. Například pole `Integer` elementy není `Integer` datového typu.  
  
 Datového typu pole je obvykle reprezentována pomocí typ elementu, kulaté závorky a čárky podle potřeby. Například jednorozměrné pole z `String` elementy je reprezentován jako `String()`a dvourozměrná pole `Boolean` elementy je reprezentován jako `Boolean(,)`.  
  
## <a name="structure-types"></a>Typy struktur  
 Neexistuje žádný single – datový typ, která obsahuje všechny struktury. Místo toho každá definice struktury představuje jedinečné datového typu, i v případě, že dvě struktury definovat identické prvky ve stejném pořadí. Ale pokud vytvoříte dva nebo více instancí stejnou strukturu, Visual Basic je považuje za stejného datového typu.  
  
## <a name="tuples"></a>Řazené kolekce členů

Řazené kolekce členů je lightweight struktura, která obsahuje dvě nebo více polí, jejichž typy jsou předdefinovány. Řazené kolekce členů jsou podporované počínaje 2017 Visual Basic. Řazené kolekce členů se nejčastěji používají k vrácení více hodnot z volání jedné metody bez nutnosti předání argumentů odkazem nebo balení pole vrácené ve plně zobrazené třídu nebo strukturu. Najdete v článku [řazených kolekcí členů](tuples.md) téma pro další informace o řazené kolekce členů.

## <a name="array-types"></a>Typy polí  
 Neexistuje žádný single – datový typ, která obsahuje všechna pole. Datový typ konkrétní instanci pole je dáno následující:  
  
-   Skutečnost, že se pole  
  
-   Pořadí (počet dimenzí) pole  
  
-   Typ elementu pole  
  
 Délka dané dimenze konkrétně není částí instance datového typu. Toto dokládá následující příklad.  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 V předchozím příkladu pole proměnných `arrayA` a `arrayB` jsou považovány za stejný datový typ. – `Byte()` – i když jsou inicializovány do různých délek. Proměnné `arrayB` a `arrayC` nejsou stejného typu, protože jejich typy elementu se liší. Proměnné `arrayC` a `arrayD` nejsou stejného typu, protože jejich pořadí se liší. Proměnné `arrayD` a `arrayE` stejný typ – `Short(,)` – protože jejich pořadí a typy elementů jsou stejné, i když `arrayD` ještě není inicializovaná.  
  
 Další informace o pole najdete v tématu [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="class-types"></a>Typy tříd  
 Neexistuje žádný single – datový typ, která obsahuje všechny třídy. I když jedna třída může dědit vlastnosti z jiné třídy, každá je samostatný datovým typem. Více instancí stejné třídy mají stejný datový typ. Chcete-li přiřadit jednu proměnnou instance třídy do druhého, nejen mají stejný datový typ., odkazují na stejnou instanci třídy v paměti.  
  
 Další informace o třídách naleznete v tématu [objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Postupy: Do proměnné umístit více než jednu hodnotu](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
