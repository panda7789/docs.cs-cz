---
title: out – modifikátor parametrů - C# odkaz
ms.custom: seodec18
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 769d1ac0b6266c87e99605c76a25e016f15eb11c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125739"
---
# <a name="out-parameter-modifier-c-reference"></a>out – modifikátor parametrů (Referenční dokumentace jazyka C#)
`out` – Klíčové slovo způsobí, že argumenty, které mají být předány podle odkazu. Formální parametr je alias pro argument, který musí být proměnná. Jinými slovy všechny operace na parametr se provádí na argumentu. Je třeba [ref](ref.md) – klíčové slovo, s výjimkou, že `ref` vyžaduje, aby před jeho předáním inicializovat proměnnou. Je také třeba [v](in-parameter-modifier.md) – klíčové slovo, s výjimkou, že `in` neumožňuje volané metody, chcete-li změnit hodnotu argumentu. Použití `out` parametr definici metody a volající metody musíte explicitně použít `out` – klíčové slovo. Příklad:  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> `out` – Klíčové slovo je také možné pomocí parametru obecného typu k určení, že parametr typu je kovariant. Další informace týkající se použití `out` – klíčové slovo v tomto kontextu, najdete v článku [out (generický modifikátor)](out-generic-modifier.md).
  
Proměnné se předaly jako `out` argumenty nemusí být inicializován před předáním ve volání metody. Volané metody je však potřeba přiřadit hodnotu dříve, než metoda vrátí.  
  
`in`, `ref`, A `out` klíčová slova nejsou považované za součást podpisu metody za účelem řešení přetížení. Proto metody nemohou být přetíženy, pokud je jediným rozdílem je, že jedna metoda má `ref` nebo `in` argument a druhý bere `out` argument. Například následující kód, nebude kompilovat:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Přetěžování je právní, ale pokud jedna metoda má `ref`, `in`, nebo `out` argument a druhý nemá žádná z těchto parametrů, následujícím způsobem:  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

Kompilátor volí přetížení optimální to provede spárováním odpovídajících modifikátorech parametrů v lokalitě volání do modifikátorech parametrů používaných pro volání metody.
 
Vlastnosti nejsou proměnné a proto ji nelze předat jako `out` parametry.
  
Nelze použít `in`, `ref`, a `out` klíčová slova pro následující druhy metod:  
  
-   Asynchronní metody, které definujete pomocí [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor.  
  
-   Metody iterátorů, mezi které patří [yield return](../../../csharp/language-reference/keywords/yield.md) nebo `yield break` příkazu.  

## <a name="declaring-out-parameters"></a>Deklarování `out` parametry   

Deklarace metody s `out` argumenty se klasické alternativní řešení Chcete-li vrátit více hodnot. Počínaje C# 7.0, vezměte v úvahu [řazených kolekcí členů](../../tuples.md) pro podobné scénáře. Následující příklad používá `out` vrátit tří proměnných s stačí jediná metoda volání. Všimněte si, že třetí argument je přiřazená na hodnotu null. To umožňuje volitelně návratové hodnoty metod.  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

## <a name="calling-a-method-with-an-out-argument"></a>Volání metody s `out` argument

V jazyce C# 6 a starší, před jeho předáním jako musíte deklarovat proměnnou v samostatné prohlášení `out` argument. Následující příklad deklaruje proměnnou s názvem `number` předtím, než je předána [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metodu, která se pokusí převést řetězec na číslo.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

Od verze C# 7.0, lze deklarovat `out` proměnné v seznamu argumentů volání metody, nikoli v samostatné deklarace proměnné. Vytvoří kód kompaktnějším a srozumitelné a také vám zabrání od nedopatřením přiřazení hodnoty proměnné před voláním metody. V následujícím příkladu je podobně jako v předchozím příkladu, s tím rozdílem, že definuje `number` proměnné ve volání [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metody.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
V předchozím příkladu `number` proměnná je silně typováno jako `int`. Implicitně typovaná lokální proměnná, můžete také deklarovat jako v následujícím příkladu.

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a>Specifikace jazyka C#  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
- [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)
