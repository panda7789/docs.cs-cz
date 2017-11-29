---
title: "C# výčty - přehled používání jazyka C#"
description: "Další informace o výčty, diskrétní s názvem konstanty v jazyku C#"
keywords: "Rozhraní .NET, csharp"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 77d315dd87d9cab32605de415674d146eb9115fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="enums"></a>Výčty

***Typ výčtu*** je typ odlišné hodnoty sadu pojmenované konstanty. Pokud potřebujete definovat typ, který může mít sadu diskrétních hodnot definujete výčty. Používají jeden z typů celočíselné hodnoty jako svoje základní úložiště. Poskytují význam sémantického diskrétní hodnoty.

Následující příklad deklaruje a používá `enum` typ s názvem `Color` s tři konstantní hodnoty, `Red`, `Green`, a `Blue`.

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

Každý `enum` typ má odpovídající integrální typu s názvem ***základní typ*** z `enum` typu. `enum` Typ, který nedeklaruje základní typ explicitně má základní typ `int`. `enum` Formát úložiště typu a rozsahu možných hodnot určuje jeho zdrojovým typem. Sada hodnoty, které `enum` typ může trvat na není omezený jeho `enum` členy. Konkrétně žádnou hodnotu základní typ `enum` lze převést na `enum` zadejte a odlišné platná hodnota této `enum` typu.

Následující příklad deklaruje `enum` typ s názvem `Alignment` s podkladovým typem `sbyte`.

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

Jak ukazuje předchozí příklad, `enum` deklarace členů může zahrnovat konstantní výraz, který určuje hodnotu člena. Konstantní hodnota pro každé `enum` člena musí být v rozsahu základní typ `enum`. Při `enum` deklarace členů neurčuje explicitně hodnotu, člen je zadána hodnota nula (Pokud je první člen v `enum` typu) nebo hodnotu textový předchozí `enum` člen plus jedna.

`Enum`hodnoty mohou být převeden na celočíselné hodnoty a naopak pomocí typ přetypování. Příklad:

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

Výchozí hodnota všech `enum` je integrální hodnota nula převést na typ `enum` typu. V případech, kde jsou automaticky inicializovány proměnné na výchozí hodnotu, je to hodnota zadané proměnné `enum` typy. V pořadí pro výchozí hodnotu `enum` typ, který má být snadno dostupné, skutečné `0` implicitně převede do jakéhokoli `enum` typu. Proto následující je povolená.

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

>[!div class="step-by-step"]
[Předchozí](interfaces.md)
[další](delegates.md)
