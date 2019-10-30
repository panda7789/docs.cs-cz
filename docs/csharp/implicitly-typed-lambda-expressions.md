---
title: Implicitně typované výrazy lambda
description: Zjistěte, proč nemůžete použít deklaraci proměnné s implicitním typem k deklaraci výrazu lambda.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: c6b0f2666a5c67ce8c89222da5959304ecb8fb93
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039129"
---
# <a name="implicitly-typed-lambda-expressions"></a>Implicitně typované výrazy lambda

Deklaraci proměnné s implicitním typem nelze použít k deklaraci výrazu lambda.
Vytvoří kruhovou logickou potíž pro kompilátor. Deklarace `var` instruuje kompilátor, aby typ proměnné z typu výrazu na pravé straně operátoru přiřazení. Výraz lambda nemá typ doby kompilace, ale je převoditelný na libovolný typ odpovídajícího delegáta nebo výrazu. Když přiřadíte výraz lambda proměnné delegáta nebo typu výrazu, říkáte kompilátoru, aby vyzkoušel a převedl výraz lambda na výraz nebo delegáta, který odpovídá podpisu proměnné "přiřazeno". Kompilátor se musí pokusit na pravé straně přiřazení, aby odpovídal typu na levé straně přiřazení. 

Na obou stranách přiřazení nelze kompilátor sdělit, aby procházel na objektu na druhé straně operátoru přiřazení a viděli, zda odpovídá typ.

Můžete získat ještě více podrobností o tom, proč C# jazyk určuje chování tak, že si přečte [Tento článek](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (stažení PDF).
