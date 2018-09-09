---
title: Konstruktory (F#)
description: 'Zjistěte, jak definovat a používat konstruktory v jazyce F # k vytvoření a inicializaci objektů třídy a struktury.'
ms.date: 05/16/2016
ms.openlocfilehash: ff2463f890034cce0bbaa85d9a5c93e50427cd03
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227126"
---
# <a name="constructors"></a>Konstruktory

Toto téma popisuje, jak definovat a používat konstruktory vytváření a inicializace objektů třídy a struktury.

## <a name="construction-of-class-objects"></a>Vytváření objektů tříd

Objekty typů třídy mají konstruktory. Existují dva typy konstruktorů. Jeden je primární konstruktor, jehož parametry se zobrazí v závorkách hned za název typu. Zadejte jiné, volitelné další konstruktory s použitím `new` – klíčové slovo. Tyto další konstruktory musí volat primárnímu konstruktoru.

Primární konstruktor obsahuje `let` a `do` vazby, které se zobrazí na začátku definice třídy. A `let` vazba deklaruje privátním polím a metodám třídy; `do` vazby spustí kód. Další informace o `let` vazby v konstruktorech tříd naleznete v tématu [ `let` vazby ve třídách](let-bindings-in-classes.md). Další informace o `do` vazby v konstruktorech, naleznete v tématu [ `do` vazby ve třídách](do-bindings-in-classes.md).

Bez ohledu na to, jestli chcete volat konstruktor primárnímu konstruktoru nebo dodatečném konstruktoru, můžete vytvořit objekty pomocí `new` výrazu, s nebo bez něj nepovinný `new` – klíčové slovo. Inicializace objektů spolu s argumenty konstruktoru, buď uvedením argumentů v pořadí a oddělené čárkami a uzavřeny v závorkách, nebo pomocí pojmenovaných argumentů a hodnoty v závorkách. Můžete také nastavit vlastnosti pro objekt během konstrukce objektu pomocí názvů vlastností a přiřazuje hodnoty stejným způsobem, jako pojmenované argumenty konstruktoru.

Následující kód ukazuje třídu, která má konstruktor a různé způsoby vytváření objektů.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

Výstup je následující.

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a>Vytváření struktur

Struktury postupujte podle všech pravidel tříd. Proto může mít primárnímu konstruktoru, a můžete poskytnout další konstruktory pomocí `new`. Existuje ale jeden důležitý rozdíl mezi strukturami a třídami: struktury mohou mít výchozí konstruktor (to znamená, jeden bez argumentů) i v případě, že je definován žádný primární konstruktor. Výchozí konstruktor inicializuje všechna pole na výchozí hodnotu pro daný typ, obvykle nula nebo jeho ekvivalent. Žádné konstruktory, které definujete pro struktury musí mít aspoň jeden argument, aby se nepřekrývaly s výchozím konstruktorem.

Navíc struktury často obsahuje pole, která se vytvářejí pomocí `val` – klíčové slovo; třídy mohou také mít tato pole. Struktury a třídy, které mají pole definovaná pomocí `val` – klíčové slovo může být navíc inicializované v konstruktorech další s využitím výrazy záznamu, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Další informace najdete v tématu [explicitní pole: `val` – klíčové slovo](explicit-fields-the-val-keyword.md).

## <a name="executing-side-effects-in-constructors"></a>Provádění vedlejší účinky v konstruktorech

Primární konstruktoru ve třídě může spustit kód v `do` vazby. Ale co kdybyste měli ke spouštění kódu vytvořeného v dodatečném konstruktoru, aniž by `do` vazbu? K tomuto účelu můžete použít `then` – klíčové slovo.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Vedlejší účinky primárního konstruktoru stále spustit. Proto výstup vypadá takto.

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>Self – identifikátory v konstruktorech

V jiných členů zadejte název pro aktuální objekt v definici každého člena. Vlastní identifikátor lze také umístit na první řádek definice třídy pomocí `as` – klíčové slovo hned za parametry konstruktoru. Následující příklad ukazuje tuto syntaxi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

V další konstruktory, můžete také definovat vlastní identifikátor vložením `as` klauzule hned po parametry konstruktoru. Následující příklad ukazuje tuto syntaxi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Při pokusu o použití objektu předtím, než je plně definována, může dojít k problémům. Použití identifikátoru samotného proto může způsobit kompilátor vygeneruje upozornění a vložit další kontroly k zajištění, že členové objektu nejsou přístupná před objekt je inicializován. Vlastní identifikátor v byste měli používat jenom `do` vazby primárního konstruktoru, nebo po `then` – klíčové slovo v dalších konstruktory.

Název identifikátoru samotného nemusí být `this`. Může být libovolný platný identifikátor.

## <a name="assigning-values-to-properties-at-initialization"></a>Přiřazení hodnoty k vlastnostem při inicializaci

Můžete přiřadit hodnoty k vlastnostem objektu třídy v inicializační kód přidáním seznam přiřazení formuláře `property = value` na seznam argumentů pro konstruktor. To je ukázáno v následujícím příkladu kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Následující verze předchozího kódu ukazuje kombinace běžné argumenty, volitelné argumenty a nastavení vlastností ve volání jeden konstruktor.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a>Konstruktory ve zděděné třídě

Při dědění ze základní třídy, která má konstruktor, je nutné zadat argumenty v klauzuli zdědit. Další informace najdete v tématu [konstruktory a dědičnost](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Statické konstruktory nebo konstruktory typu

Kromě zadání kódu pro vytváření objektů, statické `let` a `do` se můžou vytvořit vazby ve typy tříd, které se provedou předtím, než typ poprvé použila k provedení inicializace na úrovni typu. Další informace najdete v tématu [ `let` vazby ve třídách](let-bindings-in-classes.md) a [ `do` vazby ve třídách](do-bindings-in-classes.md).

## <a name="see-also"></a>Viz také:

- [Členové](index.md)
