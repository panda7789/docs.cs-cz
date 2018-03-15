---
title: "ref (Referenční dokumentace jazyka C#)"
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 427045317e9d7d0fe3435a486b9f761908ab5e78
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="ref-c-reference"></a>ref (Referenční dokumentace jazyka C#)

`ref` – Klíčové slovo označuje hodnotu, která je předána odkazem. Používá se ve třech různých kontextů: 

- V podpis metody a volání metody, mají být předány argument metodu odkazem. V tématu [předáním argumentu podle reference](#passing-an-argument-by-reference) Další informace.

- V podpis metody, bude vrácena hodnota volajícímu odkazem. V tématu [návratové hodnoty odkaz](#reference-return-values) Další informace.

- V člen textu, k označení, že návratovou hodnotu odkazu ukládají se místně jako odkaz, který má volající v úmyslu upravit. V tématu [místní hodnoty Ref](#ref-locals) Další informace.

## <a name="passing-an-argument-by-reference"></a>Předáním argumentu podle reference

Při použití v seznamu parametrů metody, `ref` – klíčové slovo znamená, že je argumentem úspěšně odkazem, ne podle hodnoty. Účinek předání odkazem je tato všechny změny argument volané metody se odrazí v volání metody. Například pokud volající předá místní proměnné výraz nebo výraz přístup k elementu pole a nahradí názvem metoda objektu, na kterou odkazuje parametr ref pak volající je místní proměnné nebo element pole nyní odkazuje na nový objekt při Metoda vrátí.

> [!NOTE]
>  Nezaměňujte koncept předání odkazem pojmu odkazové typy. Dvěma konceptů nejsou stejné. Parametr metody mohou být upravena `ref` bez ohledu na to, zda je hodnota typu nebo typu odkazu. Když je předána odkazem neexistuje žádné zabalení typ hodnoty.  

Použít `ref` nutné explicitně zadat parametr definici metody a volání metody `ref` – klíčové slovo, jak je znázorněno v následujícím příkladu.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Argument, který je předán `ref` nebo `in` parametr se musí inicializovat před předáním. Tím se liší od [out](out-parameter-modifier.md) parametry, jejichž argumenty nemusíte před jsou předávány explicitně inicializovat.

Členy třídy, nemůže mít podpisy, které se liší pouze `ref`, `in`, nebo `out`. Chyba kompilátoru dojde, pokud mezi dva členy typu jediným rozdílem je, že jedna z nich má `ref` má parametr a druhý `out`, nebo `in` parametr. Například následující kód, není zkompilují.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
Ale metody mohou být přetíženy, když má jednu metodu `ref`, `in`, nebo `out` parametr a dalších má parametr hodnotu, jak je znázorněno v následujícím příkladu.
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 V jiných situacích, které vyžadují párování podpisu, jako je například přepsání, zobrazení nebo skrytí `in`, `ref`, a `out` jsou součástí podpisu a navzájem neodpovídají.  
  
 Vlastnosti nejsou proměnné. Jsou metody a nelze předat `ref` parametry.  
  
 Informace o tom, jak předat pole najdete v tématu [předávání polí pomocí parametrů ref a out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Nelze použít `ref`, `in`, a `out` klíčová slova pro následující typy metod:  
  
- Asynchronní metody, které definují pomocí [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor.  
- Iterator metody, které zahrnují [yield vrátit](../../../csharp/language-reference/keywords/yield.md) nebo `yield break` příkaz.  

## <a name="passing-an-argument-by-reference-an-example"></a>Předáním argumentu podle reference: příklad

V předchozích příkladech předat hodnotu typy odkazem. Můžete také `ref` – klíčové slovo předat referenční typy odkazem. Předání typu odkazu odkazem umožňuje vyvolání metody lze nahradit objektu, na který odkazuje parametr odkazu v volající. Umístění úložiště objektu je předaný metodě jako hodnota parametru odkazu. Pokud změníte hodnotu v umístění úložiště parametru (tak, aby odkazoval na nový objekt), můžete také změnit umístění úložiště, na který odkazuje volající. Následující příklad předá instance typu odkaz jako `ref` parametr.   
  
[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Další informace o tom, jak předat odkazové typy podle hodnoty a podle reference najdete v tématu [předávání parametrů typu odkazu](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Referenční dokumentace návratové hodnoty

Referenční dokumentace návratové hodnoty (nebo ref vrátí) jsou hodnoty, které metoda vrátí odkaz na volajícího. To znamená volající můžete upravit hodnota vrácená metodou a tato změna se projeví ve stavu objektu, který obsahuje metodu. 

Odkaz vrátit hodnota je definována pomocí `ref` – klíčové slovo:

- V podpis metody. Například následující indikuje metoda podpis, `GetCurrentPrice` metoda vrátí <xref:System.Decimal> hodnotu odkazem.

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- Mezi `return` token a proměnná, vrátí se v `return` příkaz v metodě. Příklad:
 
   ```csharp
   return ref DecimalArray[0];
   ``` 

V pořadí pro volající změnit stav objektu vrátit hodnota musí být uložen do proměnné, která je explicitně definován jako odkaz [ref místní](#ref-locals). 

Příklad, naleznete v části [A ref vrátí a ref místní hodnoty – příklad](#a-ref-returns-and-ref-locals-example)

## <a name="ref-locals"></a>Místní hodnoty REF

Místní proměnné ref slouží k odkazování na hodnot vrácených pomocí `return ref`.  Místní proměnné ref musí být inicializován a přiřadit ref návratovou hodnotu. Všechny změny na hodnotu místní ref se projeví ve stavu objektu, jehož metoda vrátila hodnotu odkazem.

Definovat místní ref pomocí `ref` – klíčové slovo před deklarace proměnné, a také bezprostředně před volání metody, která vrátí hodnotu odkazem. 

Například následující příkaz definuje ref místní hodnotu, která vrátí metodu s názvem `GetEstimatedValue`:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Všimněte si, že `ref` – klíčové slovo se musí použít v obou místech nebo kompilátor vygeneruje chyba CS8172, "Nelze inicializovat proměnnou podle odkazu s hodnotou". 
 
## <a name="a-ref-returns-and-ref-locals-example"></a>A vrátí ref a ref místní hodnoty – příklad

V následujícím příkladu definuje `Book` třídu, která má dva <xref:System.String> pole, `Title` a `Author`. Také definuje `BookCollection` třídu, která zahrnuje privátní pole `Book` objekty. Jednotlivé knihy objektů odkazem voláním jeho `GetBookByTitle` metoda.

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Pokud má volající ukládá hodnoty vrácené `GetBookByTitle` metoda jako místní ref změn prováděných volající návratovou hodnotu se projeví v `BookCollection` objekt, jak ukazuje následující příklad.

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Předávání parametrů](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
