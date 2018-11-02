---
title: Flexibilní typy (F#)
description: 'Další informace o použití F # anotaci typu flexibilní, což znamená, že parametr, proměnné nebo hodnota má typ, který je kompatibilní s zadaného typu.'
ms.date: 05/16/2016
ms.openlocfilehash: b6c97c3cc19f15b2c8db74b2c55660a16b2858f7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "47210042"
---
# <a name="flexible-types"></a>Flexibilní typy

A *anotace typu flexibilní* znamená, že parametr, proměnné nebo hodnota má typ, který je kompatibilní s zadaného typu, kde kompatibility se určuje podle umístění v hierarchii objektově orientované třídy nebo rozhraní. Flexibilní typy jsou užitečné zejména pokud nedojde k automatické převod na typy výše v hierarchii typu, ale přesto chtějí povolit vaší funkce pro práci s jakýkoli typ v hierarchii nebo libovolný typ, který implementuje rozhraní.

## <a name="syntax"></a>Syntaxe

```fsharp
#type
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *typ* představuje základní typ nebo rozhraní.

Flexibilní typ je ekvivalentní pro obecný typ, který má omezení, která omezuje povolených typů na typy, které jsou kompatibilní s typem základní typ nebo rozhraní. To znamená jsou následující dva řádky kódu ekvivalentní.

```fsharp
#SomeType

'T when 'T :> SomeType
```

Flexibilní typy jsou užitečné v několika typy situací označuje termín. Například pokud máte vyšší pořadí funkci (funkce, která přebírá jako argument funkce), často je užitečné mít návratový typ flexibilní funkce. V následujícím příkladu, použití flexibilní typu s argumentem pořadí v `iterate2` umožňuje vyšší pořadí funkce pro práci s funkcí, které generují pořadí, pole, seznamy a jakýkoli jiný typ výčtu.

Vezměte v úvahu následující dvě funkce, jednu, která vrátí sekvenci Druhý operand, který vrátí typ flexibilní.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

Další příklad, vezměte v úvahu [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) funkce knihovny:

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

Pro tuto funkci můžete projít žádnou z následující vyčíslitelné pořadí:

- Seznam seznamů
- Seznam polí
- Pole seznamů
- Pole sekvence
- Libovolnou kombinaci vyčíslitelné pořadí

Následující kód používá `Seq.concat` k předvedení scénáře, které můžete podporovat pomocí flexibilní typy.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

Výstup je následující.

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

V jazyce F # stejně jako v jiných jazycích objektově orientované existují kontextech, ve kterých odvozené typy nebo typy, které implementují rozhraní se automaticky převedou na základní typ nebo typ rozhraní. Tyto automatické převody nastanou argumenty s přímým přístupem, ale ne v případě, že typ je v podřízené pozice, jako součást více komplexní typ, jako je například návratovým typem funkce typ, nebo jako argument typu. Proto flexibilní typu notation je to užitečné hlavně Pokud aplikujete na požadovaný typ je součástí více komplexního typu.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Obecné typy](generics/index.md)
