---
title: Provádění stromů výrazů
description: Další informace o provádění stromů výrazů jejich převedením na spustitelný soubor pokynů Intermediate Language (IL).
ms.date: 06/20/2016
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: f6dca5a3965924e8eb6e1c04fe7ffc3c78c7df93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664555"
---
# <a name="executing-expression-trees"></a>Provádění stromů výrazů

[Předchozí – Typy architektur podporující stromy výrazů](expression-classes.md)

*Stromu výrazů* je datová struktura, která představuje nějaký kód.
Není zkompilovaných a spustitelný kód. Pokud chcete spustit kód v .NET, která je reprezentována strom výrazů, je nutné ji převést do spustitelného souboru instrukcí IL.

## <a name="lambda-expressions-to-functions"></a>Výrazy lambda na funkce

Můžete převést všechny LambdaExpression nebo libovolného typu odvozeného z LambdaExpression do spustitelného souboru IL. Jiné typy výrazů nelze převést přímo do kódu. Toto omezení má malý vliv v praxi. Výrazy lambda jsou pouze typy výrazů, které byste měli provést převedením na spustitelný soubor (IL intermediate language). (Představit, co to znamenalo přímé spuštění `ConstantExpression`. By to znamenat nic užitečného?) Žádné strom výrazu, který je `LambdaExpression`, nebo typ odvozený od `LambdaExpression` lze převést na IL.
Typ výrazu `Expression<TDelegate>` je pouze konkrétní příklad v .NET Core knihovny. Používá se k reprezentaci výrazu, který se mapuje na typ delegáta. Protože tento typ se mapuje na typ delegáta, .NET můžete prozkoumat výraz a generovat IL pro příslušné delegát, který odpovídá signatuře výrazu lambda. 

Ve většině případů tím se vytvoří jednoduchý mapování mezi výrazem a jeho odpovídající delegáta. Například strom výrazu, která je reprezentována `Expression<Func<int>>` bude převeden na delegáta typu `Func<int>`. Pro výraz lambda s jakékoli návratový typ a seznam argumentů existuje typ delegáta, který je cílový typ pro spustitelný kód reprezentována tento výraz lambda.

`LambdaExpression` Typ obsahuje `Compile` a `CompileToMethod` členy, které můžete použít k převedení strom výrazu na spustitelný kód. `Compile` Metoda vytvoří delegát. `CompileToMethod` Metodu aktualizace `MethodBuilder` objekt s IL, který představuje kompilovaném výstupu stromu výrazu. Všimněte si, že `CompileToMethod` dostupná jenom v rámci plně, ne na .NET Core.

Volitelně můžete zadat taky `DebugInfoGenerator` , který se zobrazí symbol ladicí informace pro objekt generované delegáta. To umožňuje převést na strom výrazu objektu delegáta a mít úplné ladicí informace o vygenerovaný delegáta.

Výraz by převést na delegáta, pomocí následujícího kódu:

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

Všimněte si, že typ delegáta je založen na typ výrazu. Pokud chcete používat objekt delegáta silného typu způsobem, musíte znát návratový typ a seznam argumentů. `LambdaExpression.Compile()` Vrátí metoda `Delegate` typu. Je nutné přetypovat na typ správného delegáta mít žádné nástroje kompilace zkontrolujte seznam argumentů nebo návratového typu.

## <a name="execution-and-lifetimes"></a>Spuštění a životnosti

Při spuštění kódu tak, že vyvolá delegáta vytvoří, když jste volali `LambdaExpression.Compile()`. Tohle je vidět výše where `add.Compile()` vrátí delegáta. Vyvolání tohoto delegáta voláním `func()` spustí kód.

Tento delegát představuje kód ve stromu výrazu. Můžete zachovat popisovač delegátu a později ho vyvolat. Není nutné ke kompilaci pokaždé, když chcete spustit kód, který představuje strom výrazu. (Mějte na paměti, že stromů výrazů jsou neměnné a později kompilaci stejném stromu pro výraz vytvoří delegát, který spouští stejný kód.)

