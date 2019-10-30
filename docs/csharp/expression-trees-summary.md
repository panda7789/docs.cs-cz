---
title: Souhrn stromů výrazů
description: Mění způsob použití stromů výrazů k vytváření dynamických programů, které interpretují kód jako data a vytvářejí nové funkce založené na tomto kódu.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 43715c94b70f1cd7f758cde91ae7c8d1b2f70f9f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036746"
---
# <a name="expression-trees-summary"></a>Souhrn stromů výrazů

[Předchozí--posunutí výrazů](expression-trees-translating.md)

V této řadě jste viděli, jak můžete pomocí *stromů výrazů* vytvářet dynamické programy, které interpretují kód jako data a vytvářejí nové funkce založené na tomto kódu.

Můžete prozkoumávat stromy výrazů a pochopit záměr algoritmu. Tento kód nelze kontrolovat. Můžete vytvořit nové stromy výrazů, které reprezentují upravené verze původního kódu.

Můžete také použít stromy výrazů k zobrazení algoritmu a překladu tohoto algoritmu do jiného jazyka nebo prostředí. 

## <a name="limitations"></a>Omezení

Existují některé novější C# jazykové prvky, které nemusejí být dobře přeloženy do stromů výrazů. Stromy výrazů nemůžou obsahovat výrazy `await` ani `async` výrazy lambda. Mnohé z funkcí přidaných v C# 6. verzi se ve stromech výrazů přesně neprojeví jako zapsané. Místo toho budou ve stromech výrazů k dispozici novější funkce v ekvivalentu předchozí syntaxe. To nemusí být tolik omezení, jak si možná myslíte. Ve skutečnosti to znamená, že váš kód, který interpretuje stromy výrazů, bude nejspíš stále fungovat stejně, když jsou zavedeny nové funkce jazyka.

I s těmito omezeními mají stromy výrazů možnost vytvářet dynamické algoritmy, které spoléhají na interpretaci a úpravu kódu, který je reprezentován jako datová struktura. Jedná se o výkonný nástroj a jedná se o jednu z funkcí ekosystému .NET, která umožňuje využít bohatých knihoven, jako je například Entity Framework k tomu, co dělají.
