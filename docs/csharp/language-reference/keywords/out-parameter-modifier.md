---
title: modifikátor parametru out – C# referenční informace
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: bc3814b91ed4327f4af1a4a1bfbda632b0393bb8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713273"
---
# <a name="out-parameter-modifier-c-reference"></a>out – modifikátor parametrů (Referenční dokumentace jazyka C#)
Klíčové slovo `out` způsobí, že argumenty budou předány odkazem. Nastaví formální parametr jako alias pro argument, který musí být proměnná. Jinými slovy, každá operace s parametrem je provedena na argumentu. Je podobně jako klíčové slovo [ref](ref.md) s tím rozdílem, že `ref` vyžaduje, aby byla proměnná inicializována před předáním. Je také podobně jako klíčové slovo [in](in-parameter-modifier.md) , s výjimkou, že `in` nepovoluje, aby volaná metoda změnila hodnotu argumentu. Chcete-li použít parametr `out`, musí definice metody a volající metoda explicitně používat klíčové slovo `out`. Příklad:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> Klíčové slovo `out` lze také použít s parametrem obecného typu k určení toho, že parametr typu je kovariantní. Další informace o použití klíčového slova `out` v tomto kontextu naleznete v tématu [out (Generic modifikátor)](out-generic-modifier.md).
  
Proměnné předané jako argumenty `out` nemusejí být před předáním do volání metody inicializovány. Nicméně volaná metoda je vyžadována pro přiřazení hodnoty před vrácením metody.  
  
Klíčová slova `in`, `ref`a `out` nejsou považována za součást signatury metody pro účely překladu přetížení. Proto metody nemohou být přetíženy, pokud jediným rozdílem je, že jedna metoda přebírá `ref` nebo `in` argument a druhý přebírá `out` argument. Následující kód například nebude zkompilován:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Přetížení je právní, ale pokud jedna metoda přebírá `ref`, `in`nebo `out` argument a druhý nemá žádný z těchto modifikátorů, jako je:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Kompilátor zvolí nejlepší přetížení porovnáním modifikátorů parametrů na webu volání s modifikátory parametru použitými ve volání metody.
 
Vlastnosti nejsou proměnné a proto je nelze předat jako parametry `out`.
  
Klíčová slova `in`, `ref`a `out` nelze použít pro následující typy metod:  
  
- Asynchronní metody, které definujete pomocí modifikátoru [Async](./async.md) .  
  
- Metody iterátoru, které zahrnují příkaz [yield return](./yield.md) nebo `yield break`.  

## <a name="declaring-out-parameters"></a>Deklarace `out`ch parametrů   

Deklarace metody s argumenty `out` je klasické řešení, které vrací více hodnot. Počínaje C# 7,0 zvažte [řazené kolekce členů](../../tuples.md) pro podobné scénáře. Následující příklad používá `out` k vrácení tří proměnných s jedním voláním metody. Všimněte si, že třetí argument je přiřazen null. To umožňuje metodám vracet hodnoty volitelně.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>Volání metody s argumentem `out`

V C# 6 a starších verzích musíte deklarovat proměnnou v samostatném příkazu předtím, než je předáte jako argument `out`. Následující příklad deklaruje proměnnou s názvem `number` předtím, než je předána metodě [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) , která se pokusí převést řetězec na číslo.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

Počínaje C# 7,0 můžete deklarovat `out` proměnnou v seznamu argumentů volání metody, nikoli v deklaraci samostatné proměnné. Tím se vytvoří více kompaktní, čitelný kód a také neúmyslně přiřadíte hodnotu proměnné před voláním metody. Následující příklad je podobný předchozímu příkladu s tím rozdílem, že definuje `number` proměnnou ve volání metody [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) .

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
V předchozím příkladu je proměnná `number` silně typu jako `int`. Můžete také deklarovat implicitní typovou místní proměnnou, jak je uvedeno v následujícím příkladu.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a>C# – jazyková specifikace  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Parametry metody](./method-parameters.md)
