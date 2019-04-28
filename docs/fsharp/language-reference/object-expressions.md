---
title: Objektové výrazy
description: Další informace o použití F# objektové výrazy, když chcete se vyhnout zvláštní kód a režijní náklady na potřebné k vytvoření nového, s názvem typu.
ms.date: 02/08/2019
ms.openlocfilehash: 63f2c1d7128721b7b8c744e4cf02d73c2a8b4a07
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666284"
---
# <a name="object-expressions"></a>Objektové výrazy

*Objektu výraz* je výraz, který vytvoří novou instanci typu dynamicky generovaný anonymní objekt, který je založen na existující základní typ, rozhraní nebo sady rozhraní.

## <a name="syntax"></a>Syntaxe

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *typename* představuje existující typu třídy nebo rozhraní. *parametry typu* obsahuje popis parametrů, volitelné obecného typu. *Argumenty* se používají pouze pro typy tříd, které vyžadují parametry konstruktoru. *Definice členů* přepsání metody základní třídy nebo implementace abstraktní metody ze základní třídy nebo rozhraní.

Následující příklad ukazuje několik různých typů objektové výrazy.

```fsharp
// This object expression specifies a System.Object but overrides the
// ToString method.
let obj1 = { new System.Object() with member x.ToString() = "F#" }
printfn "%A" obj1

// This object expression implements the IFormattable interface.
let delimiter(delim1: string, delim2: string, value: string) =
    { new System.IFormattable with
        member x.ToString(format: string, provider: System.IFormatProvider) =
            if format = "D" then
                delim1 + value + delim2
            else
                value }

let obj2 = delimiter("{","}", "Bananas!");

printfn "%A" (System.String.Format("{0:D}", obj2))

// Define two interfaces
type IFirst =
  abstract F : unit -> unit
  abstract G : unit -> unit

type ISecond =
  inherit IFirst
  abstract H : unit -> unit
  abstract J : unit -> unit

// This object expression implements both interfaces.
let implementer() =
    { new ISecond with
        member this.H() = ()
        member this.J() = ()
      interface IFirst with
        member this.F() = ()
        member this.G() = () }
```

## <a name="using-object-expressions"></a>Použitím objektových výrazů

Objektové výrazy používají, když chcete se vyhnout zvláštní kód a režijní náklady, který je potřeba vytvořit nový s názvem typu. Používáte-li minimalizovat počet typů, které jsou vytvořené v programu objektové výrazy, můžete snížit počet řádků kódu a zabránit zbytečným růst počtu typů. Místo vytváření mnoho typů pouze pro zpracování konkrétních situacích, můžete použít objektový výraz, který přizpůsobí existujícího typu nebo poskytuje ve vhodné implementaci rozhraní pro tento konkrétní případ po ruce.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
