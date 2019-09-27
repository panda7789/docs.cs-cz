---
title: Co je nového v C# 7,2
description: Přehled nových funkcí v C# 7,2.
ms.date: 08/16/2017
ms.openlocfilehash: d559f07c501b2a79472d01e2815b50cd8f0f57a5
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332310"
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
- [`private protected`modifikátor přístupu](#private-protected-access-modifier)
  - Modifikátor `private protected` přístupu umožňuje přístup pro odvozené třídy ve stejném sestavení.
- [Podmíněné `ref` výrazy](#conditional-ref-expressions)
  - Výsledek podmíněného výrazu (`?:`) nyní může být odkazem.

Zbývající část tohoto článku poskytuje přehled jednotlivých funkcí. U každé funkce se dozvíte, co je důvod na pozadí. Naučíte se syntaxí. Pomocí `dotnet try` globálního nástroje můžete prozkoumat tyto funkce ve vašem prostředí:

1. Nainstalujte nástroj [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.
1. Naklonujte úložiště [dotnet/try-Samples](https://github.com/dotnet/try-samples) .
1. Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *Try-Samples* .
1. Spusťte `dotnet try`.

## <a name="safe-efficient-code-enhancements"></a>Bezpečné efektivní vylepšení kódu

Jazykové funkce představené v 7,2 umožňují pracovat s typy hodnot při použití sémantiky odkazů. Jsou navržené tak, aby zvýšily výkon tím, že minimalizují typy hodnot, aniž by došlo k přidělení paměti spojené s použitím typů odkazů. Mezi funkce patří:

- `in` Modifikátor u parametrů pro určení, že argument je předán odkazem, ale není upravován metodou volané. Přidání modifikátoru k argumentu je [Změna ve zdroji kompatibilní se zdrojem](version-update-considerations.md#source-compatible-changes). `in`
- `ref readonly` Modifikátor metody se vrátí, aby označoval, že metoda vrací svou hodnotu odkazem, ale nepovoluje zápisy do tohoto objektu. Přidání modifikátoru je změna ve zdroji, která je [kompatibilní se zdrojem](version-update-considerations.md#source-compatible-changes), pokud je vrácená hodnota přiřazena k hodnotě. `ref readonly` Přidání modifikátoru k existujícímu `ref` příkazu return je [nekompatibilní změna.](version-update-considerations.md#incompatible-changes) `readonly` Vyžaduje, aby volající aktualizovali deklaraci `ref` místních proměnných, aby `readonly` obsahoval modifikátor.
- Deklarace, která označuje, že struktura je neměnný a měla by být předána `in` jako parametr jeho členským metodám. `readonly struct` Přidání modifikátoru k existující deklaraci struktury je [binární kompatibilní změna.](version-update-considerations.md#binary-compatible-changes) `readonly`
- `ref struct` Deklarace, která označuje, že typ struktury přistupuje přímo k spravované paměti a musí se vždy přidělit zásobníku. Přidání modifikátoru k existující `struct` deklaraci je [nekompatibilní změna.](version-update-considerations.md#incompatible-changes) `ref` Objekt `ref struct` nemůže být členem třídy ani použit v jiných umístěních, kde může být přidělena na haldu.

Můžete si přečíst další informace o všech těchto změnách v [bezpečném kódu pro zápis](../write-safe-efficient-code.md).

## <a name="non-trailing-named-arguments"></a>Nekoncové pojmenované argumenty

Volání metody teď můžou používat pojmenované argumenty, které předcházejí Poziční argumenty, pokud jsou tyto pojmenované argumenty ve správných pozicích. Další informace naleznete u [pojmenovaných a nepovinných argumentů](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Počáteční podtržítka v numerických literálech

Implementace podpory pro oddělovače číslic v C# 7,0 neumožňuje, `_` aby byl prvním znakem hodnoty literálu. Šestnáctkové a binární číselné literály mohou nyní začínat `_`znakem.

Příklad:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>Modifikátor *privátního chráněného* přístupu

Nový modifikátor složeného přístupu: `private protected` označuje, že člen může být přístupný pomocí obsahující třídy nebo odvozené třídy, které jsou deklarovány ve stejném sestavení. I `protected internal` když umožňuje přístup odvozenými třídami nebo třídami, které jsou ve `private protected` stejném sestavení, omezují přístup k odvozeným typům deklarovaným ve stejném sestavení.

Další informace najdete v tématu [modifikátory přístupu](../language-reference/keywords/access-modifiers.md) v referenční příručce jazyka.

## <a name="conditional-ref-expressions"></a>Podmíněné `ref` výrazy

Nakonec podmíněný výraz může namísto výsledku hodnoty vytvořit ref výsledek. Například zapíšete následující příkaz, který načte odkaz na první prvek v jednom ze dvou polí:

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

Proměnná `r` je odkaz na první hodnotu `arr` v nebo `otherArr`.

Další informace naleznete v tématu [podmíněný operátor (?:)](../language-reference/operators/conditional-operator.md) v referenční příručce jazyka.
