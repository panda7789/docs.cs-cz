---
title: C#Výčty – připravuje C# jazyka
description: Další informace o výčtů diskrétní pojmenované konstanty vC#
ms.date: 08/10/2016
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: d55462f0360b6896c398d581918a9c17a87583be
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126651"
---
# <a name="enums"></a>Výčty

***Typ výčtu*** je typ odlišné hodnoty se sadou pojmenovaných konstant. Můžete definovat výčty, pro které je třeba definovat typ, který může mít sady jednotlivých hodnot. Používají jeden z typů celočíselné hodnoty jako svoje základní úložiště. Poskytují sémantický význam jednotlivých hodnot.

Následující příklad deklaruje a používá `enum` typ s názvem `Color` pomocí tří hodnot konstanty `Red`, `Green`, a `Blue`.

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

Každý `enum` typ má odpovídající integrální typ s názvem ***nadřízený typ*** z `enum` typu. `enum` Typ, který nedeklaruje explicitně nadřízený typ má základní typ `int`. `enum` Úložném formátu a rozsah možných hodnot typu se určují podle jeho nadřízeného typu. Sadu hodnot, které `enum` typu můžete provést na nebude omezen jeho `enum` členy. Konkrétně se libovolná hodnota základního typu `enum` lze převést na `enum` typ a je odlišné platnou hodnotou, která `enum` typu.

Následující příklad deklaruje `enum` typ s názvem `Alignment` pomocí základního typu `sbyte`.

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

Jak je znázorněno v předchozím příkladu, `enum` deklarace člena. může obsahovat konstantní výraz, který určuje hodnotu člena. Konstantní hodnota pro každé `enum` člen musí být v rozsahu od základního typu `enum`. Při `enum` deklarace člena explicitně neurčí hodnotu, člen je zadána hodnota nula (Pokud je první člen v `enum` typ) nebo hodnotu textový předchozí `enum` člena plus jedna.

`Enum` hodnoty mohou být převedeny na integrální hodnoty a naopak pomocí přetypování. Příklad:

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

Zadejte výchozí hodnotu kterékoli `enum` je celočíselná hodnota nula, převést na typ `enum` typu. V případech, kdy proměnné jsou automaticky inicializovány na výchozí hodnotu, jedná se o hodnotu k proměnné `enum` typy. Aby výchozí hodnota `enum` typ, který má být snadno k dispozici, literál `0` implicitně převede na jakýkoli `enum` typu. Proto následující je povolený.

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

>[!div class="step-by-step"]
>[Předchozí](interfaces.md)
>[další](delegates.md)