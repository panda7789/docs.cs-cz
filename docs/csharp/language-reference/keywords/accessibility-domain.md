---
title: Přístup k doméně C# – referenční informace
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 814aa8d3965674abe8bdb60b738cbeff93701ceb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606136"
---
# <a name="accessibility-domain-c-reference"></a>Doména přístupnosti (Referenční dokumentace jazyka C#)
Doména přístupnosti člena určuje, ve kterých oddílech programu může být členem odkazováno. Pokud je člen vnořen v jiném typu, jeho doména přístupnosti je určena [úrovní](./accessibility-levels.md) přístupnosti člena a doménou přístupnosti bezprostředně nadřazeného typu.  
  
 Doména přístupnosti typu nejvyšší úrovně je alespoň text programu projektu, v němž je deklarována. To znamená, že doména zahrnuje všechny zdrojové soubory tohoto projektu. Doména přístupnosti vnořeného typu je alespoň text programu typu, ve kterém je deklarována. To znamená, že doména je text typu, který zahrnuje všechny vnořené typy. Doména přístupnosti vnořeného typu nikdy nepřekračuje typ nadřazeného typu. Tyto koncepty jsou znázorněné v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 Tento příklad obsahuje typ nejvyšší úrovně, `T1`, a dvě vnořené `M1` třídy a `M2`. Třídy obsahují pole, která mají různé deklarované přístupnosti. `Main` V metodě se komentář řídí jednotlivými příkazy k označení domény přístupnosti každého člena. Všimněte si, že příkazy, které se pokoušejí odkázat na nepřístupné členy, jsou zakomentovány. Pokud chcete zobrazit chyby kompilátoru způsobené odkazem na nepřístupného člena, odstraňte komentáře po jednom.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Modifikátory přístupu](./access-modifiers.md)
- [Úrovně přístupnosti](./accessibility-levels.md)
- [Omezení používání úrovní přístupu](./restrictions-on-using-accessibility-levels.md)
- [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
- [internal](./internal.md)
