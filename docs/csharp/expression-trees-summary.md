---
title: Souhrn stromů výrazů
description: Rekapitulace použití stromů výrazů k vytvoření dynamické programy, které interpretovat kód jako data a vytvářet nové funkce založené na tento kód.
ms.date: 06/20/2016
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 99b9463df096d3aada19ed7995b04ef4bd41c179
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646563"
---
# <a name="expression-trees-summary"></a>Souhrn stromů výrazů

[Předchozí – Překlad výrazů](expression-trees-translating.md)

V této sérii, jste viděli, jak můžete *stromů výrazů* k vytvoření dynamické programy, které interpretovat kód jako data a vytvářet nové funkce založené na tento kód.

Můžete prozkoumat stromů výrazů k porozumění záměru algoritmus. Nelze jenom zkontrolujte, že kód. Můžete vytvářet nové stromů výrazů, které představují upravené verze původního kódu.

Můžete také použití stromů výrazů se podívat na algoritmus a převede tento algoritmus na jiný jazyk nebo prostředí. 

## <a name="limitations"></a>Omezení

Existují některé novější C# prvky jazyka, které není převedou kontejneru stromů výrazů. Stromy výrazů nesmí obsahovat `await` výrazy, nebo `async` výrazů lambda. Mnoho z funkcí přidaných do C# verze 6, nejsou zobrazeny přesně napsané ve stromu výrazu. Místo toho novější funkce se zveřejní ve stromech výrazů v ekvivalentní, starší syntaxi. Toto video asi co nejvíce z omezení jak si možná myslíte. Ve skutečnosti znamená, že váš kód, který stromů výrazů interpretuje bude pravděpodobně stále fungovat stejně při zavedení nových funkcí jazyka.

I přes tato omezení stromů výrazů umožňují vytvářet dynamické algoritmy, které využívají interpretace a upravovat kód, který je reprezentován jako datová struktura. Je výkonný nástroj, a je jednou z funkcí ekosystému .NET, která umožňuje rozsáhlé knihovny, jako je například rozhraní Entity Framework provedete, co dělají.
