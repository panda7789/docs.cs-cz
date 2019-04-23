---
title: Operators – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 109298a7945a6b76b35970b7b9c42e159bad8f90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979378"
---
# <a name="operators-c-programming-guide"></a>Operátory (Průvodce programováním v C#)

V jazyce C# *operátor* je prvek programu, který se použije pro jeden nebo několik *operandy* ve výrazu nebo příkazu. Operátory, které používají jeden operand, jako je operátor Inkrementace (`++`) nebo `new`, jsou označovány jako *unární* operátory. Operátory, které používají dva operandy, jako jsou aritmetické operátory (`+`,`-`,`*`,`/`), jsou označovány jako *binární* operátory. Jeden z operátorů, podmiňovací operátor (`?:`), má tři operandy a je jediným ternárním operátorem v jazyce C#.  
  
 Následující příkaz jazyka C# obsahuje jeden unární operátor a jeden operand. Operátor Inkrementace `++`, upravuje hodnotu operandu `y`.  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 Následující příkaz jazyka C# obsahuje dva binární operátory, z nichž každý používá dva operandy. Operátor přiřazení `=`, má celočíselné proměnné `y` a výraz `2 + 3` jako operandy. Výraz `2 + 3` samotné se skládá z operátoru sčítání a dvou operandů `2` a `3`.  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
## <a name="operators-evaluation-and-operator-precedence"></a>Operátory, vyhodnocení a priorita operátorů

 Operand může být platný výraz, který se skládá z jakékoli délky kódu a který může zahrnovat libovolný počet dílčích výrazů. Ve výrazu, který obsahuje více operátorů je pořadí použití operátorů určeno *priorita operátorů*, *asociativita*a závorky.  
  
 Jednotlivé operátory mají definovanou prioritu. Ve výrazu s větším počtem operátorů, které mají odlišnou prioritu, určuje priorita operátorů pořadí, ve kterém jsou operátory vyhodnoceny. Například následující příkaz přiřadí 3 `n1`.  
  
 `n1 = 11 - 2 * 4;`  
  
 Nejdříve je provedeno násobení, protože násobení má přednost před odčítáním.  
  
 Následující tabulka rozděluje operátory do kategorií podle typu operace, kterou provádí. Kategorie jsou uvedeny v pořadí podle priority.  
  
 **Primární operátory**  
  
