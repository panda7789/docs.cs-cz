---
title: Implicitně zadané lambda výrazy
description: Zjistěte, proč nelze použít implicitně zadávanou deklaraci proměnné k deklarování výrazu lambda.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: ef437ef961210290db4150a8a5cfb70e01aee958
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145719"
---
# <a name="implicitly-typed-lambda-expressions"></a>Implicitně zadané lambda výrazy

Implicitně zadávanou deklaraci proměnné nelze použít k deklarování výrazu lambda.
Vytvoří cyklický logický problém pro kompilátor. Deklarace `var` říká kompilátoru zjistit typ proměnné z typu výrazu na pravé straně operátoru přiřazení. Výraz lambda nemá typ času kompilace, ale je konvertibilní s libovolným odpovídajícím delegátem nebo typem výrazu. Když přiřadíte výraz lambda proměnné delegáta nebo typu výrazu, sdělíte kompilátoru, aby se pokusil převést výraz lambda na výraz nebo delegáta, který odpovídá podpisu proměnné přiřazeno. Kompilátor se musí pokusit, aby věc na pravé straně přiřazení odpovídala typu na levé straně přiřazení.

Obě strany přiřazení nemůže být říkat kompilátoru podívat se na objekt na druhé straně operátoru přiřazení a zjistěte, zda můj typ odpovídá.

Můžete získat ještě více podrobností o tom, proč jazyk C# určuje, že chování čtením [tohoto článku](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF ke stažení).
