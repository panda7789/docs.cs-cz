---
title: "Souhrn stromů výrazů"
description: "Recaps použití stromů výrazů k vytvoření dynamických programy, které interpretovat kód jako data a vytvářet nové funkce založené na tento kód."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 8088ce0c138cdb05a6e4a4fb6467e43efd252ba7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="expression-trees-summary"></a>Souhrn stromů výrazů

[Předchozí – Překladu výrazy](expression-trees-translating.md)

Z této série jste viděli, jak můžete použít *stromů výrazů* vytvořit dynamické programy, které interpretovat kód jako data a vytvářet nové funkce založené na tento kód.

Stromy výrazů pochopit záměr algoritmus můžete zkontrolovat. Nelze pouze prozkoumat tento kód. Můžete vytvořit nové stromů výrazů, které představují upravené verze původní kód.

Můžete taky použití stromů výrazů k podívejte se na algoritmus a převede tento algoritmus na jiný jazyk nebo prostředí. 

## <a name="limitations"></a>Omezení

Existují některé novější C# jazyka prvky, které nejsou převede i na stromů výrazů. Stromy výrazů nesmí obsahovat `await` výrazy, nebo `async` výrazy lambda. Mnoho funkcí přidaných do verze jazyka C# 6 tak, jak je napsaný v stromů výrazů nezobrazí. Místo toho novější funkce zveřejní ve stromech výrazy v syntaxi ekvivalentní, dřívější. Toto nemusí být tolik omezeními může si myslíte. Ve skutečnosti znamená, že váš kód, který interpretuje stromů výrazů bude stále pravděpodobně fungovat stejně při byly zavedeny nové jazykové funkce.

I když tato omezení stromů výrazů umožňují vytvářet dynamické algoritmy, které závisí na interpretace a úpravy kódu, který je reprezentován jako datové struktury. Je výkonný nástroj a je jedna z funkcí ekosystému .NET, která umožňuje bohaté knihovny, například rozhraní Entity Framework dosáhnout toho, co dělají.

