---
title: Struktury (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: ffb5b8da6c72056620cf890f38af4e7a8116ab3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322985"
---
# <a name="structs-c-programming-guide"></a>Struktury (Průvodce programováním v C#)
Struktury jsou definované pomocí [struktura](../../../csharp/language-reference/keywords/struct.md) – klíčové slovo, například:  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 Struktury sdílet většina stejnou syntaxi jako třídy, i když jsou omezenější než třídy struktury:  
  
-   V deklaraci struktura nelze inicializovat pole Pokud jsou deklarovány jako const nebo statické.  
  
-   Struktury nelze deklarovat výchozí konstruktor (konstruktor bez parametrů) nebo finalizační metody.  
  
-   Struktury se zkopírují na přiřazení. Když struktury je přiřazen k nové proměnné, ale data se zkopírují a všechny změny nové kopie nezmění data pro původní kopii. To je důležité si pamatovat při práci s kolekcí typů hodnot, jako je například slovník\<string, myStruct >.  
  
-   Struktury jsou hodnotové typy a třídy jsou odkazové typy.  
  
-   Na rozdíl od třídy, struktury se dá vytvořit instance bez použití `new` operátor.  
  
-   Struktury můžou deklarovat konstruktory, které mají parametry.  
  
-   Struktury nemůže Zdědit z jiné třídy nebo struktury a nesmí být základní třídy. Všechny struktury dědí přímo z `System.ValueType`, který dědí z `System.Object`.  
  
-   Struktury můžete implementovat rozhraní.  
  
-   Struktura slouží jako typ s možnou hodnotou Null a lze přiřadit hodnotu null.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
-   [Použití struktur](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Typy s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [Postupy: Zjištění rozdílu mezi předáním struktury a předáním odkazu na třídu metodě](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [Postupy: Implementace uživatelem definovaných převodů mezi strukturami](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Třídy](../../../csharp/programming-guide/classes-and-structs/classes.md)
