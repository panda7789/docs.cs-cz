---
title: "Co je nového v C# 7.2"
description: "Přehled nových funkcí v C# 7.2."
keywords: "C# jazyka návrhu, 7.2, Visual Studio 2017"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: cc861f186bea681bb32a2f8041a7155026679987
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2017
---
# <a name="whats-new-in-c-72"></a>Co je nového v C# 7.2

C# 7.2 je jiné verze bodu, který přidává několik užitečných funkcí.
Jeden motivu pro tuto verzi je efektivnější práci s typy hodnot vyhnout nepotřebné kopie nebo přidělení. 

Zbývající součásti jsou malé, dobrý obsahovat funkce.

C# 7.2 používá [výběr verze jazyka](csharp-7-1.md#language-version-selection) prvku konfigurace vyberte verzi jazyka kompilátoru.

Mezi nové jazykové funkce v této verzi jsou:

* [Odkaz na sémantiku s typy hodnot](#reference-semantics-with-value-types)
  - Kombinace syntaxe vylepšení, které umožňují práci s typy hodnot pomocí sémantiky odkaz.
* [Bez koncové pojmenované argumenty](#non-trailing-named-arguments)
  - Pojmenované argumenty může následovat poziční argumenty.
* [Úvodní podtržítka v číselné literály](#leading-underscores-in-numeric-literals)
  - Číselné literály teď může mít úvodní podtržítka před žádné tištěné číslice.
* [`private protected`Modifikátor přístupu](#private-protected)
  - `private protected` – Modifikátor přístupu umožňuje přístup k odvozené třídy ve stejném sestavení.

## <a name="reference-semantics-with-value-types"></a>Odkaz na sémantiku s typy hodnot

Jazykové funkce byla zavedená v 7.2 umožňují pracovat s typy hodnot při používání sémantiky odkaz. Jsou navrženy pro zvýšení výkonu pomocí minimalizace kopírování typy hodnot, aniž by docházelo k přidělení paměti související s používáním odkazové typy. Funkce patří:

 - `in` – Modifikátor parametrů, chcete-li určit, že je argument předaná odkaz ale nedojde ke změně volané metodou.
 - `ref readonly` Modifikátor na metoda vrátí označíte, že metoda vrátí jeho hodnotu odkazem, ale neumožňuje zápisy na tento objekt.
 - `readonly struct` Prohlášení znamená, že struktury se nedá změnit a mají být předány jako `in` parametru její metody člen.
 - `ref struct` Prohlášení znamená, že typu Struktura přistupují k spravované paměti přímo a musí vždy zásobníku přidělit.

Můžete si přečíst informace o všech těchto změn v [typů hodnot pomocí sémantiky odkaz](../reference-semantics-with-value-types.md).

## <a name="non-trailing-named-arguments"></a>Bez koncové pojmenované argumenty

Volání metody teď může použít pojmenované argumenty, které předcházet argumentů umístění těchto pojmenovaných argumenty po na správném místě. Další informace najdete v části [pojmenované a nepovinné argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md).

## <a name="leading-underscores-in-numeric-literals"></a>Úvodní podtržítka v číselné literály

Implementace podpory pro číslice oddělovače v C# 7.0 neumožnila `_` jako první znak literálovou hodnotou. Hex a binární číselné literály může teď začínají `_`. 

Příklad:

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

Nakonec novou modifikátor přístupu složené: `private protected` znamená, že může být členem přistupovat pomocí obsahující třídu nebo odvozené třídy, které jsou deklarovány ve stejném sestavení. Při `protected internal` umožňuje přístup odvozené třídy nebo třídy, které jsou ve stejném sestavení `private protected` omezuje přístup na odvozené typy deklarován ve stejném sestavení.

Další informace najdete v části [přístup modifikátory](../language-reference/keywords/access-modifiers.md) v dokumentu.
