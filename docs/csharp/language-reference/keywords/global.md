---
title: globální kontextové klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: 79e0184f58ffc6232038abdd3d9f852147d5732c
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404285"
---
# <a name="global-c-reference"></a>global (Referenční dokumentace jazyka C#)

`global` Kontextové klíčové slovo, pokud jde o před [:: operator](../operators/namespace-alias-qualifer.md), odkazuje na globální obor názvů, což je výchozí obor názvů pro libovolném programu C# a v opačném případě nepojmenovaný. Další informace najdete v tématu [postupy: použití aliasu globálního Namespace](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `global` kontextové klíčové slovo určit, že třída `TestApp` je definována v globálním oboru názvů:

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a>Viz také:

[Obory názvů](../../programming-guide/namespaces/index.md)