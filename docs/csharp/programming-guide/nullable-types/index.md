---
title: Typy s povolenou hodnotou Null (Průvodce programováním v C#)
ms.date: 05/15/2017
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: 10a2d4ab248276d9fdbe9d2bba40ccdd02a77408
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="nullable-types-c-programming-guide"></a>Typy s povolenou hodnotou Null (Průvodce programováním v C#)
Typy s možnou hodnotou Null jsou instancemi třídy <xref:System.Nullable%601?displayProperty=nameWithType> struktura. Typ s možnou hodnotou Null může představovat správné rozsahu hodnot pro její základní typ hodnoty, plus další `null` hodnotu. Například `Nullable<Int32>`, výrazný "S možnou hodnotou Null Int32," může být přiřazena libovolná hodnota od -2147483648 2147483647 nebo jej lze přiřadit `null` hodnotu. A `Nullable<bool>` je možné přiřadit hodnoty [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), nebo [null](../../../csharp/language-reference/keywords/null.md). Schopnost přidělit `null` na typy číselné a logická hodnota je obzvláště užitečná při pracujete s databází a jiné datové typy, které obsahují prvky, které nemusí být přiřazena hodnota. Například logické pole v databázi můžete ukládat hodnoty `true` nebo `false`, nebo to může být definovaný. 
  
[!code-csharp[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]  
  
Další příklady najdete v tématu [pomocí typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
## <a name="nullable-types-overview"></a>Přehled typů s povolenou hodnotou Null  
 Typy s možnou hodnotou Null mít následující vlastnosti:  
  
-   Typy s možnou hodnotou Null představují typ hodnoty proměnné, které lze přiřadit hodnotu `null`. Nelze vytvořit typ s možnou hodnotou Null založený na typu odkaz. (Referenční dokumentace typy již podporují `null` hodnotu.)  
  
-   Syntaxe `T?` je sdružená vlastnost <xref:System.Nullable%601>, kde `T` je typ hodnoty. Jsou dva formuláře zaměnitelné.  
  
-   Stejně jako obyčejnou hodnota typu, například přiřadit hodnotu Null typu `int? x = 10;` nebo `double? d = 4.108`. Typ s možnou hodnotou Null lze také přiřadit hodnotu `null`: `int? x = null.`  
  
-   Použití <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> metoda vrátí přiřazenou hodnotu nebo výchozí hodnota pro základní typ, pokud je hodnota `null`, například `int j = x.GetValueOrDefault();`  
  
-   Použití <xref:System.Nullable%601.HasValue%2A> a <xref:System.Nullable%601.Value%2A> vlastnosti jen pro čtení k testování pro hodnotu null a načíst hodnotu, jak je znázorněno v následujícím příkladu: `if(x.HasValue) j = x.Value;`  
  
    -   `HasValue` Vlastnost vrátí `true` Pokud proměnná obsahuje hodnotu, nebo `false` Pokud je `null`.  
  
    -   `Value` Vlastnost vrací hodnotu, pokud jeden je přiřazen. V opačném <xref:System.InvalidOperationException?displayProperty=nameWithType> je vyvolána výjimka.  
  
    -   Výchozí hodnota pro `HasValue` je `false`. `Value` Vlastnost nemá žádnou výchozí hodnotu.  
  
    -   Můžete také `==` a `!=` operátory s Null typu, jak je znázorněno v následujícím příkladu: `if (x != null) y = x;`  
  
-   Použití `??` operátor přiřadit výchozí hodnotu, která bude použita, pokud typu s povolenou hodnotou Null, jejíž aktuální hodnota je `null` se přiřadí k použití hodnot Null typu, například `int? x = null; int y = x ?? -1;`  
  
-   Vnořené typy s možnou hodnotou Null nejsou povoleny. Následující řádek nebude kompilace: `Nullable<Nullable<int>> n;`  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
-   [Použití typů s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [Zabalení typů s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [?? – operátor](../../../csharp/language-reference/operators/null-conditional-operator.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Nullable>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [C#](../../../csharp/index.md)  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Co přesně 'zrušit' znamená?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
