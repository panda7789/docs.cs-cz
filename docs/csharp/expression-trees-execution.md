---
title: Provádění stromů výrazů
description: Informace o provádění stromů výrazů jejich převedením do spustitelných pokynů pro středně dobíjecí jazyk (IL).
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 802a83f52f9c05a99c3f49f8f6511eff81ef3eaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146018"
---
# <a name="executing-expression-trees"></a>Provádění stromů výrazů

[Předchozí -- Typy architektury podporující stromy výrazů](expression-classes.md)

*Strom výrazů* je datová struktura, která představuje určitý kód.
Není kompilován a spustitelný kód. Pokud chcete spustit kód .NET, který je reprezentován stromem výrazů, musíte jej převést na spustitelné il instrukce.

## <a name="lambda-expressions-to-functions"></a>Lambda výrazy na funkce

Můžete převést libovolný LambdaExpression nebo libovolný typ odvozený z LambdaExpression do spustitelné IL. Jiné typy výrazů nelze přímo převést na kód. Toto omezení má v praxi jen malý účinek. Lambda výrazy jsou pouze typy výrazů, které byste chtěli spustit převodem na spustitelný zprostředkující jazyk (IL). (Přemýšlejte o tom, co `ConstantExpression`by to znamenalo přímo spustit . Znamenalo by to něco užitečného?) Libovolný strom výrazů, `LambdaExpression`který je , `LambdaExpression` nebo typ odvozený z lze převést na IL.
Typ `Expression<TDelegate>` výrazu je jediným konkrétním příkladem v knihovnách .NET Core. Používá se k reprezentaci výraz, který se mapuje na libovolný typ delegáta. Vzhledem k tomu, že tento typ mapuje na typ delegáta, .NET můžete zkontrolovat výraz a generovat IL pro příslušného delegáta, který odpovídá podpisu výrazu lambda.

Ve většině případů se tím vytvoří jednoduché mapování mezi výrazem a jeho odpovídajícím delegátem. Například strom výraz, který `Expression<Func<int>>` je reprezentován by být převedeny na delegáta typu `Func<int>`. Pro výraz lambda s libovolným návratovým typem a seznamem argumentů existuje typ delegáta, který je cílovým typem pro spustitelný kód reprezentovaný tímto výrazem lambda.

Typ `LambdaExpression` obsahuje `Compile` `CompileToMethod` a členy, které byste použili k převodu stromu výrazů na spustitelný kód. Metoda `Compile` vytvoří delegáta. Metoda `CompileToMethod` aktualizuje `MethodBuilder` objekt s IL, který představuje zkompilovaný výstup stromu výrazů. Všimněte `CompileToMethod` si, že je k dispozici pouze v rámci plochy, nikoli v .NET Core.

Volitelně můžete také poskytnout, `DebugInfoGenerator` který obdrží informace o ladění symbolu pro generovaný objekt delegáta. To umožňuje převést strom výrazů na objekt delegáta a mít úplné ladicí informace o generovaném delegátovi.

Výraz byste převedli na delegáta pomocí následujícího kódu:

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

Všimněte si, že typ delegáta je založen na typu výrazu. Pokud chcete objekt delegáta použít silným způsobem, musíte znát návratový typ a seznam argumentů. Metoda `LambdaExpression.Compile()` vrátí `Delegate` typ. Budete muset přetypovat na správný typ delegáta, aby všechny nástroje v době kompilace zkontrolovaly seznam argumentů nebo návratový typ.

## <a name="execution-and-lifetimes"></a>Provedení a životnost

Kód spustíte vyvoláním delegáta vytvořeného při `LambdaExpression.Compile()`volání . Můžete vidět výše, `add.Compile()` kde vrátí delegáta. Vyvolání tohoto delegáta voláním `func()` provede kód.

Tento delegát představuje kód ve stromu výrazů. Popisovač můžete zachovat na delegáta a vyvolat později. Není nutné zkompilovat strom výrazu pokaždé, když chcete spustit kód, který představuje. (Nezapomeňte, že stromy výrazů jsou neměnné a kompilace stejného stromu výrazů později vytvoří delegáta, který provede stejný kód.)

