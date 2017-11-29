---
title: "Provádění stromů výrazů"
description: "Informace o provádění stromů výrazů jejich převedením na spustitelný soubor pokyny Intermediate Language (IL)."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 4ca87c8410a04e9198e9dd6c379760e7b6596585
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="executing-expression-trees"></a>Provádění stromů výrazů

[Předchozí – Typy Framework podpůrné stromů výrazů](expression-classes.md)

*Strom výrazu* je datová struktura, která představuje nějaký kód.
Není kompilované a spustitelného kódu. Pokud chcete provést kód .NET, která je reprezentována strom výrazu, je nutné je převést na spustitelný soubor IL pokyny. 
## <a name="lambda-expressions-to-functions"></a>Lambda – výrazy to – funkce
Můžete převést všechny LambdaExpression nebo kterýkoli typ odvozený od LambdaExpression do spustitelného souboru IL. Ostatní typy výrazů nelze převést přímo do kódu. Toto omezení se v praxi malý vliv. Lambda – výrazy jsou pouze typy výrazů, které byste chtěli spusťte tak, že převádění do převodního jazyka spustitelný soubor (IL). (Vezměte v úvahu, o co znamená přímo provést `ConstantExpression`. By to znamená nic užitečného?) Všechny strom výrazu, který je `LamdbaExpression`, nebo z odvozený typ. `LambdaExpression` lze převést na IL.
Typ výrazu `Expression<TDelegate>` se pouze konkrétní příklad v rozhraní .NET Core libraries. Slouží k reprezentaci výraz, který se mapuje na jakýkoli typ delegáta. Protože tento typ se mapuje na typ delegáta, rozhraní .NET můžete zkontrolujte výraz a generovat IL pro příslušné delegáta, který odpovídá podpis výrazu lambda. 

Ve většině případů tím se vytvoří jednoduchý mapování mezi výrazu a jeho odpovídající delegáta. Například strom výrazu, která je reprezentována `Expression<Func<int>>` bude převedena na delegáta typu `Func<int>`. Výraz lambda veškeré návratový typ a seznam argumentů existuje typ delegáta, který je typ cíle pro spustitelný kód reprezentována této lamdba výrazem.

`LamdbaExpression` Typ obsahuje `Compile` a `CompileToMethod` členy, které byste použili převést strom výrazu spustitelného kódu. `Compile` Metoda vytvoří delegáta. `ConmpileToMethod` Metoda aktualizace `MethodBuilder` objekt s IL představující kompilované výstup strom výrazu. Všimněte si, že `CompileToMethod` dostupný jen na úplné desktopového rozhraní, nikoli na rozhraní .NET Core.

Volitelně můžete zadat taky `DebugInfoGenerator` , se zobrazí symbol ladicí informace pro objekt generovaného delegáta. To umožňuje převést strom výrazu do objektu delegáta a mít úplné ladicí informace o generovaného delegáta.

Výraz by převod delegáta pomocí následujícího kódu:

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

Všimněte si, že typ delegáta je založen na typ výrazu. Pokud chcete použít objekt delegáta způsobem silného typu, je nutné znát návratový typ a seznam argumentů. `LambdaExpression.Compile()` Metoda vrátí `Delegate` typu. Budete muset převést na typ správné delegáta, který má mít žádné nástroje kompilaci zkontrolujte seznam argumentů návratový typ.

## <a name="execution-and-lifetimes"></a>Spuštění a životnosti

Spouštění kódu vyvoláním delegát vytvoří, když jste volali metodu `LamdbaExpression.Compile()`. Můžete to vidět výše kde `add.Compile()` vrátí delegáta. Vyvolání delegáta, voláním `func()` spustí kód.

Tento delegát představuje kód na strom výrazu. Můžete zachovat popisovač přidělíte a později ji použít. Nemusíte kompilovat pokaždé, když chcete spustit kód, který představuje strom výrazu. (Nezapomeňte, že jsou neměnné stromů výrazů a později kompilování stejném stromu pro výraz vytvoří delegáta, který provádí stejný kód.)

