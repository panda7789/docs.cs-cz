---
title: Struktury (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: abe39b336aa8e9aa7a8a8ee96ed6848804644ddd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518700"
---
# <a name="structs-c-programming-guide"></a>Struktury (Průvodce programováním v C#)
Struktury jsou definované pomocí [struktura](../../../csharp/language-reference/keywords/struct.md) – klíčové slovo, například:  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 Většinu podle stejné syntaxe jako třídy, struktury sdílet, ačkoli struktury jsou omezeny více než třídy:  
  
-   V deklaraci struktury pole nelze inicializovat, jestliže nejsou deklarovány jako const nebo statické.  
  
-   Struktury nelze deklarovat výchozí konstruktor (konstruktor bez parametrů) nebo finalizační metodu.  
  
-   Struktury se zkopírují na přiřazení. Když je struktura přiřazena nové proměnné, se data kopírují a jakékoli změny nová kopie nezmění data pro původní kopírování. To je důležité pamatovat při práci s kolekcemi typů hodnot, jako je například slovníku\<řetězec, myStruct >.  
  
-   Struktury jsou typy hodnot a třídy jsou odkazové typy.  
  
-   Na rozdíl od tříd, struktur dá vytvořit instance bez použití `new` operátor.  
  
-   Struktury můžete deklarovat konstruktory, které mají parametry.  
  
-   Struktura nemůže dědit z jiné třídy nebo struktury a nemůže být základní třídy. Všechny struktury dědí přímo z `System.ValueType`, který dědí z `System.Object`.  
  
-   Struktury můžou implementovat rozhraní.  
  
-   Struktura může sloužit jako typ připouštějící hodnotu Null a je možné přiřadit hodnotu null.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
-   [Použití struktur](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Typy s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [Postupy: Zjištění rozdílu mezi předáním struktury a předáním odkazu na třídu metodě](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [Postupy: Implementace uživatelem definovaných převodů mezi strukturami](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Třídy](../../../csharp/programming-guide/classes-and-structs/classes.md)
