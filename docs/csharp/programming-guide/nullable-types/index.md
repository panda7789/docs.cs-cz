---
title: Typy s povolenou hodnotou Null (Průvodce programováním v C#)
ms.date: 05/15/2017
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: 64b326b82cd022ed6590a232546690e2ec2a5c78
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245584"
---
# <a name="nullable-types-c-programming-guide"></a>Typy s povolenou hodnotou Null (Průvodce programováním v C#)
Typy s možnou hodnotou Null jsou instance <xref:System.Nullable%601?displayProperty=nameWithType> struktury. Typ připouštějící hodnotu Null, může představovat správný rozsah hodnot pro jeho základní typ hodnoty, a navíc další `null` hodnotu. Například `Nullable<Int32>`, čteno "S možnou hodnotou Null Int32," je možné přiřadit libovolnou hodnotu od -2147483648 do 2147483647 nebo je možné přiřadit `null` hodnotu. A `Nullable<bool>` je možné přiřadit hodnoty [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), nebo [null](../../../csharp/language-reference/keywords/null.md). Schopnost přidělit `null` číselných a logických typů je obzvláště užitečná při jednání s databází a ostatními datovými typy, které obsahují prvky, které nemusí být přiřazena hodnota. Například logické pole v databázi můžete ukládat hodnoty `true` nebo `false`, nebo může nedefinovaný. 
  
[!code-csharp[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]  
  
Další příklady najdete v tématu [použití typů s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
## <a name="nullable-types-overview"></a>Přehled typů s povolenou hodnotou Null  
 Typy připouštějící hodnotu Null, mají následující vlastnosti:  
  
-   Typy s možnou hodnotou Null představují proměnné typu hodnoty, které je možné přiřadit hodnotu `null`. Nelze vytvořit typ připouštějící hodnotu Null na základě typu odkazu. (Referenční typy již podporují `null` hodnota.)  
  
-   Syntaxe `T?` představuje zkratku pro <xref:System.Nullable%601>, kde `T` je typ hodnoty. Dvě různými formami jsou zaměnitelné.  
  
-   Přiřadí hodnotu typu s možnou hodnotou Null, stejně jako byste to udělali pro typ běžných hodnot, například `int? x = 10;` nebo `double? d = 4.108;`. Typ připouštějící hodnotu Null lze také přiřadit hodnotu `null`: `int? x = null;`.  
  
-   Použití <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> metoda vrací hodnotu přiřazenou nebo výchozí hodnotu pro základní typ, pokud je hodnota `null`, například `int j = x.GetValueOrDefault();`  
  
-   Použití <xref:System.Nullable%601.HasValue%2A> a <xref:System.Nullable%601.Value%2A> vlastnosti jen pro čtení pro testování pro hodnotu null a načtení hodnoty, jak je znázorněno v následujícím příkladu: `if(x.HasValue) j = x.Value;`  
  
    -   `HasValue` Vrátí vlastnost `true` Pokud proměnná obsahuje hodnotu, nebo `false` jde `null`.  
  
    -   `Value` Vlastnost vrací hodnotu, pokud jeden je přiřazen. V opačném případě <xref:System.InvalidOperationException?displayProperty=nameWithType> je vyvolána výjimka.  
  
    -   Výchozí hodnota pro `HasValue` je `false`. `Value` Vlastnost nemá žádnou výchozí hodnotu.  
  
    -   Můžete také použít `==` a `!=` operátory s povolenou hodnotou Null typu, jak je znázorněno v následujícím příkladu: `if (x != null) y = x;`  
  
-   Použití `??` operátor přiřazení výchozí hodnotu, která se použijí, když typ připouštějící hodnotu Null, aktuální hodnota je `null` je přiřazený k Null typu, například `int? x = null; int y = x ?? -1;`  
  
-   Vnořené typy s možnou hodnotou Null nejsou povoleny. Nebude kompilovat následující řádek: `Nullable<Nullable<int>> n;`  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace:  
  
-   [Použití typů s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [Zabalení typů s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [?? – operátor](../../../csharp/language-reference/operators/null-coalescing-operator.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Nullable>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [C#](../../../csharp/index.md)  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Co přesně pojem "zrušeno" znamená?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
