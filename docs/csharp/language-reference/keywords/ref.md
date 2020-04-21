---
title: ref klíčové slovo - C# Reference
ms.date: 04/21/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 494a46040d6cc33c5284449779fae89705fd29c2
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738829"
---
# <a name="ref-c-reference"></a>ref (Referenční dokumentace jazyka C#)

Klíčové `ref` slovo označuje hodnotu, která je předána odkazem. Používá se ve čtyřech různých kontextech:

- V podpisu metody a volání metody předat argument metodě odkazem. Další informace naleznete [v tématu Předávání argument odkazem](#passing-an-argument-by-reference).
- V podpisu metody, chcete-li vrátit hodnotu volajícímu odkazem. Další informace naleznete v [tématu Reference return values](#reference-return-values).
- V těle člena označuje, že referenční vrácená hodnota je uložena místně jako odkaz, který volající zamýšlí změnit, nebo obecně místní proměnná přistupuje k jiné hodnotě odkazem. Další informace naleznete v tématu [Ref locals](#ref-locals).
- V `struct` prohlášení o `ref struct` prohlášení `readonly ref struct`o prohlášení a nebo . Další informace naleznete [ `ref` v](../builtin-types/struct.md#ref-struct) části struktura [typy struktury](../builtin-types/struct.md) článku.

## <a name="passing-an-argument-by-reference"></a>Předání argumentu odkazem

Při použití v seznamu parametrů metody `ref` klíčové slovo označuje, že argument je předán odkazem, nikoli hodnotou. Klíčové `ref` slovo vytvoří formální parametr alias pro argument, který musí být proměnnou. Jinými slovy, každá operace na parametr je provedena na argument. Například pokud volající předá výraz místní proměnné nebo výraz přístupu prvku pole a volaná metoda nahradí objekt, na který odkazuje ref parametr, pak volajícího místní proměnné nebo pole element nyní odkazuje na nový objekt, když metoda vrátí.

> [!NOTE]
> Nepleťte si koncept předávání odkazem s pojmem typy odkazů. Tyto dva pojmy nejsou stejné. Parametr metody lze upravit `ref` bez ohledu na to, zda se jedná o typ hodnoty nebo typ odkazu. Neexistuje žádné zabalení typu hodnoty, pokud je předán odkazem.  

Chcete-li `ref` použít parametr, definice metody a volající `ref` metoda musí explicitně použít klíčové slovo, jak je znázorněno v následujícím příkladu.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Argument, který je `ref` předán `in` nebo parametr musí být inicializován před předáním. To se liší [od](out-parameter-modifier.md) out parametry, jejichž argumenty nemusí být explicitně inicializovány před jejich předáním.

Členové třídy nemohou mít podpisy, které `ref` `in`se `out`liší pouze podle , nebo . K chybě kompilátoru dochází, pokud je jediným rozdílem mezi `ref` dvěma členy typu, že jeden z nich má parametr a druhý má parametr `out`nebo `in` parametr . Následující kód, například nekompiluje.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Metody však mohou být přetíženy, `ref` `in`pokud `out` má jedna metoda , nebo parametr a druhá má parametr hodnoty, jak je znázorněno v následujícím příkladu.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 V jiných situacích, které vyžadují porovnávání `in`podpisů, například skrytí nebo přepsání , , `ref`a `out` jsou součástí podpisu a vzájemně se neshodují.  
  
 Vlastnosti nejsou proměnné. Jsou to metody a nelze `ref` je předat parametrům.  
  
 Klíčová `out` slova a `ref`klíčová `in`slova nelze použít pro následující typy metod:  
  
- Asynchronní metody, které definujete pomocí [asynchronního](async.md) modifikátoru.  
- Iterátor metody, které zahrnují výnos `yield break` výnos [return](yield.md) nebo příkaz.

Kromě toho mají [rozšiřující metody](../../programming-guide/classes-and-structs/extension-methods.md) následující omezení:

- Klíčové `out` slovo nelze použít na první argument metody rozšíření.
- Klíčové `ref` slovo nelze použít na první argument metody rozšíření, pokud argument není struktura, nebo obecný typ není omezena být struktura.
- Klíčové `in` slovo nelze použít, pokud první argument není struktura. Klíčové `in` slovo nelze použít u žádného obecného typu, a to ani v případě, že je omezeno na strukturu.

## <a name="passing-an-argument-by-reference-an-example"></a>Předání argumentu odkazem: Příklad

Předchozí příklady předat typy hodnot odkazem. Klíčové `ref` slovo můžete také použít k předání referenčních typů odkazem. Předání typu odkazu odkazem umožňuje volané metodě nahradit objekt, na který odkazuje referenční parametr volajícího. Umístění úložiště objektu je předáno metodě jako hodnota referenčního parametru. Pokud změníte hodnotu v umístění úložiště parametru (chcete-li přejděte na nový objekt), změníte také umístění úložiště, na které volající odkazuje. Následující příklad předá instanci typu `ref` odkazu jako parametr.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Další informace o předávání typů odkazů podle hodnoty a odkazu naleznete [v tématu Předávání parametrů typu odkazu](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Referenční návratové hodnoty

Referenční vrácené hodnoty (nebo ref vrátí) jsou hodnoty, které metoda vrátí odkazem na volajícího. To znamená, že volající může upravit hodnotu vrácenou metodou a tato změna se projeví ve stavu objektu, který obsahuje metodu.

Referenční vrácená hodnota je `ref` definována pomocí klíčového slova:

- V podpisu metody. Například následující podpis metody označuje, `GetCurrentPrice` že <xref:System.Decimal> metoda vrátí hodnotu odkazem.

```csharp
public ref decimal GetCurrentPrice()
```

- Mezi `return` token a proměnná `return` vrácena v příkazu v metodě. Příklad:

```csharp
return ref DecimalArray[0];
```

Aby volající mohl upravit stav objektu, musí být vrácená hodnota odkazu uložena do proměnné, která je explicitně definována jako [ref local](#ref-locals).

Volaná metoda může také `ref readonly` deklarovat vrácenou hodnotu, která vrací hodnotu odkazem, a vynutit, aby volající kód nemohl změnit vrácenou hodnotu. Volající metoda se může vyhnout kopírování vrácené hodnoty uložením hodnoty v místní proměnné [pouze pro čtení ref.](#ref-readonly-locals)

Příklad viz [Ref returns a ref locals example](#a-ref-returns-and-ref-locals-example).

## <a name="ref-locals"></a>Ref místní obyvatelé

Ref místní proměnná se používá k `return ref`odkazování na hodnoty vrácené pomocí . Místní proměnnou ref nelze inicializovat na nevratnou hodnotu bez ref. Jinými slovy, pravá strana inicializace musí být odkaz. Všechny změny hodnoty ref local se projeví ve stavu objektu, jehož metoda vrátila hodnotu odkazem.

Definujete ref místní pomocí `ref` klíčového slova před deklarace proměnné, jakož i bezprostředně před volání metody, která vrací hodnotu odkazem.

Například následující příkaz definuje ref místní hodnotu, která `GetEstimatedValue`je vrácena metodou s názvem :

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Můžete přistupovat k hodnotě odkazem stejným způsobem. V některých případech přístup k hodnotě odkazem zvyšuje výkon tím, že se vyhne potenciálně nákladné operaci kopírování. Například následující příkaz ukazuje, jak lze definovat ref místní hodnotu, která se používá k odkazu na hodnotu.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

V obou příkladech musí být `ref` klíčové slovo použito na obou místech nebo kompilátor generuje chybu CS8172, "Nelze inicializovat proměnnou odkazu s hodnotou."

Počínaje C# 7.3, iterace `foreach` proměnná příkazu může být ref místní nebo ref pro čtení místní proměnné. Další informace naleznete v článku [foreach prohlášení.](foreach-in.md)

Také počínaje C# 7.3, můžete znovu přiřadit ref místní nebo ref pouze pro čtení místní proměnné s [operátorem přiřazení ref](../operators/assignment-operator.md#ref-assignment-operator).

## <a name="ref-readonly-locals"></a>Ref pouze pro čtení místních obyvatel

Ref pouze pro čtení místní se používá k odkazování `ref readonly` na hodnoty vrácené metodou nebo vlastností, která má ve svém podpisu a používá `return ref`. Proměnná `ref readonly` kombinuje vlastnosti `ref` místní proměnné `readonly` s proměnnou: jedná se o alias k úložišti, ke kterým je přiřazena, a nelze ji změnit.

## <a name="a-ref-returns-and-ref-locals-example"></a>Ref vrátí a ref místní příklad

Následující příklad definuje `Book` třídu, <xref:System.String> která `Title` má `Author`dvě pole a . Definuje také třídu, `BookCollection` která obsahuje `Book` soukromé pole objektů. Jednotlivé objekty knihy jsou vráceny odkazem voláním jeho `GetBookByTitle` metody.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Když volající uloží hodnotu `GetBookByTitle` vrácenou metodou jako ref local, změny, které volající provede `BookCollection` na vrácenou hodnotu, se projeví v objektu, jak ukazuje následující příklad.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Zapisujte bezpečný efektivní kód](../../write-safe-efficient-code.md)
- [Návratové hodnoty podle odkazu a lokální proměnné podle odkazu](../../programming-guide/classes-and-structs/ref-returns.md)
- [Podmíněný výraz ref](../operators/conditional-operator.md#conditional-ref-expression)
- [Předávání parametrů](../../programming-guide/classes-and-structs/passing-parameters.md)
- [Parametry metody](method-parameters.md)
- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
