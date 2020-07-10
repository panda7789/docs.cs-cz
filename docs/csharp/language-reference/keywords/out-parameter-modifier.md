---
title: out – modifikátor parametrů – reference jazyka C#
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 30946c85d2b64ead3f42e03da61108fa5b367779
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174806"
---
# <a name="out-parameter-modifier-c-reference"></a>out – modifikátor parametrů (Referenční dokumentace jazyka C#)

`out`Klíčové slovo způsobuje argumenty předávané odkazem. Nastaví formální parametr jako alias pro argument, který musí být proměnná. Jinými slovy, každá operace s parametrem je provedena na argumentu. Je podobně jako klíčové slovo [ref](ref.md) , s výjimkou, že `ref` vyžaduje, aby byla proměnná inicializována předtím, než je předána. Je také podobně jako klíčové slovo [in](in-parameter-modifier.md) , s výjimkou, která `in` neumožňuje volané metodě upravovat hodnotu argumentu. Chcete-li použít `out` parametr, definice metody a volající metoda musí explicitně použít `out` klíčové slovo. Zde je příklad:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE]
> `out`Klíčové slovo lze také použít s parametrem obecného typu k určení toho, že parametr typu je kovariantní. Další informace o použití `out` klíčového slova v tomto kontextu naleznete v tématu [out (Generic modifikátor)](out-generic-modifier.md).
  
Proměnné předané jako `out` argumenty není nutné inicializovat před předáním volání metody. Nicméně volaná metoda je vyžadována pro přiřazení hodnoty před vrácením metody.  
  
`in` `ref` `out` Klíčová slova, a nejsou považována za součást signatury metody pro účely řešení přetížení. Proto metody nemohou být přetíženy, pokud jediným rozdílem je, že jedna metoda přebírá `ref` `in` argument or a druhý přebírá `out` argument. Následující kód například nebude zkompilován:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Přetížení je právní, ale pokud jedna metoda přebírá `ref` `in` argument, nebo `out` a druhý nemá žádný z těchto modifikátorů, jako je:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Kompilátor zvolí nejlepší přetížení porovnáním modifikátorů parametrů na webu volání s modifikátory parametru použitými ve volání metody.

Vlastnosti nejsou proměnné a proto je nelze předat jako `out` parametry.
  
`in` `ref` Klíčová slova, a nelze použít `out` pro následující typy metod:  
  
- Asynchronní metody, které definujete pomocí modifikátoru [Async](./async.md) .  
  
- Metody iterátoru, které zahrnují [návratový návrat](./yield.md) nebo `yield break` příkaz yield.  

Kromě toho [rozšiřující metody](../../programming-guide/classes-and-structs/extension-methods.md) mají následující omezení:

- `out`Klíčové slovo nelze použít pro první argument metody rozšíření.
- `ref`Klíčové slovo nelze použít u prvního argumentu metody rozšíření, pokud argument není struct nebo obecný typ, který není omezen na strukturu.
- `in`Klíčové slovo nelze použít, pokud první argument není struktura. `in`Klíčové slovo nelze použít pro žádný obecný typ, ani v případě, že je omezení typu struct.

## <a name="declaring-out-parameters"></a>Deklarace `out` parametrů

Deklarace metody s `out` argumenty je klasické alternativní řešení, které vrací více hodnot. Počínaje jazykem C# 7,0 zvažte u podobných scénářů [hodnoty řazené kolekce členů](../builtin-types/value-tuples.md) . Následující příklad používá `out` k vrácení tří proměnných s jedním voláním metody. Třetí argument je přiřazen null. To umožňuje metodám vracet hodnoty volitelně.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>Volání metody s `out` argumentem

V jazyce C# 6 a starší je nutné deklarovat proměnnou v samostatném příkazu před tím, než je předáte jako `out` argument. Následující příklad deklaruje proměnnou s názvem předtím, `number` než je předána metodě [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) , která se pokusí převést řetězec na číslo.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

Počínaje jazykem C# 7,0 můžete deklarovat `out` proměnnou v seznamu argumentů volání metody, nikoli v deklaraci samostatné proměnné. Tím se vytvoří více kompaktní, čitelný kód a také neúmyslně přiřadíte hodnotu proměnné před voláním metody. Následující příklad je podobný předchozímu příkladu s tím rozdílem, že definuje `number` proměnnou ve volání metody [Int32. TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) .

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  

V předchozím příkladu `number` je proměnná silně typu jako `int` . Můžete také deklarovat implicitní typovou místní proměnnou, jak je uvedeno v následujícím příkladu.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  

## <a name="c-language-specification"></a>Specifikace jazyka C#  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Parametry metody](./method-parameters.md)
