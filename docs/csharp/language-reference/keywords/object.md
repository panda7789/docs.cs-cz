---
title: object (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: 67eaf7f1fd2f01e433395ed21701c3b7fad7c7b4
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199248"
---
# <a name="object-c-reference"></a>object (Referenční dokumentace jazyka C#)
`object` Typ je alias pro <xref:System.Object> v rozhraní .NET Framework. V systému unified typů jazyka C#, všechny typy, typy odkazů předdefinovaných a definovaný uživatelem, a typů hodnot, dědí přímo nebo nepřímo <xref:System.Object>. Můžete přiřadit proměnné typu hodnoty libovolného typu `object`. Když je proměnné typu hodnoty převeden na objekt, je označen jako *boxed*. Pokud proměnnou typu objektu je převeden na typ hodnoty, je označen jako *nezabalené*. Další informace najdete v tématu [zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázkový ukazuje, jak proměnné typu `object` může přijmout hodnoty libovolného typu dat a jak proměnné typu `object` můžete použít metody na <xref:System.Object> z rozhraní .NET Framework.  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
 [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)
