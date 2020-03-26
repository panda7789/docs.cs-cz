---
title: out modifikátor parametrů - C# Reference
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: c713aa929673e51e8e9986c536bae782121c7756
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249341"
---
# <a name="out-parameter-modifier-c-reference"></a>out – modifikátor parametrů (Referenční dokumentace jazyka C#)
Klíčové `out` slovo způsobí, že argumenty, které mají být předány odkazem. Vytvoří formální parametr alias pro argument, který musí být proměnná. Jinými slovy, každá operace na parametr je provedena na argument. Je to jako klíčové slovo `ref` [ref,](ref.md) s tím rozdílem, že vyžaduje, aby proměnná byla inicializována před předáním. Je také jako [v](in-parameter-modifier.md) klíčové `in` slovo, s tím rozdílem, že neumožňuje volané metody změnit hodnotu argumentu. Chcete-li `out` použít parametr, definice metody a volající `out` metoda musí explicitně použít klíčové slovo. Například:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> Klíčové `out` slovo lze také použít s parametrem obecného typu k určení, že parametr typu je kovariantní. Další informace o použití `out` klíčového slova v tomto kontextu naleznete v [tématu out (Generic Modifikátor)](out-generic-modifier.md).
  
Proměnné předané `out` jako argumenty nemusí být inicializovány před předáním ve volání metody. Volaná metoda je však nutné přiřadit hodnotu před metoda vrátí.  
  
`in`, `ref`a `out` klíčová slova nejsou považovány za součást podpisu metody pro účely řešení přetížení. Proto metody nelze přetížit, pokud jediný rozdíl `ref` je, že jedna metoda trvá nebo `in` argument a druhý trvá `out` argument. Následující kód, například, nebude kompilovat:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Přetížení je však legální, pokud `ref`jedna `in`metoda `out` trvá , , nebo argument a druhý nemá žádný z těchto modifikátorů, jako je tento:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Kompilátor zvolí nejlepší přetížení porovnáním modifikátorů parametrů v lokalitě volání s modifikátory parametrů použitými ve volání metody.

Vlastnosti nejsou proměnné a proto `out` nelze předat jako parametry.
  
Klíčová `out` slova a `in`klíčová `ref`slova nelze použít pro následující typy metod:  
  
- Asynchronní metody, které definujete pomocí [asynchronního](./async.md) modifikátoru.  
  
- Iterátor metody, které zahrnují výnos `yield break` výnos [return](./yield.md) nebo příkaz.  

Kromě toho mají [rozšiřující metody](../../programming-guide/classes-and-structs/extension-methods.md) následující omezení:

- Keywoard `out` nelze použít na první argument metody rozšíření.
- Klíčové `ref` slovo nelze použít na první argument metody rozšíření, pokud argument není struktura, nebo obecný typ není omezena být struktura.
- Klíčové `in` slovo nelze použít, pokud první argument není struktura. Klíčové `in` slovo nelze použít u žádného obecného typu, a to ani v případě, že je omezeno na strukturu.

## <a name="declaring-out-parameters"></a>Deklarování `out` parametrů

Deklarování `out` metody s argumenty je klasické řešení vrátit více hodnot. Počínaje C# 7.0, zvažte [řazené kolekce členů](../../tuples.md) pro podobné scénáře. Následující příklad `out` používá k vrácení tři proměnné s voláním jedné metody. Všimněte si, že třetí argument je přiřazen k hodnotě null. To umožňuje metody vrátit hodnoty volitelně.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>Volání metody s `out` argumentem

V C# 6 a starší, musíte deklarovat proměnnou `out` v samostatném příkazu před předáním jako argument. Následující příklad deklaruje proměnnou pojmenovanou `number` před předáním metodě [Int32.TryParse,](xref:System.Int32.TryParse(System.String,System.Int32@)) která se pokusí převést řetězec na číslo.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

Počínaje C# 7.0, můžete `out` deklarovat proměnnou v seznamu argument volání metody, nikoli v samostatné deklaraci proměnné. To vytváří kompaktnější, čitelný kód a také zabraňuje nechtěnému přiřazení hodnoty proměnné před voláním metody. Následující příklad je jako v předchozím příkladu, `number` s tím rozdílem, že definuje proměnnou v volání [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metoda.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

V předchozím příkladu `number` je proměnná silně `int`zadána jako . Můžete také deklarovat implicitně zadávanou místní proměnnou, jako to dělá následující příklad.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a>Specifikace jazyka C#  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](./index.md)
- [Parametry metody](./method-parameters.md)
