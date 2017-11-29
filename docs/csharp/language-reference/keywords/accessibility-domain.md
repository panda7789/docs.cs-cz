---
title: "Doména přístupnosti (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 127bacda4bf8363fccff3dd3ef6770ad50984cfb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-domain-c-reference"></a>Doména přístupnosti (Referenční dokumentace jazyka C#)
Doména přístupnosti člena určuje, ve které části program může být odkazováno členem. Pokud člen vnořen v rámci jiného typu, jak je určen jeho doména přístupnosti [úrovni přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md) člena a doména přístupnosti okamžitě nadřazeného typu.  
  
 Doména přístupnosti typu nejvyšší úrovně je alespoň text projekt, který je deklarován v programu. To znamená doména obsahuje všechny zdrojových souborů tohoto projektu. Doména přístupnosti vnořeného typu je alespoň text program typu, ve kterém je deklarovaná. To znamená že doménu je typu text, který obsahuje všechny vnořené typy. Doména přístupnosti vnořeného typu nikdy přesahuje nadřazeného typu. Tyto koncepty jsou ukázáno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 Tento příklad obsahuje typu nejvyšší úrovně `T1`a dva vnořené třídy `M1` a `M2`. Třídy obsahovat pole, které mají různé deklarované přístupnosti. V `Main` metody komentář následuje každý příkaz k označení doména přístupnosti u každého člena. Všimněte si, že jsou komentované příkazy, které se pokusí o odkazovat nepřístupný členy. Pokud chcete zobrazit chyby kompilátoru způsobené odkazování na člena nedostupné, odeberte komentáře jeden najednou.  
  
 [!code-csharp[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Omezení používání úrovní přístupu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [veřejné](../../../csharp/language-reference/keywords/public.md)  
 [privátní](../../../csharp/language-reference/keywords/private.md)  
 [chráněný](../../../csharp/language-reference/keywords/protected.md)  
 [interní](../../../csharp/language-reference/keywords/internal.md)
