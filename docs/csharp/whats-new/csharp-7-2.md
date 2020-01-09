---
title: Co je nového v C# 7,2
description: Přehled nových funkcí v C# 7,2.
ms.date: 08/16/2017
ms.openlocfilehash: 7febefb81bbea6f24690adb05488ad6a18bbf552
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694592"
---
# <a name="whats-new-in-c-72"></a>Co je nového v C# 7,2

C#7,2 je další vydání bodu, které přidává řadu užitečných funkcí.
Jeden motiv pro tuto verzi je efektivnější pracovat s typy hodnot, protože se vyhnete zbytečným kopiím nebo přidělením.

Zbývající funkce jsou malé, skvělé funkce.

C#7,2 používá prvek konfigurace [výběru jazykové verze](../language-reference/configure-language-version.md) k výběru verze jazyka kompilátoru.

Nové funkce jazyka v této verzi jsou:

- [Techniky pro psaní bezpečného efektivního kódu](#safe-efficient-code-enhancements)
  - Kombinace vylepšení syntaxe, která umožňuje práci s typy hodnot pomocí sémantiky odkazů.
- [Nekoncové pojmenované argumenty](#non-trailing-named-arguments)
  - Pojmenované argumenty mohou následovat Poziční argumenty.
- [Počáteční podtržítka v numerických literálech](#leading-underscores-in-numeric-literals)
  - Číselné literály teď můžou mít počáteční podtržítka před všemi vytištěnými číslicemi.
- [`private protected` modifikátor přístupu](#private-protected-access-modifier)
  - Modifikátor přístupu `private protected` umožňuje přístup pro odvozené třídy ve stejném sestavení.
- [Podmíněné `ref` výrazy](#conditional-ref-expressions)
  - Výsledek podmíněného výrazu (`?:`) nyní může být odkazem.

Zbývající část tohoto článku poskytuje přehled jednotlivých funkcí. U každé funkce se dozvíte, co je důvod na pozadí. Naučíte se syntaxí. Tyto funkce můžete ve svém prostředí prozkoumat pomocí globálního nástroje `dotnet try`:

1. Nainstalujte nástroj [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.
1. Naklonujte úložiště [dotnet/try-Samples](https://github.com/dotnet/try-samples) .
1. Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *Try-Samples* .
1. Spusťte `dotnet try`.

## <a name="safe-efficient-code-enhancements"></a>Bezpečné efektivní vylepšení kódu

Jazykové funkce představené v 7,2 umožňují pracovat s typy hodnot při použití sémantiky odkazů. Jsou navržené tak, aby zvýšily výkon tím, že minimalizují typy hodnot, aniž by došlo k přidělení paměti spojené s použitím typů odkazů. Mezi funkce patří:

- Modifikátor `in` u parametrů určuje, že argument je předán odkazem, ale není upraven metodou volané. Přidání modifikátoru `in` k argumentu je [Změna kompatibilní se zdrojem](version-update-considerations.md#source-compatible-changes).
- Modifikátor `ref readonly` v metodě se vrátí, aby označoval, že metoda vrací svou hodnotu odkazem, ale nepovoluje zápisy do tohoto objektu. Přidání modifikátoru `ref readonly` je [změnou kompatibilní se zdrojem](version-update-considerations.md#source-compatible-changes), pokud je vrácená hodnota přiřazena k hodnotě. Přidání modifikátoru `readonly` k existujícímu příkazu return `ref` je [nekompatibilní změna](version-update-considerations.md#incompatible-changes). Vyžaduje, aby volající aktualizovali deklaraci `ref` místních proměnných, aby obsahoval modifikátor `readonly`.
- Deklarace `readonly struct`, která označuje, že struktura je neměnná a měla by být předána jako `in` parametr svým členským metodám. Přidání modifikátoru `readonly` do existující deklarace struktury je [binární kompatibilní změna](version-update-considerations.md#binary-compatible-changes).
- Deklarace `ref struct`, která označuje, že typ struktury přistupuje přímo k spravované paměti a musí být vždy přiděleno zásobníku. Přidání modifikátoru `ref` do existující deklarace `struct` je [nekompatibilní změna](version-update-considerations.md#incompatible-changes). `ref struct` nemůže být členem třídy ani používat v jiných umístěních, kde může být přidělena na haldu.

Můžete si přečíst další informace o všech těchto změnách v [bezpečném kódu pro zápis](../write-safe-efficient-code.md).

## <a name="non-trailing-named-arguments"></a>Nekoncové pojmenované argumenty

Volání metody teď můžou používat pojmenované argumenty, které předcházejí Poziční argumenty, pokud jsou tyto pojmenované argumenty ve správných pozicích. Další informace naleznete u [pojmenovaných a nepovinných argumentů](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Počáteční podtržítka v numerických literálech

Implementace podpory pro oddělovače číslic v C# 7,0 neumožňuje `_` být prvním znakem hodnoty literálu. Šestnáctkové a binární číselné literály mohou nyní začínat `_`.

Příklad:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>Modifikátor *privátního chráněného* přístupu

Nový modifikátor složeného přístupu: `private protected` určuje, že člen může být přístupný pomocí obsahující třídy nebo odvozené třídy, které jsou deklarovány ve stejném sestavení. I když `protected internal` umožňuje přístup odvozenými třídami nebo třídami, které jsou ve stejném sestavení, `private protected` omezuje přístup k odvozeným typům deklarovaným ve stejném sestavení.

Další informace najdete v tématu [modifikátory přístupu](../language-reference/keywords/access-modifiers.md) v referenční příručce jazyka.

## <a name="conditional-ref-expressions"></a>Podmíněné `ref` výrazy

Nakonec podmíněný výraz může namísto výsledku hodnoty vytvořit ref výsledek. Například zapíšete následující příkaz, který načte odkaz na první prvek v jednom ze dvou polí:

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

Proměnná `r` je odkaz na první hodnotu buď v `arr` nebo `otherArr`.

Další informace naleznete v tématu [podmíněný operátor (?:)](../language-reference/operators/conditional-operator.md) v referenční příručce jazyka.
