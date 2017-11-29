---
title: "object (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords: object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0fcced75d3a86fd700e642e48b7e325e554cae53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="object-c-reference"></a>object (Referenční dokumentace jazyka C#)
`object` Typ je alias <xref:System.Object> v rozhraní .NET Framework. V systému jednotná typu jazyka C#, všechny typy, odkaz na předdefinované a uživatelem definované typy a typy hodnot, dědí přímo nebo nepřímo <xref:System.Object>. Můžete přiřadit hodnoty libovolného typu proměnné typu `object`. Když je proměnná typu hodnoty převést na objekt, je označováno jako *do pole*. Pokud proměnná typu objektu je převést na typ hodnoty, je označováno jako *nezabalený*. Další informace najdete v tématu [zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázkové ukazuje, jak proměnné typu `object` může přijmout hodnoty libovolného typu data a jak proměnné typu `object` můžete použít metody na <xref:System.Object> z rozhraní .NET Framework.  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
 [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)