I bude upozornění proti pokusu o vytvoření všechny sofistikovanější ukládání do mezipaměti mechanismy pro zvýšení výkonu zabráněním nepotřebné kompilace volání. Porovnání dvou stromy libovolný výrazů k určení, zda představují stejnou algoritmus bude také časově náročné provést. Pravděpodobně zjistíte, dobu výpočtů uložit zabraňující jakékoli další volání `LambdaExpression.Compile()` více než využijí na době, provádění kód, který určuje ze dvou různých stromů výrazů mít za následek stejný spustitelný kód.

## <a name="caveats"></a>Upozornění

Kompilování výrazu lambda s delegátem a vyvolání tento delegát je jedním z nejjednodušší operace, které můžete provádět s strom výrazu se nezdařilo. Nicméně i přes tato jednoduchá operace existují upozornění, které musí mít přehled o. 

Lambda – výrazy vytvoří uzavření žádné místní proměnné, které jsou odkazované ve výrazu. Musí zaručit, že jsou všechny proměnné, které by byly součástí delegát použitelné tam, kde volání `Compile`, a po spuštění výsledného delegáta.

Obecně platí kompilátor zajistí, že se jedná o hodnotu true. Ale pokud výraz přistupuje k proměnné, která implementuje `IDisposable`, je možné, že kódu může dispose objektu, zatímco je stále držené strom výrazu.

Například tento kód funguje bez problémů, protože `int` neimplementuje `IDisposable`:

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

Delegát má zaznamenat odkaz na proměnnou místní `constant`.
Tuto proměnnou přistupuje kdykoli později, když funkce vrácený `CreateBoundFunc` provede.

Zvažte však tato třída (místo contrived), který implementuje `IDisposable`:

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

Pokud můžete použít ve výrazu, jak je uvedeno níže, získáte `ObjectDisposedException` při spuštění kód odkazuje `Resource.Argument` vlastnost:

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

Tato metoda vrátí delegáta zavřel přes `constant` objekt, který byl vyřazen. (Je byl zrušen, protože byla deklarována v `using` příkaz.) 

Teď, když spustíte delegáta, tato metoda vrátí, budete mít `ObjecctDisposedException` vyvolána v okamžiku spuštění.

Pravděpodobně tak, aby měl představující kompilaci konstrukce běhová chyba neobvyklé, ale který je na světě, které jsme zadat, když budeme pracovat s stromů výrazů.

Proto je obtížné nabízejí obecné pokyny k tomu zamezit je celá řada permutací tohoto problému. Buďte opatrní při definování výrazy přístup k místní proměnné a buďte opatrní o přístup ke stavu v aktuálním objektu (reprezentována `this`) při vytváření strom výrazu, který může být vrácen pouze veřejné rozhraní API.

Kód do výrazu odkazy na metody nebo vlastnosti v ostatních sestavení. Toto sestavení musí být dostupný, když je definována výraz a když je zkompilovat a při vyvolání Výsledný delegát. Budete splnit s `ReferencedAssemblyNotFoundException` v případech, kde není přítomen.

## <a name="summary"></a>Souhrn

Stromy výrazů, které představují výrazy lambda mohou být zkompilovány vytvořit delegáta, který můžete spustit. To představuje jeden mechanismus ke spouštění kódu vytvořeného reprezentována strom výrazu se nezdařilo.

Strom výrazu představují kód, který by provést pro jakékoli dané konstrukce, které vytvoříte. Tak dlouho, dokud prostředí, kde zkompilování a spuštění kód odpovídá prostředí, kde můžete vytvořit výraz, všechno funguje podle očekávání. Když, nedojde, chyby jsou velmi předvídatelný a jejich bude zachycena v první testy kódu pomocí stromů výrazů.

[Další – Interpretace výrazy](expression-trees-interpreting.md)
