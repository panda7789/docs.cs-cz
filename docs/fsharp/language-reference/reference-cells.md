---
title: Referenční buňky
description: Přečtěte F# si, jak jsou referenční buňky umístění úložiště, která umožňují vytvářet proměnlivé hodnoty pomocí referenční sémantiky.
ms.date: 05/16/2016
ms.openlocfilehash: 2bca7797b272c0e7d5bf54df07041dc08e33709a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216779"
---
# <a name="reference-cells"></a>Referenční buňky

*Odkazové buňky* jsou umístění úložiště, která umožňují vytvářet proměnlivé hodnoty pomocí referenční sémantiky.

## <a name="syntax"></a>Syntaxe

```fsharp
ref expression
```

## <a name="remarks"></a>Poznámky

`ref` Operátor použijete před hodnotou k vytvoření nové referenční buňky, která tuto hodnotu zapouzdří. Zdrojovou hodnotu pak můžete změnit, protože je proměnlivá.

Odkazové buňky obsahují skutečnou hodnotu; není to pouze adresa. Když vytvoříte odkazovou buňku pomocí `ref` operátoru, vytvoříte kopii základní hodnoty jako zapouzdřenou proměnlivou hodnotu.

Můžete odkázat na odkazovou buňku pomocí `!` operátoru (vykřičník).

Následující příklad kódu znázorňuje deklaraci a použití odkazových buněk.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

Výstup je `50`.

Odkazové buňky jsou instancemi `Ref` obecného typu záznamu, který je deklarován následujícím způsobem.

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

Typ `'a ref` je synonymum pro `Ref<'a>`. Kompilátor a technologie IntelliSense v integrovaném vývojovém prostředí zobrazují nejprve tento typ a následně zdrojovou definici.

`ref` Operátor vytvoří novou odkazovou buňku. Následující kód je deklarace `ref` operátoru.

```fsharp
let ref x = { contents = x }
```

V následující tabulce jsou uvedeny funkce, které jsou u odkazové buňky dostupné.

|Operátor, člen nebo pole|Popis|type|Definice|
|--------------------------|-----------|----|----------|
|`!`(operátor zpětného odkazování)|Vrátí zdrojovou hodnotu.|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=`(operátor přiřazení)|Změní zdrojovou hodnotu.|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref`podnikatel|Zapouzdří hodnotu do nové odkazové buňky.|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value`majetek|Získá nebo nastaví zdrojovou hodnotu.|`unit -> 'a`|`member x.Value = x.contents`|
|`contents`(pole záznamu)|Získá nebo nastaví zdrojovou hodnotu.|`'a`|`let ref x = { contents = x }`|

Ke zdrojové hodnotě lze získat přístup několika způsoby. Hodnota vrácená operátorem dereference (`!`) není hodnotou, kterou lze přiřadit. Proto pokud upravujete podkladovou hodnotu, je místo toho nutné použít operátor přiřazení (`:=`).

`Value` Obě vlastnosti`contents` i pole jsou přiřaditelné hodnoty. Můžete je proto použít ke zpřístupnění nebo změně zdrojové hodnoty, jak znázorňuje následující kód.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

Výstup je následující.

```console
10
10
11
12
```

Pole `contents` je k dispozici pro kompatibilitu s jinými verzemi ml a během kompilace vytvoří upozornění. Chcete-li zakázat upozornění, použijte `--mlcompatibility` možnost kompilátoru. Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).

C#Programátoři by měli znát `ref` , C# že v nástroji není totéž jako `ref` v F#nástroji. Ekvivalentní konstrukce v F# jsou [byrefs](byrefs.md), což jsou jiný koncept z referenčních buněk.

Hodnoty označené jako `mutable`mohou být automaticky povýšeny `'a ref` na hodnotu, je-li zachycena uzávěrkou; viz [hodnoty](./values/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Parametry a argumenty](parameters-and-arguments.md)
- [Referenční dokumentace symbolů a operátorů](./symbol-and-operator-reference/index.md)
- [Hodnoty](./values/index.md)
