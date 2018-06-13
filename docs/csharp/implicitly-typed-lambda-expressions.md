---
title: Implicitně typovaná lambda – výrazy
description: Zjistěte, proč nelze používat deklarace proměnné implicitně typované deklarovat výrazu lambda.
ms.date: 06/20/2016
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: f06c55f51c30c941d6d507ac8e2edd95c5152742
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211820"
---
# <a name="implicitly-typed-lambda-expressions"></a>Implicitně typovaná lambda – výrazy

Nepoužívám `var` deklarovat tento strom výrazu. Nelze použít implicitně typovaná deklarace proměnné deklarovat výrazu lambda.
Vytvoří problém cyklické logiku pro kompilátor. `var` Deklarace říká kompilátoru a pokuste se zjistit typ proměnné z typ výrazu na pravé straně operátoru přiřazení. Výraz lambda nemá typu time kompilace, ale je převést na odpovídající typ delegáta nebo výraz. Když přiřazujete výrazu lambda proměnné typu delegáta nebo výraz, se zjistit kompilátoru a zkuste to převést výrazu lambda delegáta, který odpovídá podpis přiřazené k proměnné nebo výraz. Kompilátor musí pokusit zkontrolujte je věcí na pravé straně přiřazení shody typ na levé straně přiřazení. 

Oba konce přiřazení nelze informuje kompilátor podívejte se na objekt na druhé straně operátoru přiřazení a jestli odpovídá vlastního typu.

Můžete získat i další podrobnost, proč jazyka C# určuje tohoto chování načtením [v tomto článku](http://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (Stáhnout PDF)


