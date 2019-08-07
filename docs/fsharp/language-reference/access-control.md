---
title: Řízení přístupu
description: Naučte se řídit přístup k programovacím prvkům, jako jsou typy, metody a funkce, v F# programovacím jazyce.
ms.date: 05/16/2016
ms.openlocfilehash: 38f8f3fd4114c0428fbe8baca71594cd07740b2c
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817857"
---
# <a name="access-control"></a>Řízení přístupu

*Řízení přístupu* odkazuje na deklaraci toho, kteří klienti můžou používat určité prvky programu, jako jsou typy, metody a funkce.

## <a name="basics-of-access-control"></a>Základy Access Control

V F#nástroji specifikátory `public`řízení přístupu, `internal`a `private` lze použít na moduly, typy, metody, definice hodnot, funkce, vlastnosti a explicitní pole.

- `public`označuje, že k entitě lze přistupovat všichni volající.

- `internal`označuje, že k entitě lze přistupovat pouze ze stejného sestavení.

- `private`označuje, že k entitě lze přistupovat pouze z ohraničujícího typu nebo modulu.

> [!NOTE]
> Specifikátor `protected` přístupu se nepoužívá v F#, i když je přijatelný, pokud používáte typy vytvořené v `protected` jazycích, které podporují přístup. Proto pokud přepíšete chráněnou metodu, vaše metoda zůstane přístupná pouze v rámci třídy a jejích následníků.

Obecně je specifikátor umístěn před název entity, s výjimkou případu, kdy `mutable` se používá specifikátor nebo `inline` , který se zobrazí po specifikátoru řízení přístupu.

Pokud není použit žádný specifikátor přístupu, je `public`výchozí hodnota, `let` s výjimkou vazeb v typu, které jsou vždy `private` typu.

Signatury F# v nástroji poskytují jiný mechanismus řízení přístupu F# k prvkům programu. Pro řízení přístupu se signatury nevyžadují. Další informace najdete v tématu [signatury](signatures.md).

## <a name="rules-for-access-control"></a>Pravidla pro Access Control

Řízení přístupu podléhá následujícím pravidlům:

- Deklarace dědičnosti (to znamená použití `inherit` k určení základní třídy pro třídu), deklarace rozhraní (to znamená, že třída implementuje rozhraní) a abstraktní členové mají vždy stejné přístupnost jako nadřazený typ. Proto specifikátor řízení přístupu nelze použít na těchto konstrukcích.

- Přístupnost pro jednotlivé případy v rozlišeném sjednocení je určena přístupným přístupu přímo k rozlišenému sjednocení. To znamená, že konkrétní případ typu Union není méně dostupný než samotný sjednocení.

- Přístupnost pro jednotlivá pole typu záznamu je určena přístupností samotného záznamu. To znamená, že konkrétní popisek záznamu není méně dostupný než samotný záznam.

## <a name="example"></a>Příklad

Následující kód ilustruje použití specifikátorů řízení přístupu. V projektu jsou dva soubory, `Module1.fs` a. `Module2.fs` Každý soubor je implicitně modulem. Proto existují dva moduly `Module1` a. `Module2` Privátní typ a interní typ jsou definovány v `Module1`. K privátnímu typu nelze přicházet `Module2`z, ale interní typ může.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

Následující kód testuje přístupnost typů vytvořených v `Module1.fs`.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Signatury](signatures.md)