Varuji vás před pokusem o vytvoření sofistikovanějších mechanismů ukládání do mezipaměti pro zvýšení výkonu tím, že se vyhnete zbytečným voláním kompilace. Porovnání dvou libovolných stromů výrazů k určení, zda představují stejný algoritmus, bude také časově náročné spuštění. Pravděpodobně zjistíte, že výpočetní čas, který ušetříte, aby se zabránilo dalším voláním, `LambdaExpression.Compile()` bude více než spotřebován časem provádění kódu, který určuje dva různé stromy výrazů, což vede ke stejnému spustitelnému kódu.

## <a name="caveats"></a>Upozornění

Kompilace výrazu lambda delegátovi a vyvolání tohoto delegáta je jednou z nejjednodušších operací, které lze provést se stromem výrazů. Nicméně, i s touto jednoduchou operací, tam jsou upozornění, musíte být vědomi.

Lambda výrazy vytvořit uzavření přes všechny místní proměnné, které jsou odkazovány ve výrazu. Musíte zaručit, že všechny proměnné, které by byly součástí delegáta, `Compile`jsou použitelné v umístění, kde voláte , a při spuštění výsledného delegáta.

Obecně kompilátor zajistí, že je to pravda. Pokud však výraz přistupuje `IDisposable`k proměnné, která implementuje , je možné, že váš kód může nakládat s objektem, zatímco je stále držen stromem výrazů.

Například tento kód funguje `int` dobře, `IDisposable`protože neimplementuje :

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

Delegát zachytil odkaz na místní proměnnou `constant`.
Tato proměnná je přístupná kdykoli později, `CreateBoundFunc` když funkce vrácená provede.

Zvažte však tuto (spíše vykonstruovanou) třídu, která implementuje `IDisposable`:

```csharp
public class Resource : IDisposable
{
    private bool isDisposed = false;
    public int Argument
    {
        get
        {
            if (!isDisposed)
                return 5;
            else throw new ObjectDisposedException("Resource");
        }
    }

    public void Dispose()
    {
        isDisposed = true;
    }
}
```

Pokud jej použijete ve výrazu, jak je `ObjectDisposedException` znázorněno níže, získáte `Resource.Argument` při spuštění kódu, na který odkazuje vlastnost:

```csharp
private static Func<int, int> CreateBoundResource()
{
    using (var constant = new Resource()) // constant is captured by the expression tree
    {
        Expression<Func<int, int>> expression = (b) => constant.Argument + b;
        var rVal = expression.Compile();
        return rVal;
    }
}
```

Delegát vrácené z této metody `constant` byl uzavřen přes objekt, který byl vyřazen. (Byl vyřazen, protože byl deklarován v příkazu.) `using`

Nyní při spuštění delegáta vrácena z této metody, budete mít `ObjectDisposedException` vyvolána v místě spuštění.

Zdá se divné mít chybu za běhu představující konstrukci v době kompilace, ale to je svět, do kterého vstupujeme při práci se stromy výrazů.

Existuje mnoho permutací tohoto problému, takže je těžké nabídnout obecné pokyny, aby se mu zabránilo. Při definování výrazů buďte opatrní při přístupu k místním proměnným a buďte opatrní `this`při přístupu ke stavu v aktuálním objektu (reprezentovaném) při vytváření stromu výrazů, který může být vrácen veřejným rozhraním API.

Kód ve výrazu může odkazovat na metody nebo vlastnosti v jiných sestaveních. Toto sestavení musí být přístupné, když je definován výraz a když je kompilován a když je vyvolán výsledný delegát. Setkáte se s `ReferencedAssemblyNotFoundException` ním v případech, kdy není přítomen.

## <a name="summary"></a>Souhrn

Stromy výrazů, které představují výrazy lambda, mohou být zkompilovány a vytvořit delegáta, kterého můžete spustit. To poskytuje jeden mechanismus pro spuštění kódu reprezentovaného stromem výrazu.

Strom výrazů představuje kód, který by se spouštěl pro danou konstrukci, kterou vytvoříte. Tak dlouho, dokud prostředí, kde zkompilujete a spustíte kód odpovídá prostředí, kde vytvoříte výraz, vše funguje podle očekávání. Pokud k tomu nedojde, chyby jsou velmi předvídatelné a budou zachyceny v prvních testech libovolného kódu pomocí stromů výrazů.

[Další -- Interpretace výrazů](expression-trees-interpreting.md)
