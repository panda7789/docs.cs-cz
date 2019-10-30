---
title: Spouštění stromů výrazů
description: Přečtěte si informace o spouštění stromů výrazů jejich převodem na instrukce ke spustitelnému jazyku IL (executable Intermediate Language).
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 9af4b346962cb743daddf774e8b3c1f8fa722ae4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037117"
---
# <a name="executing-expression-trees"></a>Spouštění stromů výrazů

[Předchozí typy architektury podporující stromy výrazů](expression-classes.md)

*Strom výrazů* je datová struktura, která představuje nějaký kód.
Není zkompilován a spustitelný kód. Pokud chcete spustit kód .NET, který je reprezentován stromem výrazu, je nutné jej převést na spustitelné instrukce IL.

## <a name="lambda-expressions-to-functions"></a>Výrazy lambda pro funkce

Můžete převést libovolný LambdaExpression nebo jakýkoli typ odvozený z LambdaExpression do spustitelného IL. Jiné typy výrazů nelze přímo převést na kód. Toto omezení má malý účinek v praxi. Výrazy lambda jsou jediné typy výrazů, které byste chtěli provést převodem do spustitelného zprostředkujícího jazyka (IL). (Zamyslete se nad tím, co by to znamenalo k přímému spuštění `ConstantExpression`. To znamená cokoli užitečné?) Libovolný strom výrazů, který je `LambdaExpression`nebo typ odvozený od `LambdaExpression`, lze převést na IL.
Typ výrazu `Expression<TDelegate>` je jediný konkrétní příklad v knihovnách .NET Core. Slouží k reprezentaci výrazu, který se mapuje na libovolný typ delegáta. Vzhledem k tomu, že tento typ je namapován na typ delegáta, může rozhraní .NET prověřit výraz a vygenerovat IL pro příslušný delegáta, který odpovídá signatuře výrazu lambda. 

Ve většině případů to vytvoří jednoduché mapování mezi výrazem a jeho odpovídajícím delegátem. Například strom výrazu, který je reprezentován `Expression<Func<int>>`, by byl převeden na delegáta typu `Func<int>`. Pro výraz lambda s jakýmkoli návratovým typem a seznamem argumentů existuje typ delegáta, který je cílovým typem pro spustitelný kód reprezentovaný tímto výrazem lambda.

Typ `LambdaExpression` obsahuje členy `Compile` a `CompileToMethod`, které byste použili k převodu stromu výrazu na spustitelný kód. Metoda `Compile` vytvoří delegáta. Metoda `CompileToMethod` aktualizuje objekt `MethodBuilder` pomocí IL, který představuje zkompilovaný výstup stromu výrazu. Všimněte si, že `CompileToMethod` je k dispozici pouze v rozhraních kompletní plocha, nikoli v rozhraní .NET Core.

Volitelně můžete také zadat `DebugInfoGenerator`, které obdrží informace o ladění symbolů pro generovaný objekt delegáta. To umožňuje převést strom výrazu na objekt delegáta a získat úplné informace o ladění vygenerovaného delegáta.

Výraz byste převedli na delegáta pomocí následujícího kódu:

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

Všimněte si, že typ delegáta je založen na typu výrazu. Je nutné znát návratový typ a seznam argumentů, pokud chcete použít objekt delegáta ve silném typu. Metoda `LambdaExpression.Compile()` vrací typ `Delegate`. Budete je muset přetypovat na správný typ delegáta, aby se všechny nástroje v čase kompilace zkontrolovaly v seznamu argumentů nebo v návratovém typu.

## <a name="execution-and-lifetimes"></a>Spuštění a životnost

Spusťte kód vyvoláním delegáta vytvořeného při volání `LambdaExpression.Compile()`. Vidíte to výše, kde `add.Compile()` vrací delegáta. Volání tohoto delegáta voláním `func()` spustí kód.

