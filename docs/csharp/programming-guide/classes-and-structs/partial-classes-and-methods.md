---
title: Částečné třídy a metody – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: ea8d95c41df236897761ace1062ec325a069d52b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714749"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>Částečné třídy a metody (Průvodce programováním v C#)

Je možné rozdělit definici [třídy](../../language-reference/keywords/class.md), [struktury](../../language-reference/keywords/struct.md), [rozhraní](../../language-reference/keywords/interface.md) nebo metody přes dva nebo více zdrojových souborů. Každý zdrojový soubor obsahuje oddíl definice typu nebo metody a všechny části jsou kombinovány při kompilaci aplikace.

## <a name="partial-classes"></a>Částečné třídy

Je žádoucí rozdělit definici třídy na několik situací:

- Při práci na rozsáhlých projektech umožňuje rozprostření třídy přes samostatné soubory současně pracovat s více programátory.

- Při práci s automaticky generovaným zdrojem lze kód přidat do třídy, aniž by bylo nutné znovu vytvořit zdrojový soubor. Visual Studio používá tento přístup při vytváření model Windows Forms, kódu obálky webové služby a tak dále. Můžete vytvořit kód, který používá tyto třídy, aniž byste museli upravovat soubor vytvořený v aplikaci Visual Studio.

- Chcete-li rozdělit definici třídy, použijte modifikátor klíčového slova [Partial](../../language-reference/keywords/partial-type.md) , jak je znázorněno zde:

  [!code-csharp[csProgGuideObjects#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#26)]

Klíčové slovo `partial` označuje, že v oboru názvů lze definovat jiné části třídy, struktury nebo rozhraní. Všechny části musí používat klíčové slovo `partial`. Všechny části musí být k dispozici v době kompilace, aby bylo možné vytvořit konečný typ. Všechny části musí mít stejnou přístupnost, například `public`, `private`a tak dále.

Je-li kterákoli část deklarována jako abstraktní, pak je celý typ považován za abstraktní. Je-li kterákoli část deklarována jako zapečetěná, je celý typ považován za zapečetěný. Pokud jakákoli část deklaruje základní typ, pak celý typ zdědí tuto třídu.

Všechny části, které určují základní třídu, musí souhlasit, ale části, které vynechávají základní třídu, stále zdědí základní typ. Části mohou určovat odlišná základní rozhraní a konečný typ implementuje všechna rozhraní uvedená všemi částečnými deklaracemi. Všechny členy třídy, struktury nebo rozhraní deklarované v částečné definici jsou k dispozici pro všechny ostatní části. Konečný typ je kombinace všech částí v době kompilace.

> [!NOTE]
> Modifikátor `partial` není k dispozici pro deklarace delegáta nebo výčtu.

Následující příklad ukazuje, že vnořené typy mohou být částečné, i když typ, který je vnořen do, není částečně sám.

[!code-csharp[csProgGuideObjects#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#25)]

V době kompilace jsou sloučeny atributy definicí částečného typu. Zvažte například následující deklarace:

[!code-csharp[csProgGuideObjects#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#23)]

Jsou ekvivalentem následujících deklarací:

[!code-csharp[csProgGuideObjects#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#24)]

Následující jsou sloučeny ze všech definicí částečného typu:

- XML – komentáře

- rozhraní

- atributy parametru obecného typu

- class – atributy

- členové

Zvažte například následující deklarace:

[!code-csharp[csProgGuideObjects#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#21)]

Jsou ekvivalentem následujících deklarací:

[!code-csharp[csProgGuideObjects#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#22)]

### <a name="restrictions"></a>Omezení

Při práci s definicemi částečné třídy je potřeba provést několik pravidel:

- Všechny definice částečného typu, které by měly být součástí stejného typu, musí být upraveny pomocí `partial`. Například následující deklarace tříd generují chybu:

  [!code-csharp[csProgGuideObjects#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#20)]

- Modifikátor `partial` se může objevit jenom bezprostředně před klíčovými slovy `class`, `struct`nebo `interface`.

- Vnořené částečné typy jsou povoleny v definicích částečného typu, jak je znázorněno v následujícím příkladu:

  [!code-csharp[csProgGuideObjects#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#19)]

- Všechny definice částečného typu, které by měly být součástí stejného typu, musí být definovány ve stejném sestavení a stejném modulu (soubor. exe nebo. dll). Částečné definice nemůžou zahrnovat víc modulů.

- Název třídy a parametry obecného typu se musí shodovat se všemi definicemi částečného typu. Obecné typy mohou být částečné. Každá částečná deklarace musí používat stejné názvy parametrů ve stejném pořadí.

- Následující klíčová slova v definici částečného typu jsou volitelná, ale pokud jsou k dispozici v rámci jedné definice částečného typu, nemůže být v konfliktu s klíčovými slovy zadanými v jiné částečné definici pro stejný typ:

  - [public](../../language-reference/keywords/public.md)

  - [private](../../language-reference/keywords/private.md)

  - [protected](../../language-reference/keywords/protected.md)

  - [internal](../../language-reference/keywords/internal.md)

  - [abstract](../../language-reference/keywords/abstract.md)

  - [sealed](../../language-reference/keywords/sealed.md)

  - base – třída

  - [Nový](../../language-reference/keywords/new-modifier.md) modifikátor (vnořené části)

  - obecná omezení

Další informace najdete v tématu [omezení parametrů typu](../generics/constraints-on-type-parameters.md).

## <a name="example-1"></a>Příklad 1

### <a name="description"></a>Popis

V následujícím příkladu jsou pole a konstruktor třídy, `Coords`deklarovány v rámci jedné definice částečné třídy a člen, `PrintCoords`, je deklarován v jiné definici částečné třídy.

### <a name="code"></a>Kód

[!code-csharp[csProgGuideObjects#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#17)]

## <a name="example-2"></a>Příklad 2

### <a name="description"></a>Popis

Následující příklad ukazuje, že můžete také vyvíjet částečné struktury a rozhraní.

### <a name="code"></a>Kód

[!code-csharp[csProgGuideObjects#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#18)]

## <a name="partial-methods"></a>Částečné metody

Částečná třída nebo struktura může obsahovat částečnou metodu. Jedna část třídy obsahuje signaturu metody. Volitelná implementace může být definována ve stejné části nebo jiné části. Pokud není implementována implementace, pak je metoda a všechna volání metody odebrána v době kompilace.

Částečné metody umožňují, aby implementátor jednoho dílu třídy definoval metodu, podobně jako událost. Implementátor druhé části třídy se může rozhodnout, zda má být metoda implementována. Pokud není metoda implementována, kompilátor odstraní signaturu metody a všechna volání metody. Volání metody, včetně všech výsledků, které by byly provedeny z vyhodnocení argumentů v volání, nemají za běhu žádný vliv. Proto jakýkoli kód v částečné třídě může volně použít částečnou metodu, i když není zadaná implementace. Pokud je metoda volána, ale není implementována, nebudou výsledkem žádné chyby při kompilaci nebo běhové chyby.

Částečné metody jsou obzvláště užitečné jako způsob přizpůsobení vygenerovaného kódu. Umožňují vyhradit název metody a signaturu, aby vygenerovaný kód mohl volat metodu, ale vývojář se může rozhodnout, zda metodu implementovat. Podobně jako u částečných tříd může částečná metoda povolit kód vytvořený generátorem kódu a kódem vytvořeným vývojářem pro lidskou spolupráci bez nákladů na spuštění.

Deklarace částečné metody se skládá ze dvou částí: definice a implementace. Ty mohou být v samostatných částech částečné třídy nebo ve stejné části. Pokud není k dispozici žádná deklarace implementace, kompilátor optimalizuje jak definiční deklaraci, tak všechna volání metody.

```csharp
// Definition in file1.cs
partial void onNameChanged();

// Implementation in file2.cs
partial void onNameChanged()
{
  // method body
}
```

- Deklarace částečné metody musí začínat [částečným](../../language-reference/keywords/partial-type.md) klíčovým slovem kontextové a metoda musí vracet [typ void](../../language-reference/keywords/void.md).

- Částečné metody mohou mít [v](../../language-reference/keywords/in-parameter-modifier.md) parametrech nebo [ref](../../language-reference/keywords/ref.md) , ale ne [výstupní](../../language-reference/keywords/out-parameter-modifier.md) parametry.

- Částečné metody jsou implicitně [soukromé](../../language-reference/keywords/private.md), a proto nemohou být [virtuální](../../language-reference/keywords/virtual.md).

- Částečné metody nemůžou být [extern](../../language-reference/keywords/extern.md), protože přítomnost těla určuje, jestli se definuje nebo implementuje.

- Částečné metody mohou mít [statické](../../language-reference/keywords/static.md) a [nebezpečné](../../language-reference/keywords/unsafe.md) modifikátory.

- Částečné metody mohou být obecné. Omezení jsou uvedena v deklaraci částečné deklarace metody a mohou být volitelně opakována při implementaci jednoho z nich. Parametry a názvy parametrů typu nemusí být stejné v implementaci deklarace jako v rámci definujícího.

- Můžete vytvořit [delegáta](../../language-reference/builtin-types/reference-types.md) částečné metody, která je definována a implementována, ale nikoli částečnou metodu, která byla definována pouze.

## <a name="c-language-specification"></a>C# – jazyková specifikace

Další informace naleznete v tématu [částečné typy](~/_csharplang/spec/classes.md#partial-types) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy](./classes.md)
- [Struktury](./structs.md)
- [Rozhraní](../interfaces/index.md)
- [partial (typ)](../../language-reference/keywords/partial-type.md)
