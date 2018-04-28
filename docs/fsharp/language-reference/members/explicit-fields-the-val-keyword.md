---
title: 'Explicitní pole: Klíčové slovo val (F#)'
description: "Další informace o F # 'val' – klíčové slovo, které se používá k deklaraci umístění pro uložení hodnotu v typu třídu nebo strukturu nebyl zadán typ."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: dc277680121976c0469b18c77bd84443cd251afb
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="explicit-fields-the-val-keyword"></a>Explicitní pole: Klíčové slovo val

`val` – Klíčové slovo se používá k deklaraci umístění pro uložení hodnotu v typu třídy nebo struktura bez jeho inicializaci. Umístění úložiště deklarovaný tímto způsobem se nazývají *explicitní pole*. Další používání `val` – klíčové slovo je ve spojení s `member` – klíčové slovo deklarovat ve automaticky implementované vlastnosti. Další informace o automaticky implementované vlastnosti najdete v tématu [vlastnosti](properties.md).


## <a name="syntax"></a>Syntaxe

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Poznámky
Obvyklým definování polí v typu třídu nebo strukturu, je použít `let` vazby. Ale `let` vazby musí být inicializován jako součást konstruktoru třídy, která není vždy možná, potřebná nebo žádoucí. Můžete použít `val` – klíčové slovo chcete pole, které není inicializován.

Explicitní pole můžou být statické nebo nestatické. *– Modifikátor přístupu* může být `public`, `private`, nebo `internal`. Ve výchozím nastavení jsou explicitní pole veřejné. Tím se liší od `let` vazby do ve třídách, které jsou vždy privátní.

[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) atribut je požadován u explicitní pole v typy tříd, které mají primární konstruktor. Tento atribut určuje, že pole je inicializováno na nulu. Typ pole musí podporovat inicializace nula. Typ podporuje inicializace nula. Pokud jde o jeden z následujících akcí:

- Primitivní typ, který má nulovou hodnotu.

- Typ, který podporuje hodnotu null, buď jako hodnotu Normální, jako neobvyklé hodnoty nebo jako reprezentace hodnoty. To zahrnuje třídy, řazené kolekce členů, záznamy, funkce, rozhraní, referenční typy .NET, `unit` typ a rozlišovaná sjednocení typů.

- Typ hodnoty .NET.

- Struktura, jejichž pole všechny podporují výchozí nulovou hodnotu.


Například neměnné pole s názvem `someField` má základní pole v .NET zkompilovat reprezentace s názvem `someField@`, a získat přístup k hodnotě uložené pomocí vlastnost s názvem `someField`.

Pro měnitelný pole je reprezentace .NET zkompilovat pole rozhraní .NET.


>[!WARNING] 
`Note` Obor názvů rozhraní .NET Framework `System.ComponentModel` obsahuje atribut, který má stejný název. Informace o tento atribut najdete v tématu `System.ComponentModel.DefaultValueAttribute`.


Následující kód ukazuje použití explicitní pole a pro porovnání, `let` vazby ve třídy, která má primární konstruktor. Všimněte si, že `let`-vázané pole `myInt1` je soukromé. Když `let`-vázané pole `myInt1` se odkazuje z metody člen, vlastní identifikátor `this` se nevyžaduje. Když odkazujete explicitní pole, ale `myInt2` a `myString`, je vyžadován vlastní identifikátor.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

Výstup vypadá takto:

```
11 12 abc
30 def
```

Následující kód ukazuje použití explicitní pole ve třídě, která neobsahuje primární konstruktor. V takovém případě `DefaultValue` atribut se nevyžaduje, ale v konstruktorech, které jsou definovány pro typ se musí inicializovat všechna pole.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

Výstupem je `35 22`.

Následující kód ukazuje použití explicitní pole ve struktuře. Vzhledem k tomu, že typ hodnoty strukturu se má automaticky výchozí konstruktor, která nastavuje hodnoty jeho polí na nulu. Proto `DefaultValue` atribut se nevyžaduje.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

Výstupem je `11 xyz`.

Explicitní pole nejsou určeny k použití rutiny. Obecně platí, pokud je to možné byste měli používat `let` vazby v třídě místo explicitní pole. Explicitní pole jsou užitečné v některých scénářích vzájemná funkční spolupráce, například když je třeba definovat strukturu, která bude použita v platformu vyvolání volání do nativního rozhraní API, nebo ve scénářích zprostředkovatele komunikace s objekty COM. Další informace najdete v tématu [externí funkce](../functions/external-functions.md). Další situace, ve kterém může být nezbytné explicitní pole je při práci s F # generátor kódu, který vysílá tříd bez objektů primární konstruktor. Explicitní pole jsou také užitečná pro přístup z více vláken statické proměnné a podobné konstrukce. Další informace naleznete v tématu `System.ThreadStaticAttribute`.

Když klíčová slova `member val` objeví spolu v definici typu je definice automaticky implementované vlastnosti. Další informace najdete v tématu [vlastnosti](properties.md).


## <a name="see-also"></a>Viz také
[Vlastnosti](properties.md)

[Členové](index.md)

[`let` Vazby do ve třídách](let-bindings-in-classes.md)