Tento delegát představuje kód ve stromu výrazu. Můžete zachovat popisovač pro daného delegáta a vyvolat ho později. Strom výrazů není nutné kompilovat pokaždé, když chcete spustit kód, který představuje. (Nezapomeňte, že stromy výrazů jsou neměnné a kompilace stejného stromu výrazů později vytvoří delegáta, který spustí stejný kód.)

Při pokusu o vytvoření jakýchkoli propracovaných mechanismů pro ukládání do mezipaměti se mi bude snažit zvýšit výkon tím, že se vyhnete zbytečným voláním kompilace. Porovnání dvou libovolných stromů výrazů k určení, jestli představují stejný algoritmus, bude také časově náročné na provedení. Pravděpodobně zjistíte, že úsporný čas, který byste ušetřili, aby nedošlo k žádnému nadbytečnému volání `LambdaExpression.Compile()` bude více než spotřebované při provádění kódu, který určuje, že se dvě různé stromy výrazů vrátí do stejného spustitelného kódu.

## <a name="caveats"></a>Upozornění

Kompilování výrazu lambda do delegáta a vyvolání tohoto delegáta je jedním z nejjednodušších operací, které můžete provádět se stromem výrazů. I když je však tato jednoduchá operace k dispozici, je nutné mít na paměti informace o aspektech. 

Výrazy lambda vytvoří uzávěry pro všechny místní proměnné, na které se odkazuje ve výrazu. Musíte zaručit, aby všechny proměnné, které by byly součástí delegáta, byly použitelné v umístění, kde zavoláte `Compile`, a při spuštění výsledného delegáta.

Obecně kompilátor zajistí, že se jedná o true. Nicméně pokud váš výraz přistupuje k proměnné, která implementuje `IDisposable`, je možné, že váš kód může vyřadit objekt, když je stále ve stromu výrazu.

Tento kód například funguje správně, protože `int` neimplementuje `IDisposable`:

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
K této proměnné lze kdykoli později přejít, když se funkce vrátí `CreateBoundFunc` spustí.

Zvažte však tuto třídu (spíše contrived), která implementuje `IDisposable`:

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

Pokud ho použijete ve výrazu, jak je vidět níže, dostanete `ObjectDisposedException`, když spustíte kód, na který odkazuje vlastnost `Resource.Argument`:

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

Delegát vrácený touto metodou byl uzavřen nad objektem `constant`, který byl odstraněn. (Bylo zrušeno, protože bylo deklarováno v příkazu `using`.) 

Když nyní spustíte delegáta, který je vrácen z této metody, budete mít `ObjectDisposedException` vyvolána v okamžiku spuštění.

Zdá se, že došlo k chybě za běhu představující konstrukci v čase kompilace, ale to je World, který zadáte při práci s stromy výrazů.

Tento problém je hodně permutací, takže je těžké nabídnout obecné pokyny, abyste se k tomu předešli. Při vytváření stromu výrazů, který může být vrácen veřejným rozhraním API, buďte opatrní při přístupu k místním proměnným při definování výrazů a buďte opatrní při přístupu ke stavu v aktuálním objektu (reprezentovaný `this`).

Kód ve výrazu může odkazovat na metody nebo vlastnosti v jiných sestaveních. Toto sestavení musí být přístupné při definování výrazu a při jeho kompilaci a při vyvolání výsledného delegáta. V případech, kdy není k dispozici, se zobrazí `ReferencedAssemblyNotFoundException`.

## <a name="summary"></a>Souhrn

Stromy výrazů, které reprezentují výrazy lambda, mohou být zkompilovány k vytvoření delegáta, který lze spustit. To poskytuje jeden mechanismus pro spuštění kódu reprezentovaného stromem výrazu.

Strom výrazu představuje kód, který by byl proveden pro libovolnou vytvořenou konstrukci. Dokud prostředí, kde kompilujete a spouštíte kód, odpovídá prostředí, ve kterém vytvoříte výraz, vše funguje podle očekávání. Pokud k tomu nedojde, chyby jsou velmi předvídatelné a budou zachyceny v prvních testech libovolného kódu pomocí stromů výrazů.

[Další – interpretují se výrazy.](expression-trees-interpreting.md)