Můžu se průkaz pokusu o vytvoření jakékoli sofistikovanější ukládání do mezipaměti mechanismy pro zvýšení výkonu zabráněním volání zbytečných kompilace. Porovnání dvou stromů výrazů libovolného k určení, zda představují stejný algoritmus bude taky časově náročné ke spuštění. Pravděpodobně zjistíte, že výpočetní čas uložíte vyhnout jakékoli další volání `LambdaExpression.Compile()` bude používat více než v době provádění kódu, který určuje dvě různé stromů výrazů za následek stejný spustitelný kód.

## <a name="caveats"></a>Upozornění

Probíhá kompilace výrazu lambda delegátovi a vyvolání tohoto delegáta je jedním z nejjednodušší operace, které můžete provádět pomocí strom výrazu. Ale i v této jednoduché operaci existují upozornění, které musí mít přehled o. 

Výrazy lambda vytvoření uzávěry přes místní proměnné, které se odkazuje ve výrazu. Je nutné zaručit, že jsou všechny proměnné, které by byly součástí delegáta použitelné na místě, kde volání `Compile`, a při spuštění Výsledný delegát.

Kompilátor bude obecně platí, ujistěte se, že je hodnota true. Nicméně pokud výraz přistupuje k proměnné, která implementuje `IDisposable`, je možné, že váš kód může uvolnění objektu, zatímco se stále nachází ve stromu výrazu.

Například tento kód funguje, protože `int` neimplementuje `IDisposable`:

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

Delegát má zachytit odkazem na místní proměnnou `constant`.
Tuto proměnnou přistupuje kdykoli později, pokud funkce vrátí `CreateBoundFunc` spustí.

Zvažte však, zda tato (místo toho contrived) třída, která implementuje `IDisposable`:

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

Pokud používáte ho ve výrazu, jak je znázorněno níže, získáte `ObjectDisposedException` při spuštění kód odkazuje `Resource.Argument` vlastnost:

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

Delegát, tato metoda vrátí byl uzavřen za `constant` objektu, který byl vyřazen. (Je byla vyřazena, protože byl deklarován v `using` příkazu.) 

Teď, když provedete delegáta, tato metoda vrátí, máte k dispozici `ObjectDisposedException` vyvolána v době vykonání.

Zdát neobvyklé obsahuje chybu modulu runtime představující konstrukci za kompilace, ale to je svět, ve kterém jsme zadejte při spolupracujeme s stromy výrazů.

Existuje velké množství permutací tento problém tak, aby byl těžko poskytují obecné pokyny, jak jí předcházet. Buďte opatrní při přístupu k místní proměnné při definování výrazy a buďte opatrní při přístupu k stavu v aktuálním objektu (představované `this`) při vytváření stromu výrazů, který může být vrácen veřejné rozhraní API.

Kód ve výrazu může odkazovat na metody nebo vlastnosti v jiných sestaveních. Toto sestavení musí být přístupné, když je definována výrazem a při kompilaci a kdy je výsledný delegát vyvolán. Budete splnit pomocí `ReferencedAssemblyNotFoundException` v případech, kdy není k dispozici.

## <a name="summary"></a>Souhrn

Stromy výrazů, které představují výrazy lambda mohou být zkompilovány k vytvoření delegáta, který můžete spustit. To poskytuje jeden mechanismus ke spouštění kódu vytvořeného reprezentována strom výrazu.

Strom výrazu představuje kód, který bude spuštěn pro jakékoli dané konstrukce, které vytvoříte. Za předpokladu, prostředí, ve kterém zkompilovat a spustit kód odpovídá prostředí, ve kterém vytvoříte výrazu, všechno funguje podle očekávání. Když, který nestane, chyby jsou velmi předvídatelné a, bude zachycena v první testy z jakéhokoli kódu pomocí stromů výrazů.

[Další--Interpretace výrazů](expression-trees-interpreting.md)
