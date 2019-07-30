---
title: Konstruktory
description: Naučte se definovat a používat konstruktory v F# pro vytváření a inicializaci objektů tříd a struktur.
ms.date: 05/16/2016
ms.openlocfilehash: c25fdcb95c2873eb69a94f30c87735e5c04d391b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627592"
---
# <a name="constructors"></a>Konstruktory

Toto téma popisuje, jak definovat a používat konstruktory pro vytváření a inicializaci objektů tříd a struktur.

## <a name="construction-of-class-objects"></a>Konstrukce objektů třídy

Objekty typů třídy mají konstruktory. Existují dva druhy konstruktorů. Jedna je primární konstruktor, jehož parametry jsou uvedeny v závorkách hned za názvem typu. Pomocí `new` klíčového slova určíte jiné volitelné Další konstruktory. Jakékoli takové další konstruktory musí volat primární konstruktor.

Primární konstruktor obsahuje `let` a `do` vazby, které se zobrazí na začátku definice třídy. Vazba deklaruje soukromá pole a metody třídy `do` ; vazba spustí kód. `let` Další informace o `let` vazbách v konstruktorech třídy naleznete v tématu [ `let` Bindings in Classes](let-bindings-in-classes.md). Další informace o `do` vazbách v konstruktorech naleznete v tématu [ `do` Bindings in Classes](do-bindings-in-classes.md).

Bez ohledu na to, zda je konstruktor, který chcete volat, primární konstruktor nebo další konstruktor, lze objekty vytvořit pomocí `new` výrazu s volitelným `new` klíčovým slovem nebo bez něj. Vaše objekty můžete inicializovat společně s argumenty konstruktoru, buď výpisem argumentů v pořadí a oddělenými čárkami a uzavřeny v závorkách, nebo pomocí pojmenovaných argumentů a hodnot v závorkách. Můžete také nastavit vlastnosti objektu během konstrukce objektu pomocí názvů vlastností a přiřazením hodnot stejným způsobem jako argumenty pojmenovaných konstruktorů.

Následující kód ilustruje třídu, která má konstruktor a různé způsoby vytváření objektů.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

Výstup je následující.

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>Konstrukce struktur

Struktury dodržují všechna pravidla tříd. Proto můžete mít primární konstruktor a můžete poskytnout další konstruktory pomocí `new`. Nicméně existuje jeden důležitý rozdíl mezi strukturami a třídami: struktury mohou mít konstruktor bez parametrů (tj. jeden bez argumentů) i v případě, že není definován žádný primární konstruktor. Konstruktor bez parametrů inicializuje všechna pole na výchozí hodnotu pro tento typ, obvykle nula nebo ekvivalent. Všechny konstruktory, které definujete pro struktury, musí mít alespoň jeden argument, aby nedošlo ke konfliktu s výchozím konstruktorem.

Struktury také často obsahují pole, která jsou vytvořena pomocí `val` klíčového slova; třídy mohou také obsahovat tato pole. Struktury a třídy, které mají pole definovaná pomocí `val` klíčového slova, lze také inicializovat v dalších konstruktorech pomocí výrazů záznamu, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Další informace najdete v tématu [explicitní pole: `val` Klíčové slovo](explicit-fields-the-val-keyword.md).

## <a name="executing-side-effects-in-constructors"></a>Provádění vedlejších účinků v konstruktorech

Primární konstruktor ve třídě může spouštět kód ve `do` vazbě. Co když ale budete muset spustit kód v dalším konstruktoru bez `do` vazby? K tomu použijte `then` klíčové slovo.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Vedlejší účinky primárního konstruktoru se pořád spouštějí. Výstup je proto následující:

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>Osobní identifikátory v konstruktorech

V jiných členech zadáte název pro aktuální objekt v definici každého člena. Identifikátor sami můžete také umístit na první řádek definice třídy pomocí `as` klíčového slova hned za parametry konstruktoru. Následující příklad ilustruje tuto syntaxi.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

V dalších konstruktorech můžete také definovat identifikátor sami vložením `as` klauzule hned za parametry konstruktoru. Následující příklad ilustruje tuto syntaxi.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

K problémům může dojít při pokusu o použití objektu před jeho úplným definováním. Proto použití identifikátoru autoidentifier může způsobit, že kompilátor vygeneruje upozornění a vloží další kontroly, aby před inicializací objektu nebyly k dispozici členové objektu. V `do` vazbách primárního konstruktoru nebo `then` za klíčovým slovem v dalších konstruktorech byste měli použít pouze samotný identifikátor.

Název automatického identifikátoru nemusí být `this`. Může to být libovolný platný identifikátor.

## <a name="assigning-values-to-properties-at-initialization"></a>Přiřazení hodnot k vlastnostem při inicializaci

Můžete přiřadit hodnoty k vlastnostem objektu třídy v inicializačním kódu připojením seznamu přiřazení formuláře `property = value` k seznamu argumentů pro konstruktor. Toto je znázorněno v následujícím příkladu kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Následující verze předchozího kódu ilustruje kombinaci běžných argumentů, volitelných argumentů a nastavení vlastností v jednom volání konstruktoru.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a>Konstruktory v zděděné třídě

Při dědění ze základní třídy, která má konstruktor, je nutné zadat argumenty klauzule Inherit. Další informace naleznete v tématu [konstruktory a dědičnost](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Statické konstruktory nebo konstruktory typů

Kromě určení kódu pro vytváření objektů, statické `let` a `do` vazby lze vytvořit v typech třídy, které jsou spouštěny před prvním použitím tohoto typu k provedení inicializace na úrovni typu. Další informace naleznete v tématu [ `let` Bindings in Classes](let-bindings-in-classes.md) and [ `do` Bindings in Classes](do-bindings-in-classes.md).

## <a name="see-also"></a>Viz také:

- [Členové](index.md)
