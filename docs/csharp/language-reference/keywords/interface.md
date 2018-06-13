---
title: interface (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 0320b1e287f8c7a3eb7751b68b40120f74e8f61c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266539"
---
# <a name="interface-c-reference"></a>interface (Referenční dokumentace jazyka C#)
Rozhraní obsahuje pouze signatur [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md), [události](../../../csharp/programming-guide/events/index.md) nebo [indexery](../../../csharp/programming-guide/indexers/index.md). Třída nebo struktura, která implementuje rozhraní, musí implementovat členy rozhraní zadané v definici rozhraní. V následujícím příkladu musí třída `ImplementationClass` implementovat metodu s názvem `SampleMethod`, která nemá žádné parametry a vrací `void`.  
  
 Další informace a příklady naleznete v tématu [rozhraní](../../../csharp/programming-guide/interfaces/index.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 Rozhraní může být členem oboru názvů nebo třídy a může obsahovat podpisy následujících členů:  
  
-   [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [Indexery](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [Události](../../../csharp/language-reference/keywords/event.md)  
  
 Rozhraní může dědit z jednoho nebo více základních rozhraní.  
  
 Jestliže seznam základních typů obsahuje základní třídu a rozhraní, musí se základní třída nacházet v seznamu jako první.  
  
 Třída, která implementuje rozhraní, může explicitně implementovat členy rozhraní. Explicitně implementovaný člen není přístupný prostřednictvím instance třídy, ale pouze prostřednictvím instance rozhraní.  
  
 Další informace a příklady kódu v implementace explicitního rozhraní najdete v tématu [explicitní implementace rozhraní](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje implementaci rozhraní. V tomto příkladu obsahuje rozhraní deklaraci vlastnosti a třída obsahuje implementaci. Jakákoli instance třídy, která implementuje rozhraní `IPoint`, má celočíselné vlastnosti `x` a `y`.  
  
 [!code-csharp[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
 [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)  
 [Použití vlastností](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [Použití indexerů](../../../csharp/programming-guide/indexers/using-indexers.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)
