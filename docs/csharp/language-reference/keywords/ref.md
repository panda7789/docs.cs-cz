---
title: ref – C# klíčové slovo Reference
ms.custom: seodec18
ms.date: 03/26/2019
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: f11137b3c13bb9e8670c4df25fedf3251724a088
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566895"
---
# <a name="ref-c-reference"></a>ref (Referenční dokumentace jazyka C#)

`ref` Klíčové slovo označuje hodnotu, která je předána odkazem. Používá se ve čtyřech různých kontextech:

- V signatuře metody a ve volání metody předejte argument metodě odkazem. Další informace naleznete v tématu [předání argumentu odkazem](#passing-an-argument-by-reference).
- V signatuře metody pro vrácení hodnoty volajícímu odkazem. Další informace najdete v tématu [referenční návratové hodnoty](#reference-return-values).
- V těle člena, aby označoval, že návratová hodnota odkazu je uložená místně jako odkaz, který volající chce změnit, nebo obecně místní proměnná přistupuje k jiné hodnotě odkazem. Další informace naleznete v tématu [místní hodnoty REF](#ref-locals).
- V deklaraci pro `ref struct` deklaraci nebo `readonly ref struct`. `struct` Další informace naleznete v tématu [typy referenční struktury](#ref-struct-types).

## <a name="passing-an-argument-by-reference"></a>Předání argumentu odkazem

Při použití v seznamu `ref` parametrů metody označuje klíčové slovo, že argument je předán odkazem, nikoli hodnotou. `ref` Klíčové slovo nastaví formální parametr jako alias pro argument, který musí být proměnná. Jinými slovy, každá operace s parametrem je provedena na argumentu. Například pokud volající předává výraz místní proměnné nebo výraz přístupu k elementu pole a volaná metoda nahradí objekt, na který odkazuje parametr ref, pak místní proměnná volajícího nebo prvek pole nyní odkazuje na nový objekt, když Metoda vrací.

> [!NOTE]
> Nepleťte si koncept předávání odkazem s konceptem typů odkazů. Tyto dvě koncepce nejsou stejné. Parametr metody lze změnit `ref` bez ohledu na to, zda se jedná o typ hodnoty nebo typ odkazu. Pokud je předána odkazem, není k dispozici žádný zabalení typu hodnoty.  

Chcete-li `ref` použít parametr, definice metody a volající metoda musí explicitně `ref` používat klíčové slovo, jak je znázorněno v následujícím příkladu.  

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Argument, který je předán `ref` parametru nebo `in` , musí být inicializován před předáním. To se liší od parametrů [out](out-parameter-modifier.md) , jejichž argumenty není nutné před předáním explicitně inicializovat.

Členové třídy nemohou mít signatury, které se liší pouze `ref`pomocí `in`, nebo `out`. K chybě kompilátoru dojde, pokud jediným rozdílem mezi dvěma členy typu je, že jeden z nich má `ref` parametr a druhý `out`má parametr, nebo `in` . Následující kód například není zkompilován.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Nicméně metody mohou být přetíženy v případě `ref`, že jedna metoda má parametr, `in`nebo `out` a druhá má parametr hodnoty, jak je znázorněno v následujícím příkladu.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 V jiných situacích, které vyžadují porovnávání signatur, jako je například skrytí nebo `in`přepsání `ref`,, `out` a jsou součástí podpisu a vzájemně se neshodují.  
  
 Vlastnosti nejsou proměnné. Jsou to metody a nelze je předat `ref` parametrům.  
  
 Klíčová slova `ref`, `in`a `out` nelze použít pro následující typy metod:  
  
- Asynchronní metody, které definujete pomocí modifikátoru [Async](async.md) .  
- Metody iterátoru, které zahrnují [návratový návrat](yield.md) nebo `yield break` příkaz yield.  

## <a name="passing-an-argument-by-reference-an-example"></a>Předání argumentu odkazem: Příklad

Předchozí příklady přecházejí typu hodnoty odkazem. Můžete také použít `ref` klíčové slovo k předání typu odkazu odkazem. Předání typu odkazu odkazem umožňuje volané metodě nahradit objekt, na který odkazuje parametr reference v volajícím. Umístění úložiště objektu je předáno metodě jako hodnota referenčního parametru. Změníte-li hodnotu v umístění úložiště parametru (aby odkazovala na nový objekt), můžete také změnit umístění úložiště, do kterého se volající odkazuje. Následující příklad předává instanci typu odkazu jako `ref` parametr.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Další informace o tom, jak předat typy odkazů podle hodnoty a odkazu, naleznete v tématu [předávání parametrů typu odkazu](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Referenční návratové hodnoty

Návratové hodnoty odkazu (nebo ref vrátí) jsou hodnoty, které metoda vrátí odkazem na volajícího. To znamená, že volající může změnit hodnotu vrácenou metodou a tato změna se projeví ve stavu objektu, který obsahuje metodu.

Návratová hodnota odkazu je definována pomocí `ref` klíčového slova:

- V signatuře metody. Například následující signatura metody označuje, že `GetCurrentPrice` metoda <xref:System.Decimal> vrací hodnotu odkazem.

```csharp
public ref decimal GetCurrentPrice()
```

- Mezi tokenem a proměnnou vrácenou `return` v příkazu v metodě. `return` Příklad:

```csharp
return ref DecimalArray[0];
```

Aby mohl volající změnit stav objektu, návratová hodnota odkazu musí být uložena do proměnné, která je explicitně definována jako [místní referenční](#ref-locals)číslo.

Volaná metoda může také deklarovat návratovou hodnotu `ref readonly` tak, aby vracela hodnotu odkazem a vynutila, že volající kód nemůže změnit vrácenou hodnotu. Volající metoda se může vyhnout zkopírování vracené hodnoty tím, že uloží hodnotu v proměnné s [parametrem ReadOnly](#ref-readonly-locals) .

Příklad naleznete v části [ref Returns a lokální hodnoty REF](#a-ref-returns-and-ref-locals-example).

## <a name="ref-locals"></a>Lokální hodnoty REF

Lokální proměnná ref slouží k odkazování na hodnoty vrácené pomocí `return ref`. Lokální proměnnou ref nelze inicializovat pro návratovou hodnotu, která není ref. Jinými slovy, pravé straně inicializace musí být odkaz. Jakékoli úpravy hodnoty lokálního odkazu se projeví ve stavu objektu, jehož metoda vrátila hodnotu odkazem.

Místní odkaz definujete pomocí `ref` klíčového slova před deklaraci proměnné, stejně jako bezprostředně před voláním metody, která vrací hodnotu odkazem.

Například následující příkaz definuje místní hodnotu REF, která je vrácena metodou s názvem `GetEstimatedValue`:

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

K hodnotě můžete přistupovat stejným způsobem pomocí odkazu. V některých případech přístup k hodnotě pomocí odkazu zvyšuje výkon tím, že se vyhne potenciálně nákladné operaci kopírování. Například následující příkaz ukazuje, jak může jeden definovat místní hodnotu REF, která se používá k odkazování na hodnotu.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Všimněte si, že v obou `ref` příkladech je klíčové slovo nutné použít na obou místech, nebo kompilátor generuje chybu CS8172, "" nemůže inicializovat proměnnou podle odkazu s hodnotou. "

Počínaje C# 7,3 se proměnná `foreach` iterace příkazu může jednat o místní proměnnou ref nebo ref jen pro čtení. Další informace naleznete v článku o [příkazu foreach](foreach-in.md) .

## <a name="ref-readonly-locals"></a>Místní referenční hodnoty jen pro čtení

Místní odkaz jen pro čtení se používá k odkazování na hodnoty vracené metodou nebo vlastností, `ref readonly` která má jeho signaturu `return ref`a používá. Proměnná kombinuje vlastnosti `ref` místní proměnné s `readonly` proměnnou: Jedná se o alias úložiště, ke kterému je přiřazený, a nedá se změnit. `ref readonly` 

## <a name="a-ref-returns-and-ref-locals-example"></a>Příklad odkazů vrátí a místní hodnoty REF

Následující příklad definuje `Book` třídu, která má dvě <xref:System.String> pole `Title` a `Author`. Definuje `BookCollection` také třídu, která obsahuje soukromé `Book` pole objektů. Jednotlivé objekty knihy jsou vráceny odkazem voláním její `GetBookByTitle` metody.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Když volající ukládá hodnotu vrácenou `GetBookByTitle` metodou jako místní referenční číslo, změny, které volající provede na vrácenou hodnotu, se projeví `BookCollection` v objektu, jak ukazuje následující příklad.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="ref-struct-types"></a>Typy referenční struktury

Přidání modifikátoru `struct` k deklaraci definuje, že instance daného typu musí být přiděleny zásobníku. `ref` Jinými slovy, instance těchto typů nelze nikdy vytvořit v haldě jako člen jiné třídy. Primární motivace pro tuto funkci byla <xref:System.Span%601> a související struktury.

Cílem zachování `ref struct` typu jako proměnné přidělené zásobníku je několik pravidel, která kompilátor vynutil pro všechny `ref struct` typy.

- Nemůžete pole `ref struct`a. Nelze přiřadit `ref struct` typ k proměnné typu `object`, `dynamic`nebo žádnému typu rozhraní.
- `ref struct`typy nemohou implementovat rozhraní.
- Nelze deklarovat `ref struct` jako člena pole třídy nebo normální struktury. To zahrnuje deklaraci automaticky implementované vlastnosti, která vytvoří pole pro zálohování generované kompilátorem. 
- Nelze deklarovat lokální proměnné, které jsou `ref struct` typy v asynchronních metodách. Můžete je deklarovat v synchronních metodách, <xref:System.Threading.Tasks.Task>které <xref:System.Threading.Tasks.Task%601> vracejí `Task`nebo jako typy.
- V iterátorech `ref struct` nelze deklarovat lokální proměnné.
- Nemůžete `ref struct` zachytit proměnné ve výrazech lambda nebo místních funkcích.

Tato omezení zajišťují, že nechtěně nepoužíváte `ref struct` způsobem, který by ho mohl zvýšit na spravovanou haldu.

Můžete kombinovat modifikátory a deklarovat strukturu jako `readonly ref`. Kombinuje výhody a `ref struct` omezení a `readonly struct` deklarace. `readonly ref struct`

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
