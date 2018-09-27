---
title: Co je nového v jazyce C# 7.2
description: Přehled nových funkcí v jazyce C# 7.2.
ms.date: 08/16/2017
ms.openlocfilehash: 87fd67b37a31a02960334a2b2a325724e0cc2c73
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400800"
---
# <a name="whats-new-in-c-72"></a>Co je nového v jazyce C# 7.2

C# 7.2 je jiný bod. Tato verze přidává řadu užitečných funkcí.
Jeden motiv pro tuto verzi je efektivnější práci s typy hodnot se vyhnout zbytečným kopie nebo přidělení. 

Zbývající součásti jsou malé, nice mají funkce.

Používá C# 7.2 [výběr verze jazyka](../language-reference/configure-language-version.md) konfigurační prvek a vyberte verzi jazyka kompilátoru.

Nové funkce jazyků v této verzi jsou:

* [Referenční sémantika s typy hodnot](#reference-semantics-with-value-types)
  - Kombinace syntaxe vylepšení, které umožňují práci s typy hodnot pomocí odkazové sémantiky.
* [Nekoncové pojmenované argumenty](#non-trailing-named-arguments)
  - Pojmenované argumenty může být následován poziční argumenty.
* [Úvodní podtržítka v numerických literálech](#leading-underscores-in-numeric-literals)
  - Číselné literály teď můžou mít úvodní podtržítka před všechny tištěné číslice.
* [`private protected` Modifikátor přístupu](#private-protected-access-modifier)
  - `private protected` Modifikátor přístupu umožňuje přístup pro odvozené třídy ve stejném sestavení.

## <a name="reference-semantics-with-value-types"></a>Referenční sémantika s typy hodnot

Jazykových funkcí 7.2 zavedený umožňují pracovat s typy hodnot a zároveň pomocí odkazové sémantiky. Jsou určené ke zvýšení výkonu minimalizací kopírování hodnotové typy bez dalších nákladů na přidělení paměti spojených s použitím typy odkazů. Mezi funkce patří:

 - `in` Modifikátor parametrů k určení, zda je argument předaný odkazem, ale nedojde ke změně ve volané metody. Přidání `in` modifikátor na argument [zdroj kompatibilní změnu](version-update-considerations.md#source-compatible-changes).
 - `ref readonly` Modifikátor metoda vrátí hodnotu označující, že metoda vrátí jeho hodnota podle odkazu, ale neumožňuje zápisy do tohoto objektu. Přidání `ref readonly` modifikátor [zdroj kompatibilní změnu](version-update-considerations.md#source-compatible-changes), pokud je vrácená přiřadit hodnotu. Přidávání `readonly` modifikačních do existujícího `ref` návratový příkaz je [nekompatibilní změna](version-update-considerations.md#incompatible-changes). Vyžaduje volající aktualizovat deklarace `ref` místní proměnné k zahrnutí `readonly` modifikátor.
 - `readonly struct` Deklarace můžete určit, že struktura je neměnná a mají být předány jako `in` parametr metody jeho členů. Přidání `readonly` modifikátor na existující deklaraci struktury [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).
 - `ref struct` Deklarace můžete určit, že typu Struktura přistupuje k nim spravované paměti přímo a musí vždy zásobníku přidělovat. Přidávání `ref` Modifikátor pro stávající `struct` deklarace je [nekompatibilní změna](version-update-considerations.md#incompatible-changes). A `ref struct` nemůže být členem třídy nebo použít v jiných umístěních, kde mohou být přiděleny do haldy.

Můžete si přečíst další informace o všech těchto změn v [pomocí typů hodnot pomocí odkazové sémantiky](../reference-semantics-with-value-types.md).

## <a name="non-trailing-named-arguments"></a>Nekoncové pojmenované argumenty

Volání metody teď může použít pojmenované argumenty, které předcházet poziční argumenty, pokud tyto pojmenované argumenty jsou do správné polohy. Další informace najdete v části [pojmenované a nepovinné argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Úvodní podtržítka v numerických literálech

Implementace podpory pro oddělovače číslic v jazyce C# 7.0 neměli povolit `_` bude první znak hodnota literálu. Hex a binární číselné literály teď začít s `_`. 

Příklad:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>_privátní, chráněné_ modifikátor přístupu

A konečně, nový modifikátor přístupu složené: `private protected` označuje, že můžou být dostupné členy obsahující třídu nebo odvozené třídy, které jsou deklarovány ve stejném sestavení. Zatímco `protected internal` umožňuje přístup odvozené třídy nebo třídy, které jsou ve stejném sestavení, `private protected` omezuje přístup k odvozené typy deklarované ve stejném sestavení.

Další informace najdete v části [modifikátorů přístupu](../language-reference/keywords/access-modifiers.md) v referenční dokumentaci jazyka.
