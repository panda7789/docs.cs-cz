---
title: Vazby do ve třídách (F#)
description: 'Naučte se používat F # "do" vazby v definici třídy, který provádí akce, když je objekt vytvořený, nebo při prvním použití typu.'
ms.date: 05/16/2016
ms.openlocfilehash: 779b33c44b1518135f4c7f270173ec8124fec101
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565188"
---
# <a name="do-bindings-in-classes"></a>Vazby do ve třídách

A `do` vazby v definici třídy provede akce, když je objekt vytvořený nebo pro statického `do` vazby, pokud typ prvním použití.


## <a name="syntax"></a>Syntaxe

```fsharp
[static] do expression
```

## <a name="remarks"></a>Poznámky
A `do` vazba se zobrazí, společně s nebo po `let` vazby, ale před definice člen v definici třídy. I když `do` – klíčové slovo je pro volitelné `do` vazby na úrovni modulu, není pro volitelné `do` vazby v definici třídy.

Pro tvorbu každý objekt libovolného daného typu, nestatické `do` vazby a nestatické `let` vazby jsou spouštěny v pořadí, ve kterém se zobrazí v definici třídy. Více `do` vazby se může objevit v jednoho typu. Nestatické `let` vazby a nestatické `do` vazby stane textem primární konstruktoru. Kód v nestatickou `do` vazby části odkazovat primární konstruktor parametry a všechny hodnoty nebo funkce, které jsou definovány v `let` části vazby.

Nestatické `do` vazby můžete přístup ke členům třídy tak dlouho, dokud třída má vlastní identifikátor, který je definován `as` – klíčové slovo v třídě nadpis a pokud jsou všechny používá tyto členů kvalifikovaný pomocí vlastní identifikátor pro třídu.

Protože `let` vazby inicializovat soukromá pole třídy, který je často nutné zajistit, že členové chovat podle očekávání, `do` vazby jsou obvykle ukládat po `let` vazby, že kód `do` může vazby spustit s objektem plně inicializovaném. Pokud váš kód se pokusí použít člen před dokončením inicializace, je vyvolána výjimkou InvalidOperationException.

Statické `do` vazby mohou odkazovat statické členy nebo pole uzavření do třídy, ale není instance členů nebo pole. Statické `do` vazby stane součástí statické inicializátoru pro třídu, která záruku, že se provést před prvním použití třídy.

Atributy jsou ignorovány pro `do` vazeb v typy. Pokud atribut je požadován pro kód, který spustí `do` vazba, je nutné použít na primární konstruktoru.

V následujícím kódu, třída má statického `do` vazby a nestatickou `do` vazby. Objekt nemá konstruktor, který má dva parametry `a` a `b`, a dva privátní pole jsou definovány v `let` vazby pro třídu. Dvě vlastnosti je definována. Všechny jsou v oboru v nestatickou `do` vazby části, jak je znázorněno použitím řádek, který vypíše všechny tyto hodnoty.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

Výstup je následující.

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a>Viz také
[Členové](index.md)

[Třídy](../classes.md)

[Konstruktory](constructors.md)

[`let` Vazby do ve třídách](let-bindings-in-classes.md)

[`do` Vazby](../functions/do-Bindings.md)
