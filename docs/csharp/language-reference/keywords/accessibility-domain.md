---
description: Doména usnadnění – Referenční dokumentace jazyka C#
title: Doména usnadnění – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 2cfc4cc72a79b33276b7d822a2b31eb518dcf784
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127058"
---
# <a name="accessibility-domain-c-reference"></a>Doména přístupnosti (Referenční dokumentace jazyka C#)
Doména přístupnosti člena určuje, ve kterých oddílech programu může být členem odkazováno. Pokud je člen vnořen v jiném typu, jeho doména přístupnosti je určena [úrovní přístupnosti](./accessibility-levels.md) člena a doménou přístupnosti bezprostředně nadřazeného typu.  
  
 Doména přístupnosti typu nejvyšší úrovně je alespoň text programu projektu, v němž je deklarována. To znamená, že doména zahrnuje všechny zdrojové soubory tohoto projektu. Doména přístupnosti vnořeného typu je alespoň text programu typu, ve kterém je deklarována. To znamená, že doména je text typu, který zahrnuje všechny vnořené typy. Doména přístupnosti vnořeného typu nikdy nepřekračuje typ nadřazeného typu. Tyto koncepty jsou znázorněné v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 Tento příklad obsahuje typ nejvyšší úrovně, `T1` , a dvě vnořené třídy `M1` a `M2` . Třídy obsahují pole, která mají různé deklarované přístupnosti. V `Main` metodě se komentář řídí jednotlivými příkazy k označení domény přístupnosti každého člena. Všimněte si, že příkazy, které se pokoušejí odkázat na nepřístupné členy, jsou zakomentovány. Pokud chcete zobrazit chyby kompilátoru způsobené odkazem na nepřístupného člena, odstraňte komentáře po jednom.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Modifikátory přístupu](./access-modifiers.md)
- [Úrovně přístupnosti](./accessibility-levels.md)
- [Omezení používání úrovní přístupu](./restrictions-on-using-accessibility-levels.md)
- [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
- [internal](./internal.md)
