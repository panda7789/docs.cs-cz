---
title: Vazby do ve třídách
description: Naučte se používat F# vazbu do definice třídy, která provádí akce při vytváření objektu nebo při prvním použití typu.
ms.date: 05/16/2016
ms.openlocfilehash: ced4f1bb17d9e23bf51cc79b5a275cc334cca013
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627591"
---
# <a name="do-bindings-in-classes"></a>Vazby do ve třídách

Vazba v definici třídy provádí akce, když je objekt vytvořen nebo, pro statickou `do` vazbu, při prvním použití typu. `do`

## <a name="syntax"></a>Syntaxe

```fsharp
[static] do expression
```

## <a name="remarks"></a>Poznámky

Vazba se zobrazí spolu s nebo po `let` vazbách, ale před definicemi členů v definici třídy. `do` I když je `do` `do` klíčové slovo volitelné pro vazby na úrovni modulu, není volitelné pro vazby v definici třídy. `do`

Pro konstrukci každého objektu daného typu, nestatické `do` vazby a nestatické `let` vazby jsou spouštěny v pořadí, ve kterém jsou uvedeny v definici třídy. V `do` jednom typu může být více vazeb. Nestatické `let` vazby a nestatické `do` vazby se stanou tělo primárního konstruktoru. Kód v oddílu nestatické `do` vazby může odkazovat na parametry primárního konstruktoru a všechny hodnoty nebo funkce, které jsou definovány `let` v části Bindings.

Nestatické `do` vazby mají přístup ke členům třídy, pokud má vlastní identifikátor, který je definován `as` klíčovým slovem v záhlaví třídy, a pokud všechny použití těchto členů jsou kvalifikovány pomocí identifikátoru vlastníku pro třídu.

Vzhledem `let` k tomu, že vazby inicializují soukromá pole třídy, což je často nutné k zajištění toho, aby se členové `do` chovali podle očekávání, `let` vazby jsou obvykle umístěny po vazbách tak, aby kód ve `do` vazbě mohl provede se plně inicializovaným objektem. Pokud se váš kód pokusí použít člena před dokončením inicializace, dojde k vyvolání InvalidOperationException.

Statické `do` vazby můžou odkazovat na statické členy nebo pole ohraničující třídy, ale ne členy instance nebo pole. Statické `do` vazby se stanou součástí statického inicializátoru pro třídu, která je zaručena k provedení před prvním použitím třídy.

Atributy jsou u `do` vazeb v typech ignorovány. Pokud je vyžadován atribut pro kód, který je spuštěn ve `do` vazbě, je nutné použít na primární konstruktor.

V následujícím kódu má třída statickou `do` vazbu a nestatickou `do` vazbu. Objekt má konstruktor, který má dva parametry `a` a `b`a dvě soukromá `let` pole jsou definována ve vazbách pro třídu. Jsou definované také dvě vlastnosti. Všechny tyto položky jsou v rozsahu v sekci nestatické `do` vazby, jak je znázorněno na řádku, který tiskne všechny tyto hodnoty.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

Výstup je následující.

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>Viz také:

- [Členové](index.md)
- [Třídy](../classes.md)
- [Konstruktory](constructors.md)
- [`let`Vazby ve třídách](let-bindings-in-classes.md)
- [`do`Vazeb](../functions/do-Bindings.md)
