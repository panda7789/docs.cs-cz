---
title: Řízení přístupu (F#)
description: Zjistěte, jak řídit přístup k programovací prvky, jako jsou typy, metody a funkce, F# programovací jazyk.
ms.date: 05/16/2016
ms.openlocfilehash: 136eba5ec33fa6128e677b614fc0ace3c71d17df
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153706"
---
# <a name="access-control"></a>Access Control

*Řízení přístupu* odkazuje na deklarace, které klienty můžete použít některé prvky programu, jako jsou typy, metody a funkce.

## <a name="basics-of-access-control"></a>Základní informace o řízení přístupu

V F#, specifikátorů řízení přístupu `public`, `internal`, a `private` lze použít u modulů, typy, metody, definice hodnot, funkce, vlastnosti a explicitní pole.

- `public` Označuje, že entita je přístupný všem volajícím.

- `internal` Označuje, že entita je přístupný jenom ze stejného sestavení.

- `private` Označuje, že entita je přístupný pouze z nadřazeného typu nebo modulu.

> [!NOTE]
> Specifikátor přístupu `protected` se nepoužívá v F#, i když je přijatelné, pokud používáte typů definovaných v jazycích, které podporují `protected` přístup. Proto pokud je přepsat chráněnou metodu, metodu zůstane dostupný jenom v rámci třídy a jeho následovníky.

Obecně platí, je specifikátor umístit před název sady entit, kromě případů, kdy `mutable` nebo `inline` specifikátor se používá, které se zobrazí po specifikátoru přístupu ovládacího prvku.

Pokud není použit žádný specifikátor přístupu, výchozí hodnota je `public`, s výjimkou `let` vazby v typu, které jsou vždy `private` typu.

Podpisy v F# jiný mechanismus pro řízení přístupu k F# prvky programu. Podpisy nejsou požadována pro řízení přístupu. Další informace najdete v tématu [podpisy](signatures.md).

## <a name="rules-for-access-control"></a>Pravidla pro řízení přístupu

Řízení přístupu se vztahují následující pravidla:

- Deklarace dědičnosti (to znamená použití `inherit` k určení základní třída pro třídu), deklarace (které se určuje, že třída implementuje rozhraní) rozhraní a abstraktní členové mají vždy stejnou přístupností jako nadřazený typ. Proto nelze použít specifikátor řízení přístupu na tyto konstrukce.

- Usnadnění pro jednotlivé případy diskriminovaného sjednocení se určuje podle usnadnění diskriminované sjednocení, samotného. To znamená je konkrétní – případ typu union ne míň dostupný než samotné sjednocení.

- Usnadnění pro jednotlivá pole záznamu typu nelze je určena dostupnost samotného záznamu. Popisek konkrétního záznamu je tedy ne míň dostupný než samotného záznamu.

## <a name="example"></a>Příklad

Následující kód ukazuje použití specifikátorů řízení přístupu. Existují dva soubory v projektu `Module1.fs` a `Module2.fs`. Každý soubor je implicitně modul. Proto existují dva moduly `Module1` a `Module2`. Typ privátní a interní typ jsou definovány v `Module1`. Privátní typ nejde přistupovat z `Module2`, ale můžete vnitřního typu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]

Následující kód testy přístupnost typů vytvořených v `Module1.fs`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Signatury](signatures.md)
