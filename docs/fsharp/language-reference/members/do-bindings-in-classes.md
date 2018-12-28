---
title: Vazby do ve třídách
description: Další informace o použití F# provést vazbu v definici třídy, které provádí akce, když je objekt vytvořen nebo při prvním použití typu.
ms.date: 05/16/2016
ms.openlocfilehash: 0ddf2b5ca458d0950c2e07bf2c37c205877e2173
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613112"
---
# <a name="do-bindings-in-classes"></a>Vazby do ve třídách

A `do` vazby v definici třídy provede akce při vytvoření objektu nebo pro statickou `do` vazby, když typ je nejprve použít.

## <a name="syntax"></a>Syntaxe

```fsharp
[static] do expression
```

## <a name="remarks"></a>Poznámky

A `do` vazby se zobrazí spolu s nebo po `let` vazby, ale před definice členů v definici třídy. I když `do` – klíčové slovo je nepovinné pro `do` vazby na úrovni modulu není pro volitelné `do` vazby v definici třídy.

Pro tvorbu žádné každý objekt daného typu, nestatické `do` vazby a informace o nestatická `let` vazby jsou provedeny v pořadí, v jakém jsou uvedeny v definici třídy. Více `do` vazby může dojít v jednom typu. Nestatické `let` vazby a nestatické `do` vazby stát tělo primárnímu konstruktoru. Kód v nestatické `do` část vazby můžete odkazovat na primární konstruktor parametry a hodnoty nebo funkce, které jsou definovány v `let` část vazby.

Nestatických `do` vazby můžete přistupovat k členům třídy, pokud třída má vlastní identifikátor, který je definován `as` – klíčové slovo ve třídě nadpis a dokud všechna použití těchto členů jsou kvalifikované identifikátoru samotného pro třídu.

Protože `let` vazby inicializovat privátní pole třídy, která je často nutné zajistit, že členové chovat dle očekávání, `do` vazby jsou obvykle umístěny po `let` vazby tak, že kód `do` může vazby Spusťte s plně inicializaci objektu. Pokud se váš kód se pokusí před dokončením inicializace, použijte člena, je vyvolána InvalidOperationException.

Statické `do` vazby můžete odkazovat na statické členy nebo pole nadřazené třídy, ale není instancí členů nebo pole. Statické `do` vazby se stanou součástí statický inicializátor pro třídu, která je zaručeno, že ke spuštění než třída při prvním použití.

Atributy se ignorují. pro `do` vazby v typech. Pokud je požadované pro kód, který se spustí v atributu `do` vazby, musí být použita k primárnímu konstruktoru.

V následujícím kódu, že třída používá statickou `do` vazby a nestatická `do` vazby. Objekt nemá konstruktor, který má dva parametry `a` a `b`, a dvě soukromé pole jsou definována v `let` vazby pro třídu. Dvě vlastnosti jsou také definovány. Všechny z nich jsou v oboru v nestatické `do` část vazby, které jsou popsány v řádku, který vypíše všechny tyto hodnoty.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

Výstup je následující.

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>Viz také:

- [Členové](index.md)
- [Třídy](../classes.md)
- [Konstruktory](constructors.md)
- [`let` Vazby ve třídách](let-bindings-in-classes.md)
- [`do` Vazby](../functions/do-Bindings.md)