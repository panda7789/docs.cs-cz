---
title: Souhrn stromů výrazů
description: Rekapituluje, jak můžete pomocí stromů výrazů vytvářet dynamické programy, které interpretují kód jako data, a vytvářet nové funkce založené na tomto kódu.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 513244a987e295c81cfb5d00d9a0cfd6912074e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145888"
---
# <a name="expression-trees-summary"></a>Souhrn stromů výrazů

[Předchozí -- Překlad výrazů](expression-trees-translating.md)

V této řadě jste viděli, jak můžete pomocí *stromů výrazů* vytvářet dynamické programy, které interpretují kód jako data, a vytvářet nové funkce založené na tomto kódu.

Můžete prozkoumat stromy výrazů pochopit záměr algoritmu. Můžete nejen zkoumat tento kód. Můžete vytvořit nové stromy výrazů, které představují upravené verze původního kódu.

Stromy výrazů můžete také použít k pohledu na algoritmus a přeložit tento algoritmus do jiného jazyka nebo prostředí.

## <a name="limitations"></a>Omezení

Existují některé novější prvky jazyka Jazyka Jazyka Jazyka C#, které se nepřekládají dobře do stromů výrazů. Stromy výrazů `await` nemohou obsahovat výrazy nebo `async` výrazy lambda. Mnoho funkcí přidaných ve verzi C# 6 se nezobrazuje přesně tak, jak je napsáno ve stromech výrazů. Místo toho budou novější funkce vystaveny ve stromech výrazů v ekvivalentní starší syntaxi. To nemusí být tak velké omezení, jak si možná myslíte. Ve skutečnosti to znamená, že váš kód, který interpretuje stromy výrazů bude pravděpodobně i nadále fungovat stejně, když jsou zavedeny nové funkce jazyka.

I s těmito omezeními stromy výrazů umožňují vytvářet dynamické algoritmy, které spoléhají na interpretaci a úpravu kódu, který je reprezentován jako datová struktura. Je to mocný nástroj a je to jedna z funkcí ekosystému .NET, který umožňuje bohaté knihovny, jako je entity Framework k dosažení toho, co dělají.
