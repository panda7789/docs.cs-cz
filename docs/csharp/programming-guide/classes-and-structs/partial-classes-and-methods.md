---
title: Částečné třídy a metody – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: 50b192d5a7416a982f41d0c3ac13e9c1bfe3397c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399817"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>Částečné třídy a metody (Průvodce programováním v C#)

Je možné rozdělit definici [třídy](../../language-reference/keywords/class.md), [struktury](../../language-reference/builtin-types/struct.md), [rozhraní](../../language-reference/keywords/interface.md) nebo metody na dva nebo více zdrojových souborů. Každý zdrojový soubor obsahuje část definice typu nebo metody a všechny části jsou kombinovány při kompilaci aplikace.

## <a name="partial-classes"></a>Částečné třídy

Existuje několik situací, kdy je žádoucí rozdělení definice třídy:

- Při práci na velkých projektech umožňuje rozprostření třídy přes samostatné soubory více programátorům pracovat na ní současně.

- Při práci s automaticky generovaným zdrojem lze kód přidat do třídy bez nutnosti znovu vytvořit zdrojový soubor. Visual Studio používá tento přístup při vytváření formulářů Windows, obálkový kód webové služby a tak dále. Můžete vytvořit kód, který používá tyto třídy bez nutnosti upravovat soubor vytvořený visual studio.

- Chcete-li rozdělit definici třídy, použijte modifikátor [částečného](../../language-reference/keywords/partial-type.md) klíčového slova, jak je znázorněno zde:

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

Klíčové `partial` slovo označuje, že ostatní části třídy, struktury nebo rozhraní mohou být definovány v oboru názvů. Všechny části musí `partial` používat klíčové slovo. Všechny části musí být k dispozici v době kompilace tvořit konečný typ. Všechny součásti musí mít stejnou `public`přístupnost, například , `private`, a tak dále.

Pokud je kterákoli část deklarována jako abstraktní, je celý typ považován za abstraktní. Pokud je některá část prohlášena za uzavřenou, považuje se celý typ za zapečetěný. Pokud některá část deklaruje základní typ, pak celý typ dědí tuto třídu.

Všechny části, které určují základní třídu, musí souhlasit, ale části, které vynechou základní třídu, stále dědí základní typ. Části můžete určit různé základní rozhraní a konečný typ implementuje všechna rozhraní uvedená ve všech částečných deklaracích. Všechny členy třídy, struktury nebo rozhraní deklarované v částečné definici jsou k dispozici pro všechny ostatní části. Konečný typ je kombinací všech částí v době kompilace.

> [!NOTE]
> Modifikátor `partial` není k dispozici v deklaracích delegáta nebo výčtu.

Následující příklad ukazuje, že vnořené typy mohou být částečné, i když typ, ve které jsou vnořené, není částečný sám.

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

V době kompilace jsou sloučeny atributy definice částečného typu. Zvažte například následující prohlášení:

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

Jsou rovnocenné následujícím prohlášením:

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

Následující jsou sloučeny ze všech definic částečného typu:

- XML – komentáře

- rozhraní

- atributy parametrů obecného typu

- class – atributy

- členy

Zvažte například následující prohlášení:

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

Jsou rovnocenné následujícím prohlášením:

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a>Omezení

Při práci s částečnými definicemi tříd je třeba dodržovat několik pravidel:

- Všechny definice částečného typu, které mají být součástí `partial`stejného typu, musí být změněny pomocí . Například následující deklarace třídy generují chybu:

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- `partial` Modifikátor se může objevit `class`pouze `struct`bezprostředně `interface`před klíčovými slovy , nebo .

- Vnořené částečné typy jsou povoleny v definicích částečného typu, jak je znázorněno v následujícím příkladu:

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- Všechny definice částečného typu, které mají být součástí stejného typu, musí být definovány ve stejném sestavení a ve stejném modulu (soubor .exe nebo .dll). Částečné definice nemohou mít více modulů.

- Název třídy a parametry obecného typu musí odpovídat všem definicím částečného typu. Obecné typy mohou být částečné. Každá částečná deklarace musí používat stejné názvy parametrů ve stejném pořadí.

