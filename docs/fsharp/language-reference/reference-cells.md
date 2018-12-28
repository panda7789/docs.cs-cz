---
title: Referenční buňky
description: Zjistěte, jak F# odkazové buňky jsou úložná místa, které umožňují vytvořit proměnlivé hodnoty pomocí odkazové sémantiky.
ms.date: 05/16/2016
ms.openlocfilehash: e4fcd3cf1abcf5f5e3b4d5439c9215b79ff8dbcd
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612761"
---
# <a name="reference-cells"></a>Referenční buňky

*Odkazové buňky* jsou úložná místa, které umožňují vytvořit proměnlivé hodnoty pomocí odkazové sémantiky.

## <a name="syntax"></a>Syntaxe

```fsharp
ref expression
```

## <a name="remarks"></a>Poznámky

Můžete použít `ref` operátor před hodnotou, má-li vytvořit novou odkazovou buňku, která zapouzdřuje hodnotu. Zdrojovou hodnotu pak můžete změnit, protože je proměnlivá.

Odkazové buňky obsahují skutečnou hodnotu; není to pouze adresa. Při vytvoření odkazové buňky pomocí `ref` operátoru, vytvoření kopie zdrojové hodnoty ve formě zapouzdřené proměnlivé hodnoty.

Že přestoupíte odkazové buňky pomocí `!` – operátor (vykřičník).

Následující příklad kódu znázorňuje deklaraci a použití odkazových buněk.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

Výstup je `50`.

Odkazové buňky jsou instance `Ref` generického typu záznamu, který je deklarován následujícím způsobem.

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

Typ `'a ref` je synonymum pro `Ref<'a>`. Kompilátor a technologie IntelliSense v integrovaném vývojovém prostředí zobrazují nejprve tento typ a následně zdrojovou definici.

`ref` Operátor vytvoří novou odkazovou buňku. Následující kód je deklarace `ref` operátor.

```fsharp
let ref x = { contents = x }
```

V následující tabulce jsou uvedeny funkce, které jsou u odkazové buňky dostupné.

|Operátor, člen nebo pole|Popis|Typ|Definice|
|--------------------------|-----------|----|----------|
|`!` (operátor zrušení odkazu)|Vrátí zdrojovou hodnotu.|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=` (operátor přiřazení)|Změní zdrojovou hodnotu.|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref` (operátor)|Zapouzdří hodnotu do nové odkazové buňky.|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value` (vlastnost)|Získá nebo nastaví zdrojovou hodnotu.|`unit -> 'a`|`member x.Value = x.contents`|
|`contents` (pole záznamu)|Získá nebo nastaví zdrojovou hodnotu.|`'a`|`let ref x = { contents = x }`|

Ke zdrojové hodnotě lze získat přístup několika způsoby. Hodnota vrácená operátorem zrušení odkazu (`!`) není Přiřaditelná. Proto se při změně zdrojové hodnoty, musíte použít operátor přiřazení (`:=`) místo toho.

Oba `Value` vlastnost a `contents` pole jsou Přiřaditelné hodnoty. Můžete je proto použít ke zpřístupnění nebo změně zdrojové hodnoty, jak znázorňuje následující kód.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

Výstup je následující.

```
10
10
11
12
```

Pole `contents` zajišťuje kompatibilitu s jinými verzemi ML a během kompilace zobrazí upozornění. Chcete-li toto upozornění zakážete, použijte `--mlcompatibility` – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).

C#Programátoři by měl vědět, že `ref` v C# není totéž jako `ref` v F#. Ekvivalent konstrukce F# jsou [ByRef](byrefs.md), které jsou různé koncept z odkazové buňky.

Hodnoty označeny jako `mutable`může automaticky povýšen na `'a ref` nezachytává uzavření; naleznete v tématu [hodnoty](values/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Parametry a argumenty](parameters-and-arguments.md)
- [Referenční dokumentace symbolů a operátorů](symbol-and-operator-reference/index.md)
- [Hodnoty](values/index.md)
