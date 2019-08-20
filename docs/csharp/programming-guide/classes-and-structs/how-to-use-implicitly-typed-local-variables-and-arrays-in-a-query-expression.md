---
title: 'Postupy: Použití implicitního typu lokálních proměnných a polí ve výrazu dotazu – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: 5003e03b488a16d53e4e3d20a0b0b0e09630b46f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596690"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Postupy: Použití implicitního typu lokálních proměnných a polí ve výrazu dotazu (C# Průvodce programováním)
Můžete použít implicitně typované lokální proměnné, kdykoli chcete, aby kompilátor určil typ místní proměnné. Pro uložení anonymních typů, které se často používají ve výrazech dotazů, je nutné použít implicitní typové lokální proměnné. Následující příklady ilustrují volitelná i požadovaná použití implicitních typů místních proměnných v dotazech.  
  
 Implicitně typované lokální proměnné jsou deklarovány pomocí klíčového slova [var](../../language-reference/keywords/var.md) . Další informace naleznete v tématu [implicitně typované lokální proměnné](./implicitly-typed-local-variables.md) a [implicitně typované pole](../arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje běžný scénář, ve kterém `var` je klíčové slovo požadováno: výraz dotazu, který vytváří sekvenci anonymních typů. V tomto scénáři musí být proměnná dotazu a proměnná iterace v `foreach` příkazu implicitně typované pomocí `var` , protože nemáte přístup k názvu typu pro anonymní typ. Další informace o anonymních typech naleznete v tématu [anonymní typy](./anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `var` klíčové slovo v situaci, která je podobná, ale `var` použití je volitelné. Protože `student.LastName` je řetězec, provádění dotazu vrátí sekvenci řetězců. Proto lze typ `queryID` deklarace deklarovat jako `System.Collections.Generic.IEnumerable<string>` místo `var`. Klíčové `var` slovo se používá pro pohodlí. V příkladu je proměnná iterace v `foreach` příkazu explicitně typu jako řetězec, ale lze ji deklarovat pomocí. `var` Vzhledem k tomu, že typ proměnné iterace není anonymní typ, použití `var` je možnost, nikoli požadavek. Pamatujte na `var` to, že se nejedná o typ, ale instrukci kompilátoru pro odvození a přiřazení typu.  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Rozšiřující metody](./extension-methods.md)
- [LINQ (jazykově integrovaný dotaz)](../../linq/index.md)
- [var](../../language-reference/keywords/var.md)
- [Výrazy dotazů LINQ](../linq-query-expressions/index.md)
