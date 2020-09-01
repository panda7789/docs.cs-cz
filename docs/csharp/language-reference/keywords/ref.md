---
description: ref – klíčové slovo – Reference jazyka C#
title: ref – klíčové slovo – Reference jazyka C#
ms.date: 04/21/2020
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 58a4ce30e11ca023b50e5e53b1f1554a30d44390
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137081"
---
# <a name="ref-c-reference"></a>ref (Referenční dokumentace jazyka C#)

`ref`Klíčové slovo označuje hodnotu, která je předána odkazem. Používá se ve čtyřech různých kontextech:

- V signatuře metody a ve volání metody předejte argument metodě odkazem. Další informace naleznete v tématu [předání argumentu odkazem](#passing-an-argument-by-reference).
- V signatuře metody pro vrácení hodnoty volajícímu odkazem. Další informace najdete v tématu [referenční návratové hodnoty](#reference-return-values).
- V těle člena, aby označoval, že návratová hodnota odkazu je uložená místně jako odkaz, který volající chce změnit, nebo obecně místní proměnná přistupuje k jiné hodnotě odkazem. Další informace naleznete v tématu [místní hodnoty REF](#ref-locals).
- V `struct` deklaraci pro deklaraci `ref struct` nebo `readonly ref struct` . Další informace naleznete [ `ref` v části struktura v článku](../builtin-types/struct.md#ref-struct) [typy struktury](../builtin-types/struct.md) .

## <a name="passing-an-argument-by-reference"></a>Předání argumentu odkazem

Při použití v seznamu parametrů metody `ref` označuje klíčové slovo, že argument je předán odkazem, nikoli hodnotou. `ref`Klíčové slovo nastaví formální parametr jako alias pro argument, který musí být proměnná. Jinými slovy, každá operace s parametrem je provedena na argumentu. Například pokud volající předává výraz místní proměnné nebo výraz přístupu k elementu pole a volaná metoda nahradí objekt, na který odkazuje parametr ref, pak místní proměnná volajícího nebo prvek pole nyní odkazuje na nový objekt, když se metoda vrátí.

> [!NOTE]
> Nepleťte si koncept předávání odkazem s konceptem typů odkazů. Tyto dvě koncepce nejsou stejné. Parametr metody lze změnit `ref` bez ohledu na to, zda se jedná o typ hodnoty nebo typ odkazu. Pokud je předána odkazem, není k dispozici žádný zabalení typu hodnoty.  

Chcete-li použít `ref` parametr, definice metody a volající metoda musí explicitně používat `ref` klíčové slovo, jak je znázorněno v následujícím příkladu.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Argument, který je předán `ref` parametru nebo, `in` musí být inicializován před předáním. To se liší od parametrů [out](out-parameter-modifier.md) , jejichž argumenty není nutné před předáním explicitně inicializovat.

Členové třídy nemohou mít signatury, které se liší pouze pomocí `ref` , `in` nebo `out` . K chybě kompilátoru dojde, pokud jediným rozdílem mezi dvěma členy typu je, že jeden z nich má `ref` parametr a druhý má `out` parametr, nebo `in` . Následující kód například není zkompilován.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Nicméně metody mohou být přetíženy v případě, že jedna metoda má `ref` `in` parametr, nebo `out` a druhá má parametr hodnoty, jak je znázorněno v následujícím příkladu.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 V jiných situacích, které vyžadují porovnávání signatur, jako je například skrytí nebo přepsání,, `in` `ref` a `out` jsou součástí podpisu a vzájemně se neshodují.  
  
 Vlastnosti nejsou proměnné. Jsou to metody a nelze je předat `ref` parametrům.  
  
 `ref` `in` Klíčová slova, a nelze použít `out` pro následující typy metod:  
  
- Asynchronní metody, které definujete pomocí modifikátoru [Async](async.md) .  
- Metody iterátoru, které zahrnují [návratový návrat](yield.md) nebo `yield break` příkaz yield.

Kromě toho [rozšiřující metody](../../programming-guide/classes-and-structs/extension-methods.md) mají následující omezení:

- `out`Klíčové slovo nelze použít pro první argument metody rozšíření.
- `ref`Klíčové slovo nelze použít u prvního argumentu metody rozšíření, pokud argument není struct nebo obecný typ, který není omezen na strukturu.
- `in`Klíčové slovo nelze použít, pokud první argument není struktura. `in`Klíčové slovo nelze použít pro žádný obecný typ, ani v případě, že je omezení typu struct.

## <a name="passing-an-argument-by-reference-an-example"></a>Předání argumentu odkazem: příklad

Předchozí příklady přecházejí typu hodnoty odkazem. Můžete také použít `ref` klíčové slovo k předání typu odkazu odkazem. Předání typu odkazu odkazem umožňuje volané metodě nahradit objekt, na který odkazuje parametr reference v volajícím. Umístění úložiště objektu je předáno metodě jako hodnota referenčního parametru. Změníte-li hodnotu v umístění úložiště parametru (aby odkazovala na nový objekt), můžete také změnit umístění úložiště, do kterého se volající odkazuje. Následující příklad předává instanci typu odkazu jako `ref` parametr.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Další informace o tom, jak předat typy odkazů podle hodnoty a odkazu, naleznete v tématu [předávání parametrů typu odkazu](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Referenční návratové hodnoty

Návratové hodnoty odkazu (nebo ref vrátí) jsou hodnoty, které metoda vrátí odkazem na volajícího. To znamená, že volající může změnit hodnotu vrácenou metodou a tato změna se projeví ve stavu objektu v metodě volání.

Návratová hodnota odkazu je definována pomocí `ref` klíčového slova:

- V signatuře metody. Například následující signatura metody označuje, že `GetCurrentPrice` metoda vrací <xref:System.Decimal> hodnotu odkazem.

```csharp
public ref decimal GetCurrentPrice()
```

- Mezi `return` tokenem a proměnnou vrácenou v `return` příkazu v metodě. Příklad:

```csharp
return ref DecimalArray[0];
```

Aby mohl volající změnit stav objektu, návratová hodnota odkazu musí být uložena do proměnné, která je explicitně definována jako [místní referenční](#ref-locals)číslo.

Zde je příklad uceleného návratového příkladu, který zobrazuje jak podpis metody, tak tělo metody.

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Volaná metoda může také deklarovat návratovou hodnotu tak `ref readonly` , aby vracela hodnotu odkazem a vynutila, že volající kód nemůže změnit vrácenou hodnotu. Volající metoda se může vyhnout zkopírování vracené hodnoty tím, že uloží hodnotu v proměnné s [parametrem ReadOnly](#ref-readonly-locals) .

Příklad naleznete v části [ref Returns a lokální hodnoty REF](#a-ref-returns-and-ref-locals-example).

## <a name="ref-locals"></a>Lokální hodnoty REF

Lokální proměnná ref slouží k odkazování na hodnoty vrácené pomocí `return ref` . Lokální proměnnou ref nelze inicializovat pro návratovou hodnotu, která není ref. Jinými slovy, pravá strana inicializace musí být odkazem. Jakékoli úpravy hodnoty lokálního odkazu se projeví ve stavu objektu, jehož metoda vrátila hodnotu odkazem.

Místní odkaz definujete pomocí `ref` klíčového slova před deklaraci proměnné, stejně jako bezprostředně před voláním metody, která vrací hodnotu odkazem.

Například následující příkaz definuje místní hodnotu REF, která je vrácena metodou s názvem `GetEstimatedValue` :

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

K hodnotě můžete přistupovat stejným způsobem pomocí odkazu. V některých případech přístup k hodnotě pomocí odkazu zvyšuje výkon tím, že se vyhne potenciálně nákladné operaci kopírování. Například následující příkaz ukazuje, jak může jeden definovat místní hodnotu REF, která se používá k odkazování na hodnotu.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

V obou příkladech `ref` musí být klíčové slovo použito na obou místech, nebo kompilátor generuje chybu CS8172, "" nemůže inicializovat proměnnou podle odkazu s hodnotou. "

Počínaje jazykem C# 7,3 může být proměnná iterace `foreach` příkazu ref na místní proměnnou ref nebo ref jen pro čtení. Další informace naleznete v článku o [příkazu foreach](foreach-in.md) .

Počínaje jazykem C# 7,3 můžete znovu přiřadit místní proměnnou ref nebo ref jen pro čtení s [operátorem přiřazení ref](../operators/assignment-operator.md#ref-assignment-operator).

## <a name="ref-readonly-locals"></a>Místní referenční hodnoty jen pro čtení

Místní odkaz jen pro čtení se používá k odkazování na hodnoty vracené metodou nebo vlastností, která má `ref readonly` jeho signaturu a používá `return ref` . `ref readonly`Proměnná kombinuje vlastnosti `ref` místní proměnné s `readonly` proměnnou: Jedná se o alias úložiště, ke kterému je přiřazený, a nedá se změnit.

## <a name="a-ref-returns-and-ref-locals-example"></a>Příklad odkazů vrátí a místní hodnoty REF

Následující příklad definuje `Book` třídu, která má dvě <xref:System.String> pole `Title` a `Author` . Definuje také `BookCollection` třídu, která obsahuje soukromé pole `Book` objektů. Jednotlivé objekty knihy jsou vráceny odkazem voláním její `GetBookByTitle` metody.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Když volající ukládá hodnotu vrácenou `GetBookByTitle` metodou jako místní referenční číslo, změny, které volající provede na vrácenou hodnotu, se projeví v `BookCollection` objektu, jak ukazuje následující příklad.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Zapisovat bezpečný efektivní kód](../../write-safe-efficient-code.md)
- [Návratové hodnoty podle odkazu a lokální proměnné podle odkazu](../../programming-guide/classes-and-structs/ref-returns.md)
- [Podmíněný výraz ref](../operators/conditional-operator.md#conditional-ref-expression)
- [Předávání parametrů](../../programming-guide/classes-and-structs/passing-parameters.md)
- [Parametry metody](method-parameters.md)
- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