- Následující klíčová slova v definici částečného typu jsou nepovinná, ale pokud jsou k dispozici v jedné definici částečného typu, nemohou být v konfliktu s klíčovými slovy zadanými v jiné částečné definici pro stejný typ:

  - [Veřejné](../../language-reference/keywords/public.md)

  - [Soukromé](../../language-reference/keywords/private.md)

  - [protected](../../language-reference/keywords/protected.md)

  - [Vnitřní](../../language-reference/keywords/internal.md)

  - [Abstraktní](../../language-reference/keywords/abstract.md)

  - [sealed](../../language-reference/keywords/sealed.md)

  - base – třída

  - [nový](../../language-reference/keywords/new-modifier.md) modifikátor (vnořené části)

  - obecná omezení

Další informace naleznete [v tématu Omezení parametrů typu](../generics/constraints-on-type-parameters.md).

## <a name="example-1"></a>Příklad 1

### <a name="description"></a>Popis

V následujícím příkladu jsou pole a konstruktor `Coords`třídy , deklarovány v `PrintCoords`jedné definici částečné třídy a člen , je deklarován v jiné definici částečné třídy.

### <a name="code"></a>kód

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a>Příklad 2

### <a name="description"></a>Popis

Následující příklad ukazuje, že můžete také vyvinout částečné struktury a rozhraní.

### <a name="code"></a>kód

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a>Částečné metody

Částečná třída nebo struktura může obsahovat částečnou metodu. Jedna část třídy obsahuje podpis metody. Volitelná implementace může být definována ve stejné nebo jiné části. Pokud implementace není zadána, pak metoda a všechna volání metody jsou odebrány v době kompilace.

Částečné metody umožňují implementátoru jedné části třídy definovat metodu, podobně jako událost. Implementátor druhé části třídy se může rozhodnout, zda metodu implementovat či nikoli. Pokud metoda není implementována, pak kompilátor odebere podpis metody a všechna volání metody. Volání metody, včetně všech výsledků, které by nastaly z vyhodnocení argumentů v volání, nemají žádný vliv v době běhu. Proto jakýkoli kód v částečné třídě můžete volně používat částečnou metodu, i v případě, že implementace není zadána. Žádné chyby kompilace nebo za běhu dojde, pokud je metoda volána, ale není implementována.

Částečné metody jsou užitečné zejména jako způsob přizpůsobení generovaného kódu. Umožňují název metody a podpis, které mají být vyhrazeny, tak, aby generovaný kód může volat metodu, ale vývojář se může rozhodnout, zda implementovat metodu. Podobně jako částečné třídy, částečné metody umožňují kód vytvořený generátorem kódu a kód vytvořený lidským vývojářem pro spolupráci bez nákladů za běhu.

Deklarace částečné metody se skládá ze dvou částí: definice a implementace. Ty mohou být v samostatných částech částečné třídy nebo ve stejné části. Pokud neexistuje žádná deklarace implementace, pak kompilátor optimalizuje pryč definování deklarace a všechna volání metody.

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- Deklarace částečné metody musí začínat kontextovým klíčovým slovem [partial](../../language-reference/keywords/partial-type.md) a metoda musí vrátit [void](../../language-reference/builtin-types/void.md).

- Částečné metody mohou mít [v](../../language-reference/keywords/in-parameter-modifier.md) nebo [ref,](../../language-reference/keywords/ref.md) ale ne [out](../../language-reference/keywords/out-parameter-modifier.md) parametry.

- Částečné metody jsou implicitně [soukromé](../../language-reference/keywords/private.md), a proto nemohou být [virtuální](../../language-reference/keywords/virtual.md).

- Částečné metody nemohou být [extern](../../language-reference/keywords/extern.md), protože přítomnost těla určuje, zda jsou definování nebo provádění.

- Částečné metody mohou mít [statické](../../language-reference/keywords/static.md) a [nebezpečné](../../language-reference/keywords/unsafe.md) modifikátory.

- Částečné metody mohou být obecné. Omezení jsou umístěny na definování deklarace částečné metody a může být volitelně opakovat na prováděcí jeden. Názvy parametrů a parametrů typu nemusí být v prováděcí deklaraci stejné jako v definujícím prohlášení.

- Můžete vytvořit [delegáta](../../language-reference/builtin-types/reference-types.md) na částečnou metodu, která byla definována a implementována, ale ne na částečnou metodu, která byla definována pouze.

## <a name="c-language-specification"></a>Specifikace jazyka C#

Další informace naleznete v tématu [Partial types](~/_csharplang/spec/classes.md#partial-types) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy](./classes.md)
- [Typy struktur](../../language-reference/builtin-types/struct.md)
- [Rozhraní](../interfaces/index.md)
- [partial (typ)](../../language-reference/keywords/partial-type.md)
