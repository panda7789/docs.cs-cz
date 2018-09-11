---
title: globální kontextové klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: 837245e31a9a795aa2f13cfc6c33fefb6402801d
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44367350"
---
# <a name="global-c-reference"></a>global (Referenční dokumentace jazyka C#)

`global` Kontextové klíčové slovo, pokud jde o před [:: operator](../operators/namespace-alias-qualifer.md), odkazuje na globální obor názvů, což je výchozí obor názvů pro libovolném programu C# a v opačném případě nepojmenovaný. Další informace najdete v tématu [postupy: použití aliasu globálního Namespace](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `global` kontextové klíčové slovo určit, že třída `TestApp` je definována v globálním oboru názvů:

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a>Viz také:

- [Obory názvů](../../programming-guide/namespaces/index.md)