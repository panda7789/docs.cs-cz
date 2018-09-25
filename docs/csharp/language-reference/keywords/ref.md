---
title: REF – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 03/06/2018
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: e0b82de125246e95d8dce2a7afc20119a8a1fe4f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2018
ms.locfileid: "47027801"
---
# <a name="ref-c-reference"></a>ref (Referenční dokumentace jazyka C#)

`ref` – Klíčové slovo určuje hodnotu, která je předána odkazem. Používá se ve čtyřech různých kontextech:

- V podpisu metody a volání metody, pro předání argumentu podle odkazu na metodu. Zobrazit [předání argumentu podle odkazu](#passing-an-argument-by-reference) Další informace.
- V podpisu metody, vracet hodnotu odkazem volajícímu. Zobrazit [referenční návratové hodnoty](#reference-return-values) Další informace.
- V těle členské k označení, že návratová hodnota odkazu uložená místně jako odkaz, který si klade za cíl volajícího k úpravě nebo obecně platí, místní proměnná přistupuje ke jiná hodnota podle odkazu. Zobrazit [místních](#ref-locals) Další informace.
- V `struct` deklarace deklarovat `ref struct` nebo `ref readonly struct`. Další informace najdete v tématu [referenční sémantika s typy hodnot](../../reference-semantics-with-value-types.md).

## <a name="passing-an-argument-by-reference"></a>Předání argumentu podle odkazu

Při použití v seznamu parametrů metod, `ref` – klíčové slovo určuje, že argument se předá odkazem, ne podle hodnoty. Předávání odkazem efekt je, že všechny změny argumentů volané metody se projeví ve volání metody. Například pokud volající předává místní proměnnou výraz nebo výraz přístupu k elementu pole a volané metody nahradí objekt, na které odkazuje parametr ref a pak volajícího uživatele místní proměnné nebo element pole nyní odkazuje na nový objekt při Metoda vrátí.

> [!NOTE]
> Nezaměňujte koncept předávání odkazem s konceptem odkazových typů. Dvě koncepce nejsou stejné. Parametr metody. je možné upravovat prostřednictvím `ref` bez ohledu na to, zda je typ hodnoty nebo typ odkazu. Pokud je předána odkazem. neexistuje žádná zabalení typu hodnoty.  

Použití `ref` parametr definici metody a volající metody musíte explicitně použít `ref` – klíčové slovo, jak je znázorněno v následujícím příkladu.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Argument, který je předán `ref` nebo `in` parametr musí být inicializován před jeho předáním. Tím se liší od [si](out-parameter-modifier.md) parametry, jejichž argumenty není nutné explicitně inicializovat předtím, než jsou předány.

Členy třídy nemůže mít podpisy, které se liší pouze `ref`, `in`, nebo `out`. Chyba kompilátoru nastane, pokud jediným rozdílem mezi dva členy typu je, že jedna z nich má `ref` má parametr a druhý `out`, nebo `in` parametru. Například následující kód, nebude kompilovat.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Však metody mohou být přetíženy, když má jednu metodu `ref`, `in`, nebo `out` parametr a druhý je hodnota parametru, jak je znázorněno v následujícím příkladu.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 V jiných situacích, které vyžadují párování podpis, například přepsání, zobrazení nebo skrytí `in`, `ref`, a `out` jsou součást podpisu a navzájem neodpovídají.  
  
 Vlastnosti nejsou proměnné. Jsou metody a nelze předat `ref` parametry.  
  
 Nelze použít `ref`, `in`, a `out` klíčová slova pro následující druhy metod:  
  
- Asynchronní metody, které definujete pomocí [asynchronní](async.md) modifikátor.  
- Metody iterátorů, mezi které patří [yield return](yield.md) nebo `yield break` příkazu.  

## <a name="passing-an-argument-by-reference-an-example"></a>Předání argumentu podle odkazu: příklad

V předchozích příkladech předávání typů hodnot pomocí odkazu. Můžete také použít `ref` – klíčové slovo k předání referenční typy podle odkazu. Typ odkazu předávání odkazem umožňuje volané metody k nahrazení objektu, na které odkazuje parametr odkazu volajícího. Umístění úložiště objekt je předán metodě jako hodnota parametru odkazu. Pokud změníte hodnotu v umístění úložiště parametru (tak, aby odkazoval na nový objekt), také změnit umístění úložiště, na který odkazuje volající. Následující příklad předá instance typu odkaz jako `ref` parametru.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Další informace o tom, jak předat typy odkazů podle hodnoty a podle reference najdete v tématu [předávání parametrů typu odkazu](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Referenční návratové hodnoty

Referenční návratové hodnoty (nebo návratové) jsou hodnoty, které metoda vrací odkazem na volajícího. To znamená že volající může změnit hodnotu, vrací metoda, a tato změna se projeví ve stavu objektu, který obsahuje metodu.

Vrátí odkaz hodnota je definována pomocí `ref` – klíčové slovo:

- V podpisu metody. Například následující podpis metody Určuje, že `GetCurrentPrice` metoda vrátí hodnotu <xref:System.Decimal> hodnota podle odkazu.

```csharp
public ref decimal GetCurrentPrice()
```

- Mezi `return` token a vrácené v proměnné `return` příkaz v metodě. Příklad:

```csharp
return ref DecimalArray[0];
```

Aby volající změnit stav objektu, vrátit hodnota musí být uložen do proměnné, která není výslovně uveden jako odkaz [lokální proměnná podle odkazu](#ref-locals).

Příklad najdete v tématu [A návratové a příklad místní hodnoty ref](#a-ref-returns-and-ref-locals-example)

## <a name="ref-locals"></a>Místní referenční hodnoty

Lokální proměnná ref se používá k odkazování na hodnoty, které jsou vráceny za použití `return ref`. Lokální proměnná ref nejde inicializovat na návratovou hodnotu bez ref. Jinými slovy pravou stranu inicializace musí být odkaz. Všechny změny na hodnotu lokální proměnnou se projeví ve stavu objektu, jehož metoda vrátila hodnotu odkazem.

Definice lokální proměnnou s použitím `ref` – klíčové slovo před deklaraci proměnné, stejně jako bezprostředně před volání metody, která vrátí hodnotu odkazem.

Například následující příkaz definuje ref místní hodnotu, která je vrácena metodou s názvem `GetEstimatedValue`:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Stejným způsobem můžete přistupovat hodnota podle odkazu. V některých případech se přístup k hodnota podle odkazu zvyšuje výkon se vyhnout operaci kopírování potenciálně nákladné. Následující příkaz například ukazuje, jak jeden můžete definovat, který se používá k odkazování hodnotu lokální hodnota ref.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Všimněte si, že v obou příkladech `ref` – klíčové slovo musí být použit v obou místech, nebo kompilátor vygeneruje chybu CS8172 "Nelze inicializovat proměnnou podle odkazu s hodnotou".

## <a name="a-ref-returns-and-ref-locals-example"></a>A návratové a příklad místní hodnoty ref

Následující příklad definuje `Book` třídu, která má dvě <xref:System.String> pole, `Title` a `Author`. Definuje také `BookCollection` třídu, která obsahuje privátní pole `Book` objekty. Jednotlivé knihy objekty jsou vráceny ve vztahu voláním jeho `GetBookByTitle` metoda.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Pokud volající uloží hodnoty vrácené `GetBookByTitle` změny, které umožňuje volajícímu návratovou hodnotu metody jako lokální proměnná podle odkazu, se projeví v `BookCollection` objektu, jak ukazuje následující příklad.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Referenční sémantika s typy hodnot](../../reference-semantics-with-value-types.md)  
- [Předávání parametrů](../../programming-guide/classes-and-structs/passing-parameters.md)  
- [Parametry metody](method-parameters.md)  
- [Referenční dokumentace jazyka C#](../index.md)  
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
- [Klíčová slova jazyka C#](index.md)