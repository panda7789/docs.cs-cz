---
title: ref – C# klíčové slovo Reference
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 25c74317ce9033ef10735ee0087f275632b6bd17
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715189"
---
# <a name="ref-c-reference"></a>ref (Referenční dokumentace jazyka C#)

Klíčové slovo `ref` označuje hodnotu, která je předána odkazem. Používá se ve čtyřech různých kontextech:

- V signatuře metody a ve volání metody předejte argument metodě odkazem. Další informace naleznete v tématu [předání argumentu odkazem](#passing-an-argument-by-reference).
- V signatuře metody pro vrácení hodnoty volajícímu odkazem. Další informace najdete v tématu [referenční návratové hodnoty](#reference-return-values).
- V těle člena, aby označoval, že návratová hodnota odkazu je uložená místně jako odkaz, který volající chce změnit, nebo obecně místní proměnná přistupuje k jiné hodnotě odkazem. Další informace naleznete v tématu [místní hodnoty REF](#ref-locals).
- V deklaraci `struct` k deklaraci `ref struct` nebo `readonly ref struct`. Další informace naleznete v tématu [typy referenční struktury](#ref-struct-types).

## <a name="passing-an-argument-by-reference"></a>Předání argumentu odkazem

Při použití v seznamu parametrů metody označuje klíčové slovo `ref`, že argument je předán odkazem, nikoli hodnotou. Klíčové slovo `ref` provede formální parametr alias pro argument, který musí být proměnná. Jinými slovy, každá operace s parametrem je provedena na argumentu. Například pokud volající předává výraz místní proměnné nebo výraz přístupu k elementu pole a volaná metoda nahradí objekt, na který odkazuje parametr ref, pak místní proměnná volajícího nebo prvek pole nyní odkazuje na nový objekt, když Metoda vrací.

> [!NOTE]
> Nepleťte si koncept předávání odkazem s konceptem typů odkazů. Tyto dvě koncepce nejsou stejné. Parametr metody lze upravit pomocí `ref` bez ohledu na to, zda se jedná o typ hodnoty nebo typ odkazu. Pokud je předána odkazem, není k dispozici žádný zabalení typu hodnoty.  

Chcete-li použít parametr `ref`, musí definice metody a volající metoda explicitně používat klíčové slovo `ref`, jak je znázorněno v následujícím příkladu.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Argument předaný `ref` nebo parametr `in` musí být před předáním inicializován. To se liší od parametrů [out](out-parameter-modifier.md) , jejichž argumenty není nutné před předáním explicitně inicializovat.

Členové třídy nemohou mít signatury, které se liší pouze `ref`, `in`nebo `out`. K chybě kompilátoru dojde, pokud jediným rozdílem mezi dvěma členy typu je, že jeden z nich má parametr `ref` a druhý má `out`nebo parametr `in`. Následující kód například není zkompilován.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Nicméně metody mohou být přetíženy v případě, že jedna metoda má parametr `ref`, `in`nebo `out` a druhý má parametr hodnoty, jak je znázorněno v následujícím příkladu.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 V jiných situacích, které vyžadují shodu s podpisy, jako je například skrytí nebo přepsání, `in`, `ref`a `out` jsou součástí podpisu a vzájemně se neshodují.  
  
 Vlastnosti nejsou proměnné. Jsou to metody a nelze je předat `ref` parametrům.  
  
 Klíčová slova `ref`, `in`a `out` nelze použít pro následující typy metod:  
  
- Asynchronní metody, které definujete pomocí modifikátoru [Async](async.md) .  
- Metody iterátoru, které zahrnují příkaz [yield return](yield.md) nebo `yield break`.  

## <a name="passing-an-argument-by-reference-an-example"></a>Předání argumentu odkazem: příklad

Předchozí příklady přecházejí typu hodnoty odkazem. Můžete také použít klíčové slovo `ref` k předání typu odkazu odkazem. Předání typu odkazu odkazem umožňuje volané metodě nahradit objekt, na který odkazuje parametr reference v volajícím. Umístění úložiště objektu je předáno metodě jako hodnota referenčního parametru. Změníte-li hodnotu v umístění úložiště parametru (aby odkazovala na nový objekt), můžete také změnit umístění úložiště, do kterého se volající odkazuje. Následující příklad předává instanci typu odkazu jako parametr `ref`.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Další informace o tom, jak předat typy odkazů podle hodnoty a odkazu, naleznete v tématu [předávání parametrů typu odkazu](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Referenční návratové hodnoty

Návratové hodnoty odkazu (nebo ref vrátí) jsou hodnoty, které metoda vrátí odkazem na volajícího. To znamená, že volající může změnit hodnotu vrácenou metodou a tato změna se projeví ve stavu objektu, který obsahuje metodu.

Návratová hodnota odkazu je definována pomocí klíčového slova `ref`:

- V signatuře metody. Například následující signatura metody označuje, že metoda `GetCurrentPrice` vrací hodnotu <xref:System.Decimal> odkazem.

```csharp
public ref decimal GetCurrentPrice()
```

- Mezi tokenem `return` a proměnnou vrácenou v příkazu `return` v metodě. Příklad:

```csharp
return ref DecimalArray[0];
```

Aby mohl volající změnit stav objektu, návratová hodnota odkazu musí být uložena do proměnné, která je explicitně definována jako [místní referenční](#ref-locals)číslo.

Volaná metoda může také deklarovat návratovou hodnotu jako `ref readonly`, aby vrátila hodnotu odkazem a vynutila, že volající kód nemůže změnit vrácenou hodnotu. Volající metoda se může vyhnout zkopírování vracené hodnoty tím, že uloží hodnotu v proměnné s [parametrem ReadOnly](#ref-readonly-locals) .

Příklad naleznete v části [ref Returns a lokální hodnoty REF](#a-ref-returns-and-ref-locals-example).

## <a name="ref-locals"></a>Lokální hodnoty REF

Lokální proměnná ref slouží k odkazování na hodnoty vrácené pomocí `return ref`. Lokální proměnnou ref nelze inicializovat pro návratovou hodnotu, která není ref. Jinými slovy, pravé straně inicializace musí být odkaz. Jakékoli úpravy hodnoty lokálního odkazu se projeví ve stavu objektu, jehož metoda vrátila hodnotu odkazem.

Místní klíčová slova se definují pomocí klíčového slova `ref` před deklaraci proměnné, stejně jako bezprostředně před voláním metody, která vrací hodnotu odkazem.

Například následující příkaz definuje lokální hodnotu REF, která je vrácena metodou s názvem `GetEstimatedValue`:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

K hodnotě můžete přistupovat stejným způsobem pomocí odkazu. V některých případech přístup k hodnotě pomocí odkazu zvyšuje výkon tím, že se vyhne potenciálně nákladné operaci kopírování. Například následující příkaz ukazuje, jak může jeden definovat místní hodnotu REF, která se používá k odkazování na hodnotu.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Všimněte si, že v obou příkladech musí být klíčové slovo `ref` použito na obou místech, nebo kompilátor generuje chybu CS8172, "" nemůže inicializovat proměnnou podle odkazu s hodnotou. "

Počínaje C# 7,3 může být proměnná iterace příkazu `foreach` místní proměnnou ref nebo ref jen pro čtení. Další informace naleznete v článku o [příkazu foreach](foreach-in.md) .

## <a name="ref-readonly-locals"></a>Místní referenční hodnoty jen pro čtení

Místní odkaz jen pro čtení se používá k odkazování na hodnoty vrácené metodou nebo vlastností, která má `ref readonly` v jejím podpisu a používá `return ref`. Proměnná `ref readonly` kombinuje vlastnosti `ref` místní proměnné s proměnnou `readonly`: Jedná se o alias úložiště, ke kterému je přiřazený, a nedá se změnit. 

## <a name="a-ref-returns-and-ref-locals-example"></a>Příklad odkazů vrátí a místní hodnoty REF

Následující příklad definuje třídu `Book`, která má dvě pole <xref:System.String>, `Title` a `Author`. Definuje také třídu `BookCollection`, která obsahuje soukromé pole `Book` objektů. Jednotlivé objekty knihy jsou vráceny odkazem voláním jeho metody `GetBookByTitle`.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Když volající ukládá hodnotu vrácenou metodou `GetBookByTitle` jako místní referenční číslo, změny, které volající provede na vrácenou hodnotu, se projeví v objektu `BookCollection`, jak ukazuje následující příklad.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a>Typy referenční struktury

Přidání modifikátoru `ref` do deklarace `struct` definuje, že instance daného typu musí být přiděleny zásobníku. Jinými slovy, instance těchto typů nelze nikdy vytvořit v haldě jako člen jiné třídy. Primární motivace pro tuto funkci byla <xref:System.Span%601> a související struktury.

Cílem uchování `ref struct` typu jako proměnné přidělené zásobníkem zavádí několik pravidel, která kompilátor vynutil pro všechny typy `ref struct`.

- Nemůžete box `ref struct`. Typ `ref struct` nelze přiřadit proměnné typu `object`, `dynamic`ani libovolnému typu rozhraní.
- typy `ref struct` nemohou implementovat rozhraní.
- Nelze deklarovat `ref struct` jako člena pole třídy nebo normální struktury. To zahrnuje deklaraci automaticky implementované vlastnosti, která vytvoří pole pro zálohování generované kompilátorem. 
- Nelze deklarovat lokální proměnné, které jsou `ref struct` typy v asynchronních metodách. Můžete je deklarovat v synchronních metodách, které vracejí <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> nebo `Task`typy podobných.
- V iterátorech nelze deklarovat `ref struct` lokální proměnné.
- Ve výrazech lambda nebo místních funkcích nemůžete zachytit proměnné `ref struct`.

Tato omezení zajistí, že nechtěně nepoužíváte `ref struct` způsobem, který by ho mohl zvýšit na spravovanou haldu.

Můžete kombinovat modifikátory pro deklaraci struktury jako `readonly ref`. `readonly ref struct` kombinuje výhody a omezení deklarací `ref struct` a `readonly struct`.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zapisovat bezpečný efektivní kód](../../write-safe-efficient-code.md)
- [Návratové a místní referenční hodnoty](../../programming-guide/classes-and-structs/ref-returns.md)
- [Podmíněný výraz ref](../operators/conditional-operator.md#conditional-ref-expression)
- [operátor přiřazení ref](../operators/assignment-operator.md#ref-assignment-operator)
- [Předávání parametrů](../../programming-guide/classes-and-structs/passing-parameters.md)
- [Parametry metody](method-parameters.md)
- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
