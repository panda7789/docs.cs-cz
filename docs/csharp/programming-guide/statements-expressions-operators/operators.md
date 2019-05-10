---
title: Operators – C# Průvodce programováním
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: fd10999066f599d819ef188e09028c64c6a5e9e6
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65064044"
---
# <a name="operators-c-programming-guide"></a>Operátory (Průvodce programováním v C#)

V jazyce C# *operátor* je prvek programu, který se použije pro jeden nebo několik *operandy* ve výrazu nebo příkazu. Operátory, které používají jeden operand, jako je operátor Inkrementace (`++`) nebo `new`, jsou označovány jako *unární* operátory. Operátory, které používají dva operandy, jako jsou aritmetické operátory (`+`,`-`,`*`,`/`), jsou označovány jako *binární* operátory. Jeden z operátorů, podmiňovací operátor (`?:`), má tři operandy a je jediným ternárním operátorem v jazyce C#.  
  
 Následující příkaz jazyka C# obsahuje jeden unární operátor a jeden operand. Operátor Inkrementace `++`, upravuje hodnotu operandu `y`.  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 Následující příkaz jazyka C# obsahuje dva binární operátory, z nichž každý používá dva operandy. Operátor přiřazení `=`, má celočíselné proměnné `y` a výraz `2 + 3` jako operandy. Výraz `2 + 3` samotné se skládá z operátoru sčítání a dvou operandů `2` a `3`.  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
Operand může být platný výraz, který se skládá z jakékoli délky kódu a který může zahrnovat libovolný počet dílčích výrazů. Ve výrazu, který obsahuje více operátorů je pořadí použití operátorů určeno *priorita operátorů*, *asociativita*a závorky.  

## <a name="operator-precedence"></a>Priorita operátorů
  
Jednotlivé operátory mají definovanou prioritu. Ve výrazu s větším počtem operátorů, které mají odlišnou prioritu, určuje priorita operátorů pořadí, ve kterém jsou operátory vyhodnoceny. Například následující příkaz přiřadí 3 `n1`:

```csharp
n1 = 11 - 2 * 4;
```

Nejdříve je provedeno násobení, protože násobení má přednost před odčítáním.

Pro úplný seznam C# operátory seřazené podle úrovně priority, naleznete v tématu [ C# operátory](../../language-reference/operators/index.md).
  
## <a name="associativity"></a>Asociativita

 Pokud výraz obsahuje dva nebo více operátorů se stejnou prioritou, jsou vyhodnocovány na základě asociativity. Operátory asociativní zleva se vyhodnocují v pořadí zleva doprava. Například `x * y / z` se vyhodnotí jako `(x * y) / z`. Operátory asociativní zprava se vyhodnocují v pořadí zprava doleva. Například operátor přiřazení je asociativní zprava. Pokud by nebyl, následující kód by způsobil chybu.  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 Další příklad tříhodnotový operátor ([?:](../../../csharp/language-reference/operators/conditional-operator.md)) je asociativní zprava. Většina binární operátory jsou asociativní zleva.  
  
 Ať už jsou operátory ve výrazu asociativní zleva nebo asociativní zprava, jsou nejdříve vyhodnocovány operandy jednotlivých výrazů, zleva doprava. Následující příklady znázorňují pořadí vyhodnocení operátorů a operandů.  
  
|Příkaz|Pořadí vyhodnocení|  
|---------------|-------------------------|  
|`a = b`|a, b, =|  
|`a = b + c`|a, b, c, +, =|  
|`a = b + c * d`|a, b, c, d, *, +, =|  
|`a = b * c + d`|a, b, c, *, d, +, =|  
|`a = b - c + d`|a, b, c, -, d, +, =|  
|`a += b -= c`|a, b, c, -=, +=|  
  
## <a name="adding-parentheses"></a>Přidávání závorek

 Pořadí stanovené na základě priority operátorů a asociativity můžete změnit pomocí závorek. Například `2 + 3 * 2` obvykle vyhodnocen jako 8, protože operátory násobení přednost před operátory sčítání. Nicméně pokud napíšete výraz jako `(2 + 3) * 2`, sčítání je vyhodnoceno před násobením a výsledkem je 10. Následující příklady znázorňují pořadí vyhodnocení ve výrazech se závorkami. Stejně jako v předchozích příkladech se operandy vyhodnocují ještě před použitím operátoru.  
  
|Příkaz|Pořadí vyhodnocení|  
|---------------|-------------------------|  
|`a = (b + c) * d`|a, b, c, +, d, *, =|  
|`a = b - (c + d)`|a, b, c, d, +, -, =|  
|`a = (b + c) * (d - e)`|a, b, c, +, d, e, -, *, =|  
  
## <a name="operator-overloading"></a>Přetížení operátoru

Můžete definovat chování určitých operátorů pro vlastní třídy a struktury. Tento proces se označuje jako *přetížení operátoru*. Další informace najdete v tématu [přetížitelné operátory](overloadable-operators.md) a [operátor](../../language-reference/keywords/operator.md) článku – klíčové slovo.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Příkazy, výrazy a operátory](index.md)
- [Operátory jazyka C#](../../language-reference/operators/index.md)
- [Klíčová slova operátorů](../../language-reference/keywords/operator-keywords.md)
