---
title: get - C# Reference
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 61d8c02aaf13f43ff8ea17c1e868ea9fd52893c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173624"
---
# <a name="get-c-reference"></a>get (Referenční dokumentace jazyka C#)

Klíčové `get` slovo definuje *přistupující* metodu ve vlastnosti nebo indexeru, který vrací hodnotu vlastnosti nebo prvek indexeru. Další informace naleznete [v tématu Vlastnosti](../../programming-guide/classes-and-structs/properties.md), [Automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md) a [indexery](../../programming-guide/indexers/index.md).  
  
Následující příklad definuje jak `get` a `set` a a přistupující objekt pro vlastnost s názvem `Seconds`. Používá soukromé pole `_seconds` s názvem zpět hodnotu vlastnosti.  

 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
Často přistupující `get` ho se skládá z jednoho příkazu, který vrátí hodnotu, jako tomu bylo v předchozím příkladu. Počínaje C# 7.0, můžete `get` implementovat přistupující objekt jako člen s výrazem. Následující příklad implementuje `get` i `set` a přistupující ho jako členy s výrazem.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]

Pro jednoduché případy, ve `get` kterých vlastnosti a `set` přistupující objekty provádět žádné jiné operace než nastavení nebo načítání hodnoty v soukromém záložním poli, můžete využít podpory kompilátoru Jazyka C# pro automaticky implementované vlastnosti. Následující příklad implementuje `Hours` jako automaticky implementované vlastnosti.
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](./index.md)
- [Vlastnosti](../../programming-guide/classes-and-structs/properties.md)
