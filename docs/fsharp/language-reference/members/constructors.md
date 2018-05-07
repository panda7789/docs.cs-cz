---
title: Konstruktory (F#)
description: 'Zjistěte, jak definovat a použít konstruktory v jazyce F # k vytvoření a inicializace třídy a struktury objektů.'
ms.date: 05/16/2016
ms.openlocfilehash: 1773c111e0398aa83951afe14979d8a4ebc4907f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="constructors"></a>Konstruktory

Toto téma popisuje, jak definovat a použít k vytvoření a inicializace objektů třídy a struktury konstruktory.


## <a name="construction-of-class-objects"></a>Konstrukce objektů – třída
Objekty třídy typů mít konstruktory. Existují dva druhy konstruktory. Jeden je primární konstruktoru, jejíž parametry se zobrazí v závorkách bezprostředně za název typu. Zadejte jiné, volitelné další konstruktory pomocí `new` – klíčové slovo. Tyto další konstruktory musí volat primární konstruktoru.

Obsahuje primární konstruktor `let` a `do` vazby, které se zobrazují na začátku definici třídy. A `let` vazba deklaruje privátním polím a metody třídy; `do` vazby spustí kód. Další informace o `let` vazby v konstruktorech třídy, najdete v části [ `let` vazby do ve třídách](let-bindings-in-classes.md). Další informace o `do` vazby v konstruktorech, najdete v části [ `do` vazby do ve třídách](do-bindings-in-classes.md).

Bez ohledu na to, jestli je konstruktor, který chcete použít primární konstruktor nebo další konstruktor, můžete vytvořit objekty pomocí `new` výraz s nebo bez volitelné `new` – klíčové slovo. Inicializace objektů vašeho společně s argumenty konstruktoru, buď tak, že uvedete argumenty v pořadí a oddělených čárkami a uzavřený v závorkách, nebo pomocí pojmenované argumenty a hodnoty v závorkách. Můžete také nastavit vlastnosti objektu během vytváření objektu pomocí názvů vlastností a přiřazení hodnoty, stejně jako použít s názvem argumenty konstruktoru.

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
Struktury podle všechna pravidla tříd. Proto může mít primární konstruktor a můžete poskytnout další konstruktory pomocí `new`. Nicméně je důležitý rozdíl mezi struktury a třídy: struktury může mít výchozí konstruktor (to znamená, jeden bez argumentů), i když je definovaný žádný primární konstruktor. Výchozí konstruktor inicializuje všechna pole na výchozí hodnotu pro tento typ, obvykle nula nebo jeho ekvivalent. Všechny konstruktory, které definujete pro struktury musí mít alespoň jeden argument, tak, aby nedošlo ke konfliktu s výchozí konstruktor.

Navíc struktury mají často pole, které jsou vytvořené pomocí `val` – klíčové slovo; třídy může mít tato pole. Struktury a třídy, které mají pole definovaná pomocí `val` – klíčové slovo může být navíc inicializované v konstruktorech další pomocí záznamu výrazy, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

Další informace najdete v tématu [explicitní pole: `val` – klíčové slovo](explicit-fields-the-val-keyword.md).


## <a name="executing-side-effects-in-constructors"></a>Provádění vedlejší účinky v konstruktorech
Primární konstruktor v třídě může spustit kód `do` vazby. Ale co když máte bez spuštění kódu v další konstruktoru, `do` vazbu? K tomuto účelu použijete `then` – klíčové slovo.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

Vedlejší efekty primární konstruktoru spustit. Proto výstup je následující.

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a>Self – identifikátory v konstruktorech
V další členy zadejte název pro aktuální objekt v definici u každého člena. Vlastní identifikátor můžete také umístit na první řádek definice třídy pomocí `as` – klíčové slovo okamžitě následující parametry konstruktor. Následující příklad ilustruje tuto syntaxi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

V další konstruktory, můžete také definovat vlastní identifikátor umístěním `as` klauzule hned po parametry konstruktor. Následující příklad ilustruje tuto syntaxi.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

Problémy může dojít, když se pokusíte použít objekt předtím, než je plně definována. Použití vlastní identifikátor proto může způsobit kompilátor posílat upozornění a další kontroly, aby se zajistilo, že členové objektu nejsou přístupné před inicializací objekt vložit. Vlastní identifikátor v byste měli používat jenom `do` vazby primární konstruktoru, nebo po `then` – klíčové slovo v další konstruktory.

Název vlastní identifikátor nemusí být `this`. Může být libovolný platný identifikátor.


## <a name="assigning-values-to-properties-at-initialization"></a>Přiřazení hodnoty k vlastnosti v inicializace
Můžete přiřadit hodnoty k vlastnosti objektu třídy v kódu inicializace připojením seznam přiřazení formuláře `property = value` na seznam argumentů pro konstruktor. To je znázorněno v následujícím příkladu kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

Následující verze předchozí kód ukazuje kombinace obyčejnou argumenty nepovinné argumenty a nastavení vlastností ve volání jednoho konstruktor.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]
    
## <a name="constructors-in-inherited-class"></a>Konstruktory v zděděné třídy
Když je zděděný z databáze třídu, která má konstruktor, je nutné zadat v klauzuli inherit její argumenty. Další informace najdete v tématu [konstruktory a dědičnost](../inheritance.md#constructors-and-inheritance).

## <a name="static-constructors-or-type-constructors"></a>Statické konstruktory nebo konstruktory typu
Kromě určení kód pro vytváření objektů, statické `let` a `do` vazby mohou být vytvořeny v typy tříd, které se spouští před typ poprvé použila k provedení inicializace na úrovni typu. Další informace najdete v tématu [ `let` vazby do ve třídách](let-bindings-in-classes.md) a [ `do` vazby do ve třídách](do-bindings-in-classes.md).

## <a name="see-also"></a>Viz také
[Členové](index.md)
