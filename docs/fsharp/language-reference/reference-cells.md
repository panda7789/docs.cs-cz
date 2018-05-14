---
title: Referenční buňky (F#)
description: 'Zjistěte, jak referenční buňky F # jsou umístění úložiště, které vám umožní vytvořit měnitelný hodnoty s sémantiku odkaz.'
ms.date: 05/16/2016
ms.openlocfilehash: 3a632425356a250f07e5babd2751b9923eec6552
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2018
---
# <a name="reference-cells"></a>Referenční buňky

*Referenční buňky* jsou umístění úložiště, které vám umožní vytvořit měnitelný hodnoty s sémantiku odkaz.

## <a name="syntax"></a>Syntaxe

```fsharp
ref expression
```

## <a name="remarks"></a>Poznámky
Můžete použít `ref` operátor před hodnotu k vytvoření nové buňky odkaz, který zapouzdřuje hodnotu. Zdrojovou hodnotu pak můžete změnit, protože je proměnlivá.

Odkazové buňky obsahují skutečnou hodnotu; není to pouze adresa. Když vytvoříte odkaz na buňku pomocí `ref` operátor, vytvořit kopii základní hodnoty jako zapouzdřené měnitelný hodnota.

Odkaz na buňku můžete dereference pomocí `!` operátor (vykřičník).

Následující příklad kódu znázorňuje deklaraci a použití odkazových buněk.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

Výstupem je `50`.

Referenční buňky jsou instancemi třídy `Ref` typ obecné záznamu, který je deklarován následujícím způsobem.

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

Typ `'a ref` se jedná o synonymum `Ref<'a>`. Kompilátor a technologie IntelliSense v integrovaném vývojovém prostředí zobrazují nejprve tento typ a následně zdrojovou definici.

`ref` Operátor vytvoří nový odkaz na buňku. Následující kód je deklaraci `ref` operátor.

```fsharp
let ref x = { contents = x }
```

V následující tabulce jsou uvedeny funkce, které jsou u odkazové buňky dostupné.

|Operátor, člen nebo pole|Popis|Typ|Definice|
|--------------------------|-----------|----|----------|
|`!` (operátoru zrušení)|Vrátí zdrojovou hodnotu.|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=` (operátor přiřazení)|Změní zdrojovou hodnotu.|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref` (operátor)|Zapouzdří hodnotu do nové odkazové buňky.|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value` (vlastnost)|Získá nebo nastaví zdrojovou hodnotu.|`unit -> 'a`|`member x.Value = x.contents`|
|`contents` (záznam pole)|Získá nebo nastaví zdrojovou hodnotu.|`'a`|`let ref x = { contents = x }`|
Ke zdrojové hodnotě lze získat přístup několika způsoby. Hodnota vrácená operátorem dereference (`!`) není přiřadit hodnotu. Proto pokud měníte základní hodnotu, musíte použít operátor přiřazení (`:=`) místo.

Obě `Value` vlastnost a `contents` pole jsou Přiřaditelné hodnoty. Můžete je proto použít ke zpřístupnění nebo změně zdrojové hodnoty, jak znázorňuje následující kód.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

Výstup je následující.

```
10
10
11
12
```

Pole `contents` zajišťuje kompatibilitu s jinými verzemi ML a vygeneruje upozornění během kompilace. Chcete-li zakázat upozornění, použijte `--mlcompatibility` – možnost kompilátoru. Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).

Následující kód znázorňuje použití odkazových buněk při předávání parametrů. Typ Incrementor má metoda přírůstek, která přebírá parametr, který obsahuje byref typ parametru. Byref v parametru typu označuje, že volající musí projít odkaz na buňku nebo adresu typické proměnné zadaného typu, v této případu int. Zbývající kód ukazuje, jak volat přírůstek s oběma typy argumentů a ukazuje použití operátoru ref na proměnnou, do které vytvořit odkaz na buňku (ref myDelta1). Potom ukazuje použití address-of – operátor (&amp;) ke generování odpovídající argument. Nakonec přírůstek je volání metody znovu pomocí odkaz na buňku, která je deklarovaná použití umožňují vazby. Poslední řádek kódu demonstruje použití! operátor pro dereference – odkaz na buňku pro tisk.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

Další informace o tom, jak předat odkazem najdete v tématu [parametry a argumenty](parameters-and-arguments.md).

>[!NOTE]
Programátory v jazyce C# měli vědět, že tento ref funguje jinak v jazyce F # než v jazyce C#. Například použití ref při předání argumentu nemá stejného efektu v jazyce F # stejně jako v jazyce C#.

>[!NOTE]
`mutable` proměnné mohou být automaticky povýšen na `'a ref` zachycenou uzavření; najdete v části [hodnoty](values/index.md).

## <a name="consuming-c-ref-returns"></a>Přijímání C# `ref` vrátí

Od verze 4.1 F #, můžete využívat `ref` vrátí vygenerované v jazyce C#.  Výsledkem volání je `byref<_>` ukazatel.

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

Je možné transparentně volat v F # se žádné speciální syntaxí:

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

Můžete také deklarovat funkce, které může trvat `ref` vrátit jako vstup, například:

```fsharp
let f (x: byref<int>) = &x
```

Aktuálně neexistuje žádný způsob, jak vygenerovat `ref` návratový v jazyce F # které by mohly spotřebovat v jazyce C#.

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Parametry a argumenty](parameters-and-arguments.md)

[Referenční dokumentace symbolů a operátorů](symbol-and-operator-reference/index.md)

[Hodnoty](values/index.md)
