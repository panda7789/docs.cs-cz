---
title: Co je nového v jazyce C# 7.2
description: Přehled nových funkcí v C# 7.2.
ms.date: 08/16/2017
ms.openlocfilehash: 7febefb81bbea6f24690adb05488ad6a18bbf552
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75694592"
---
# <a name="whats-new-in-c-72"></a>Co je nového v jazyce C# 7.2

C# 7.2 je další bod vydání, které přidává řadu užitečných funkcí.
Jedním z motivů pro tuto verzi je efektivnější práce s typy hodnot tím, že se vyhnete zbytečným kopiím nebo přidělením.

Zbývající funkce jsou malé, příjemné-k-mít funkce.

C# 7.2 používá prvek konfigurace [výběru jazykové verze](../language-reference/configure-language-version.md) k výběru k výběru verze kompilátoru.

Nové jazykové funkce v této verzi jsou:

- [Techniky pro psaní bezpečného efektivního kódu](#safe-efficient-code-enhancements)
  - Kombinace vylepšení syntaxe, které umožňují práci s typy hodnot pomocí referenční sémantiky.
- [Nekoncové pojmenované argumenty](#non-trailing-named-arguments)
  - Pojmenované argumenty mohou následovat poziční argumenty.
- [Úvodní podtržítka v číselných literálech](#leading-underscores-in-numeric-literals)
  - Číselné literály mohou nyní mít úvodní podtržítka před libovolnými vytištěné číslice.
- [`private protected`modifikátor přístupu](#private-protected-access-modifier)
  - Modifikátor `private protected` přístupu umožňuje přístup pro odvozené třídy ve stejném sestavení.
- [Podmíněné `ref` výrazy](#conditional-ref-expressions)
  - Výsledkem podmíněného výrazu (`?:`) nyní může být odkaz.

Zbývající část tohoto článku obsahuje přehled jednotlivých funkcí. U každé funkce se dozvíte důvody, které za ní stojí. Naučíte se syntaxi. Tyto funkce můžete prozkoumat ve `dotnet try` vašem prostředí pomocí globálního nástroje:

1. Nainstalujte globální nástroj [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)
1. Klonovat úložiště [dotnet/try-samples.](https://github.com/dotnet/try-samples)
1. Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *try-samples.*
1. Spusťte `dotnet try`.

## <a name="safe-efficient-code-enhancements"></a>Bezpečná efektivní vylepšení kódu

Funkce jazyka zavedené v 7.2 umožňují pracovat s typy hodnot při použití referenční sémantiky. Jsou navrženy tak, aby zvýšily výkon minimalizací kopírování typů hodnot bez vzniku přidělení paměti přidruženého k použití typů odkazů. Toto jsou některé z dostupných funkcí:

- Modifikátor `in` parametrů, který určuje, že argument je předán odkazem, ale není změněn volanou metodou. Přidání `in` modifikátoru k argumentu je změna kompatibilní se [zdrojem](version-update-considerations.md#source-compatible-changes).
- Modifikátor `ref readonly` na metodu vrátí, označuje, že metoda vrátí svou hodnotu odkazem, ale neumožňuje zápisy do tohoto objektu. Přidání `ref readonly` modifikátoru je změna kompatibilní se [zdrojem](version-update-considerations.md#source-compatible-changes), pokud je návrat přiřazen hodnotě. Přidání `readonly` modifikátoru `ref` do existujícího příkazu return je [nekompatibilní změna](version-update-considerations.md#incompatible-changes). Vyžaduje, aby volající aktualizovat `ref` deklaraci místních `readonly` proměnných zahrnout modifikátor.
- Deklarace, `readonly struct` označující, že struktura je neměnná a `in` měla by být předána jako parametr jeho členským metodám. Přidání `readonly` modifikátoru do existující deklarace struktury je [binární kompatibilní změna](version-update-considerations.md#binary-compatible-changes).
- Deklarace, `ref struct` označující, že typ struktury přistupuje ke spravované paměti přímo a musí být vždy přidělenzásobníku. Přidání `ref` modifikátoru `struct` do existující deklarace je [nekompatibilní změna](version-update-considerations.md#incompatible-changes). A `ref struct` nemůže být členem třídy nebo použít v jiných umístěních, kde může být přidělena na haldě.

Můžete si přečíst více o všech těchto změnách v [bezpečném efektivním kódu pro zápis](../write-safe-efficient-code.md).

## <a name="non-trailing-named-arguments"></a>Nekoncové pojmenované argumenty

Volání metod může nyní používat pojmenované argumenty, které předcházejí poziční argumenty, pokud jsou tyto pojmenované argumenty ve správných pozicích. Další informace naleznete [v tématu Pojmenované a volitelné argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Úvodní podtržítka v číselných literálech

Implementace podpory oddělovačů číslic v c# 7.0 `_` neumožnila být první znak literál hodnoty. Hex a binární číselné literály `_`nyní mohou začínat písmenem .

Například:

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>*privátní chráněný* přístup modifikátor

Nový modifikátor `private protected` složeného přístupu: označuje, že člen může být přístupný obsahující třídu nebo odvozené třídy, které jsou deklarovány ve stejném sestavení. Zatímco `protected internal` umožňuje přístup odvozené třídy nebo třídy, které jsou ve stejném sestavení, `private protected` omezuje přístup k odvozené typy deklarované ve stejném sestavení.

Další informace naleznete v [tématu modifikátory přístupu](../language-reference/keywords/access-modifiers.md) v odkazu na jazyk.

## <a name="conditional-ref-expressions"></a>Podmíněné `ref` výrazy

Nakonec podmíněný výraz může způsobit ref výsledek namísto výsledku hodnoty. Například byste napsat následující načíst odkaz na první prvek v jednom ze dvou polí:

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

Proměnná `r` je odkaz na první `arr` hodnotu v buď nebo `otherArr`.

Další informace naleznete v tématu [podmíněný operátor (?:)](../language-reference/operators/conditional-operator.md) v odkazu na jazyk.
