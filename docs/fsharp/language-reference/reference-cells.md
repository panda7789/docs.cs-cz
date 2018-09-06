---
title: Referenční buňky (F#)
description: 'Zjistěte, jak F # odkazové buňky jsou úložná místa, které umožňují vytvořit proměnlivé hodnoty pomocí odkazové sémantiky.'
ms.date: 05/16/2016
ms.openlocfilehash: 133aec6b162a13306a05c9afa172f859890565eb
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892415"
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

Následující kód znázorňuje použití odkazových buněk při předávání parametrů. Typ Incrementor má metodu přírůstek, který přijímá parametr, který obsahuje v parametru typu byref. Byref v typu parametru označuje, že volající musejí předat odkazovou buňku nebo adresu typické proměnné zadaného typu, v tomto případu int. Zbývající kód znázorňuje, jak volat přírůstek s oběma těmito typy argumentů a ukazuje použití operátoru ref u proměnné vytvořit odkazovou buňku (ref myDelta1). Pak znázorňuje použití operátoru address-of (&amp;) ke generování příslušného argumentu. Nakonec metoda Increment volána znovu pomocí odkazové buňky, která je deklarována pomocí vazby let. Poslední řádek kódu ukazuje použití! operátor zrušení odkazu odkazové buňky pro tisk.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

Další informace o předávání pomocí odkazu naleznete v tématu [parametry a argumenty](parameters-and-arguments.md).

>[!NOTE]
Programátoři v C# měli vědět, že tento odkaz funguje jinak než v jazyce F # než v jazyce C#. Například použití ref při předávání argumentu nemá stejný účinek v jazyce F # stejně jako v jazyce C#.

>[!NOTE]
`mutable` proměnné mohou být automaticky povýšen na `'a ref` nezachytává uzavření; naleznete v tématu [hodnoty](values/index.md).

## <a name="consuming-c-ref-returns"></a>Přijímání C# `ref` vrátí

Od verze F # 4.1, můžete využívat `ref` vrátí vygenerované v jazyce C#.  Výsledek volání `byref<_>` ukazatele.

C# metodu:

```csharp
namespace RefReturns
{
    public static class RefClass
    {
        public static ref int Find(int val, int[] vals)
        {
            for (int i = 0; i < vals.Length; i++)
            {
                if (vals[i] == val)
                {
                    return ref numbers[i]; // Returns the location, not the value
                }
            }

            throw new IndexOutOfRangeException($"{nameof(number)} not found");
        }
    }
}
```

Je možné transparentně vyvolat v F # se žádná speciální syntax:

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

Můžete také deklarovat funkce, což může trvat `ref` vrátit jako vstup, například:

```fsharp
let f (x: byref<int>) = &x
```

Aktuálně neexistuje žádný způsob, jak vygenerovat `ref` vrácené v jazyce F #, která by mohla využívat v jazyce C#.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Parametry a argumenty](parameters-and-arguments.md)
- [Referenční dokumentace symbolů a operátorů](symbol-and-operator-reference/index.md)
- [Hodnoty](values/index.md)
