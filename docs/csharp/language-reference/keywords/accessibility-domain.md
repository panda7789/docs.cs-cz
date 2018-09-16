---
title: Doména přístupnosti (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 01854b60fb58d4dcd0a217552f19d6c0cd32ec78
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664433"
---
# <a name="accessibility-domain-c-reference"></a>Doména přístupnosti (Referenční dokumentace jazyka C#)
Doména přístupnosti člena určuje, ve které části programu může být odkazováno člena. Pokud člen je vnořená v rámci jiného typu, jak je určen jeho doméně přístupnosti [úrovni přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md) z člena a doménou přístupnosti bezprostředně nadřazeného typu.  
  
 Doména přístupnosti člena typu nejvyšší úrovně je alespoň textem programu, který je deklarován v projektu. To znamená doména obsahuje všechny zdrojové soubory tohoto projektu. Doména přístupnosti vnořeného typu je alespoň textem programu typu, ve kterém je deklarována. To znamená že doménu je typu text, který zahrnuje všechny vnořené typy. Doména přístupnosti vnořeného typu nikdy překročí nadřazeného typu. Tyto koncepty je ukázán v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu obsahuje typu nejvyšší úrovně `T1`a dvě vnořené třídy, `M1` a `M2`. Třídy obsahovat pole, které mají různé deklarované přístupnosti. V `Main` metody komentář následuje každý příkaz označíte, tak doména přístupnosti člena každý člen. Všimněte si, že příkazy, které se pokouší odkazovat nepřístupní členové jsou označené jako komentář. Pokud chcete zobrazit chyby kompilátoru způsobené odkazuje na nepřístupný člena, odeberte komentáře jeden po druhém.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [Omezení používání úrovní přístupu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
- [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [public](../../../csharp/language-reference/keywords/public.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [protected](../../../csharp/language-reference/keywords/protected.md)  
- [internal](../../../csharp/language-reference/keywords/internal.md)