|Výraz|Popis|  
|----------------|-----------------|  
|x[.](../../../csharp/language-reference/operators/member-access-operator.md)y<br /><br /> x?.y|Přístup ke členům<br /><br /> Podmíněný člen přístup|  
|f[(x)](../../../csharp/language-reference/operators/invocation-operator.md)|Vyvolání metod a delegátů|  
|a[&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md)<br /><br /> a?[x]|Přístup k poli a indexeru<br /><br /> Podmíněný přístup k poli a indexeru|  
|x[++](../../../csharp/language-reference/operators/arithmetic-operators.md#increment-operator-)|Postinkrementace|  
|x[--](../../../csharp/language-reference/operators/arithmetic-operators.md#decrement-operator---)|Postdekrementace|  
|[nové](../../../csharp/language-reference/keywords/new-operator.md) T(...)|Vytvoření objektu a delegátu|  
|`new` T(...){...}|Vytvoření objektu s inicializátorem. Zobrazit [inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).|  
|`new` {...}|Inicializátor anonymních objektů. Zobrazit [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).|  
|`new` T[...]|Vytvoření pole. Zobrazit [pole](../../../csharp/programming-guide/arrays/index.md).|  
|[typeof](../../../csharp/language-reference/keywords/typeof.md)(T)|Získání objektu System.Type pro T|  
|[checked](../../../csharp/language-reference/keywords/checked.md)(x)|Vyhodnocení výrazu ve zkontrolovaném kontextu|  
|[unchecked](../../../csharp/language-reference/keywords/unchecked.md)(x)|Vyhodnocení výrazu v nezkontrolovaném kontextu|  
|[výchozí](../../../csharp/language-reference/keywords/default.md) (T)|Získání výchozí hodnoty typu T|  
|[Delegát](../../../csharp/language-reference/keywords/delegate.md) {}|Anonymní funkce (anonymní metoda)|  
  
 **Unární operátory**  
  
|Výraz|Popis|  
|----------------|-----------------|  
|[+](../../../csharp/language-reference/operators/addition-operator.md)x|Identita|  
|[-](../../../csharp/language-reference/operators/subtraction-operator.md)x|Negace|  
|[\!](../../../csharp/language-reference/operators/boolean-logical-operators.md#logical-negation-operator-)x|Logická negace|  
|[~](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#bitwise-complement-operator-)x|Bitová negace.|  
|[++](../../../csharp/language-reference/operators/arithmetic-operators.md#increment-operator-)x|Preinkrementace|  
|[--](../../../csharp/language-reference/operators/arithmetic-operators.md#decrement-operator---)x|Predekrementace|  
|[(T)](../../../csharp/language-reference/operators/invocation-operator.md)x|Explicitní převod x na typ T|  
  
 **Operátory násobení**  
  
|Výraz|Popis|  
|----------------|-----------------|  
|[*](../../../csharp/language-reference/operators/arithmetic-operators.md#multiplication-operator-)|Násobení|  
|[/](../../../csharp/language-reference/operators/arithmetic-operators.md#division-operator-)|Dělení|  
|[%](../../../csharp/language-reference/operators/arithmetic-operators.md#remainder-operator-)|Zbytek|  
  
 **Operátory sčítání**  
  
|Výraz|Popis|  
|----------------|-----------------|  
|x [+](../../../csharp/language-reference/operators/addition-operator.md) y|Sčítání, řetězení řetězců, kombinování delegátů|  
|x [-](../../../csharp/language-reference/operators/subtraction-operator.md) y|Odčítání, odebrání delegátů|  
  
 **Operátory posunutí**  
  
|Výraz|Popis|
|----------------|-----------------|
|x [<\<](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#left-shift-operator-) y|Posun doleva|
|x [>>](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#right-shift-operator-) y|Posun doprava|
  
 **Relační operátory a operátory typu**  
  
|Výraz|Popis|  
|----------------|-----------------|  
|x [\<](../../../csharp/language-reference/operators/less-than-operator.md) y|Menší než|  
|x [>](../../../csharp/language-reference/operators/greater-than-operator.md) y|Větší než|  
|x [\<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) y|Menší nebo rovno|  
|x [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) y|Větší nebo rovno|  
|x [is](../../../csharp/language-reference/keywords/is.md) T|Vrátí hodnotu true, pokud x je T, jinak hodnotu false|  
|x [as](../../../csharp/language-reference/keywords/as.md) T|Vrátí x jako T, nebo hodnotu null, pokud x není T|  
  
 **Operátory rovnosti**  
  
|Výraz|Popis|  
|----------------|-----------------|  
|x [==](../../../csharp/language-reference/operators/equality-operators.md#equality-operator-) y|Rovno|  
|x [! =](../../../csharp/language-reference/operators/equality-operators.md#inequality-operator-) y|Nerovná se|  
  
 **Logické, Podmiňovací a nulové operátory**  
  
|Kategorie|Výraz|Popis|
|--------------|----------------|-----------------|
|Logický operátor AND|`x & y`|[Bitový operátor AND celého čísla](../../language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), [logická logický operátor AND](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-)|
|Logický operátor XOR|`x ^ y`|[Bitový operátor XOR celého čísla](../../language-reference/operators/bitwise-and-shift-operators.md#logical-exclusive-or-operator-), [logická logický operátor XOR](../../language-reference/operators/boolean-logical-operators.md#logical-exclusive-or-operator-)|
|Logický operátor OR|`x | y`|[Bitový operátor OR celého čísla](../../language-reference/operators/bitwise-and-shift-operators.md#logical-or-operator-), [logická logický operátor OR](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-)|
|Podmiňovací operátor AND|x [&&](../../../csharp/language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) y|Vyhodnocuje y pouze v případě, že x má hodnotu true|
|Podmiňovací operátor OR|x [ &#124; &#124; ](../../../csharp/language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) y|Vyhodnocuje y pouze v případě, že x má hodnotu false|
|Nulové sloučení|x [??](../../../csharp/language-reference/operators/null-coalescing-operator.md) y|Vyhodnotí y, pokud x má hodnotu null, jinak vyhodnotí x|
|Podmiňovací operátor|x [?](../../../csharp/language-reference/operators/conditional-operator.md) y : z|Vyhodnotí y, pokud x má hodnotu true; vyhodnotí z, pokud x má hodnotu false|
  
 **Přiřazení a anonymní operátory**  
  
|Výraz|Popis|
|----------------|-----------------|
|[=](../../../csharp/language-reference/operators/assignment-operator.md)|Přiřazení|
|x op= y|Složené přiřazení. Podporuje tyto operátory: [ += ](../../../csharp/language-reference/operators/addition-assignment-operator.md), [ -= ](../../../csharp/language-reference/operators/subtraction-assignment-operator.md), [ *= ](../../../csharp/language-reference/operators/arithmetic-operators.md#compound-assignment), [ /= ](../../../csharp/language-reference/operators/arithmetic-operators.md#compound-assignment), [ %= ](../../../csharp/language-reference/operators/arithmetic-operators.md#compound-assignment) , [&=](../../../csharp/language-reference/operators/boolean-logical-operators.md#compound-assignment), [&#124;=](../../../csharp/language-reference/operators/boolean-logical-operators.md#compound-assignment), [^=](../../../csharp/language-reference/operators/boolean-logical-operators.md#compound-assignment), [<\<=](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#compound-assignment), [>>=](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#compound-assignment)|
|(T x) [=>](../../../csharp/language-reference/operators/lambda-operator.md) y|Anonymní funkce (výraz lambda)|
  
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

 Můžete změnit chování operátorů pro vlastní třídy a struktury. Tento proces se označuje jako *přetížení operátoru*. Další informace najdete v tématu [přetížitelné operátory](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md) a [operátor](../../../csharp/language-reference/keywords/operator.md) článku – klíčové slovo.  
  
## <a name="related-sections"></a>Související oddíly

 Další informace najdete v tématu [klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md) a [operátory jazyka C#](../../../csharp/language-reference/operators/index.md).  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Příkazy, výrazy a operátory](../../../csharp/programming-guide/statements-expressions-operators/index.md)
