---
title: Konstruktory
description: Naučte se definovat a používat konstruktory v F# pro vytváření a inicializaci objektů tříd a struktur.
ms.date: 05/16/2016
ms.openlocfilehash: 6769ec7fc6768090d8ae68e21946a58829b6eea0
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736852"
---
# <a name="constructors"></a>Konstruktory

Tento článek popisuje, jak definovat a používat konstruktory pro vytváření a inicializaci objektů tříd a struktur.

## <a name="construction-of-class-objects"></a>Konstrukce objektů třídy

Objekty typů třídy mají konstruktory. Existují dva druhy konstruktorů. Jedna je primární konstruktor, jehož parametry jsou uvedeny v závorkách hned za názvem typu. Pomocí klíčového slova `new` určíte jiné volitelné Další konstruktory. Jakékoli takové další konstruktory musí volat primární konstruktor.

Primární konstruktor obsahuje vazby `let` a `do`, které se zobrazí na začátku definice třídy. Vazba `let` deklaruje soukromá pole a metody třídy; vazba `do` spustí kód. Další informace o vazbách `let` v konstruktorech třídy naleznete v tématu [vazby `let` v třídách](let-bindings-in-classes.md). Další informace o vazbách `do` v konstruktorech naleznete v tématu [bindings `do` in Classes](do-bindings-in-classes.md).

Bez ohledu na to, zda je konstruktor, který chcete volat, primární konstruktor nebo další konstruktor, lze objekty vytvořit pomocí výrazu `new` s volitelným klíčovým slovem `new`, nebo bez něj. Vaše objekty můžete inicializovat společně s argumenty konstruktoru, buď výpisem argumentů v pořadí a oddělenými čárkami a uzavřeny v závorkách, nebo pomocí pojmenovaných argumentů a hodnot v závorkách. Můžete také nastavit vlastnosti objektu během konstrukce objektu pomocí názvů vlastností a přiřazením hodnot stejným způsobem jako argumenty pojmenovaných konstruktorů.

Následující kód ilustruje třídu, která má konstruktor a různé způsoby vytváření objektů:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

Výstup je následující:

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>Konstrukce struktur

Struktury dodržují všechna pravidla tříd. Proto můžete mít primární konstruktor a můžete poskytnout další konstruktory pomocí `new`. Nicméně existuje jeden důležitý rozdíl mezi strukturami a třídami: struktury mohou mít konstruktor bez parametrů (tj. jeden bez argumentů) i v případě, že není definován žádný primární konstruktor. Konstruktor bez parametrů inicializuje všechna pole na výchozí hodnotu pro tento typ, obvykle nula nebo ekvivalent. Všechny konstruktory, které definujete pro struktury, musí mít alespoň jeden argument, aby nedošlo ke konfliktu s konstruktory bez parametrů.

Struktury také často obsahují pole, která jsou vytvořena pomocí klíčového slova `val`; třídy mohou mít také tato pole. Struktury a třídy, které mají pole definovaná pomocí klíčového slova `val`, lze také inicializovat v dalších konstruktorech pomocí výrazů záznamů, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Další informace naleznete v tématu [explicitní pole: klíčové slovo `val`](explicit-fields-the-val-keyword.md).

## <a name="executing-side-effects-in-constructors"></a>Provádění vedlejších účinků v konstruktorech

Primární konstruktor ve třídě může spouštět kód v rámci vazby `do`. Co když ale budete muset spustit kód v dalším konstruktoru bez vazby `do`? K tomu použijte klíčové slovo `then`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Vedlejší účinky primárního konstruktoru se pořád spouštějí. Výstup je proto následující:

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>Osobní identifikátory v konstruktorech

V jiných členech zadáte název pro aktuální objekt v definici každého člena. Identifikátor sami můžete také umístit na první řádek definice třídy pomocí klíčového slova `as` hned po parametrech konstruktoru. Následující příklad ilustruje tuto syntaxi.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

V dalších konstruktorech můžete také definovat identifikátor držitele vložením klauzule `as` přímo za parametry konstruktoru. Následující příklad ilustruje tuto syntaxi:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

K problémům může dojít při pokusu o použití objektu před jeho úplným definováním. Proto použití identifikátoru autoidentifier může způsobit, že kompilátor vygeneruje upozornění a vloží další kontroly, aby před inicializací objektu nebyly k dispozici členové objektu. V vazbách `do` primárního konstruktoru nebo po klíčovém slově `then` v dalších konstruktorech byste měli použít pouze samotný identifikátor.

Název automatického identifikátoru nemusí být `this`. Může to být libovolný platný identifikátor.

## <a name="assigning-values-to-properties-at-initialization"></a>Přiřazení hodnot k vlastnostem při inicializaci

Můžete přiřadit hodnoty k vlastnostem objektu třídy v inicializačním kódu připojením seznamu přiřazení formuláře `property = value` do seznamu argumentů pro konstruktor. To je znázorněno v následujícím příkladu kódu:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Následující verze předchozího kódu ilustruje kombinaci běžných argumentů, volitelných argumentů a nastavení vlastností ve volání jednoho konstruktoru:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a>Konstruktory v zděděné třídě

Při dědění ze základní třídy, která má konstruktor, je nutné zadat argumenty klauzule Inherit. Další informace naleznete v tématu [konstruktory a dědičnost](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Statické konstruktory nebo konstruktory typů

Kromě určení kódu pro vytváření objektů, statické vazby `let` a `do` mohou být vytvořeny v typech třídy, které jsou spouštěny před prvním použitím tohoto typu k provedení inicializace na úrovni typu. Další informace naleznete v tématu [vazby `let` v třídách](let-bindings-in-classes.md) a [vazby `do` v třídách](do-bindings-in-classes.md).

## <a name="see-also"></a>Další informace najdete v tématech

- [Pedagog](index.md)
