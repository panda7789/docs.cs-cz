---
title: Řízení přístupu (F#)
description: 'Zjistěte, jak řídit přístup k elementům programování, jako jsou typy, metod a funkce v programovací jazyk F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: fee5f719904b61c3082d56f73448defdea39f472
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="access-control"></a>Access Control

*Řízení přístupu* odkazuje na deklarace, které klienty můžete použít určité program elementů, například typy, metod a funkce.


## <a name="basics-of-access-control"></a>Základní informace o řízení přístupu
V jazyce F #, řízení přístupu specifikátory `public`, `internal`, a `private` lze použít na moduly, typy, metody, definice hodnotu, funkce, vlastnosti a explicitní pole.


- `public` Označuje, že entita byla přístupná pomocí všechny volající.

- `internal` Označuje, že entita může přistupovat pouze z stejného sestavení.

- `private` Označuje, že entita může přistupovat pouze z nadřazených modul nebo typ.


>[!NOTE] 
Specifikátor přístupu `protected` se nepoužívá v F # je přijatelné, pokud používáte typy vytvořené v jazycích, které podporují `protected` přístup. Proto pokud chráněný metodu přepíšete, metodu zůstávají dostupné pouze v rámci třídy a jejího podřízeného prvku.

Obecně platí, je před název entity, s výjimkou případů, kdy se umístí specifikátor `mutable` nebo `inline` specifikátor se používá, které jsou uvedeny po specifikátor řízení přístupu.

Pokud se používá žádný přístup specifikátor, výchozí hodnota je `public`, s výjimkou `let` vazeb v typu, které jsou vždy `private` typu.

Podpisy v jazyce F # nabízejí jiný mechanismus řízení přístupu na elementy program F #. Podpisy nejsou nutné pro řízení přístupu. Další informace najdete v tématu [podpisy](signatures.md).


## <a name="rules-for-access-control"></a>Pravidla pro řízení přístupu
Řízení přístupu podléhá následující pravidla:


- Deklarace dědičnosti (to znamená použití `inherit` určit základní třídu pro třídu), rozhraní deklarace (které se určuje, že třída implementuje rozhraní) a abstraktní členy, bude mít vždy stejnou usnadnění jako nadřazených typů. Proto nelze použít specifikátor řízení přístupu na tyto konstrukce.

- Rozlišovaná sjednocení jednotlivých případech, nemůže mít vlastní ovládací prvek modifikátory přístupu odděleně od typu union.

- Jednotlivá pole typu záznamu nemůže mít vlastní ovládací prvek modifikátory přístupu odděleně od typ záznamu.


## <a name="example"></a>Příklad
Následující kód ukazuje použití specifikátory řízení přístupu. Existují dva soubory v projektu `Module1.fs` a `Module2.fs`. Každý soubor je implicitně modul. Proto existují dvě moduly `Module1` a `Module2`. Typu privátní a interní typ jsou definovány v `Module1`. Typ privátního není přístupný z `Module2`, ale můžete interní typ.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
Následující kód testy usnadnění typů vytvořené v `Module1.fs`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Signatury](signatures.md)
