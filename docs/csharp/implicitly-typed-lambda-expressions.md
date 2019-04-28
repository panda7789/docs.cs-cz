---
title: Implicitně typovaná lambda výrazy
description: Zjistěte, proč nelze použít deklaraci proměnné implicitně typované k deklarování výrazů lambda.
ms.date: 06/20/2016
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: 9b798f40676afaad2075806d6dc512f279bc7065
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672078"
---
# <a name="implicitly-typed-lambda-expressions"></a>Implicitně typovaná lambda výrazy

Implicitně typovaná deklarace proměnné nelze použít k deklarování výrazů lambda.
Vytvoří problém cyklické logiku pro kompilátor. `var` Deklarace instruuje kompilátor, aby zjistit typ proměnné z typu výrazu na pravé straně operátoru přiřazení. Výraz lambda nemá typ času kompilace, ale lze převést na odpovídající typ delegáta nebo výraz. Pokud je výraz lambda přiřadit proměnné typu delegát nebo výraz, dáte kompilátoru vyzkoušet a převést výraz lambda výraz nebo delegát, který se shoduje se signaturou přiřazená k proměnné. Kompilátor musí pokusí provést je na pravé straně přiřazení shoda typu přiřazení na levé straně. 

Obě strany přiřazení nelze sděluje kompilátoru, aby podívat se na objekt na druhé straně operátoru přiřazení a jestli Moje typ odpovídá.

Získáte i další podrobnosti o tom, proč jazyka C# určuje chování načtením [v tomto článku](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (Stáhnout soubor PDF)
