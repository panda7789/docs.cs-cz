---
title: Použití implicitního typu lokálních proměnných a polí ve výrazu dotazu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: c6022aaa4c37bc0c11c09375d3637d8287fce61a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970426"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Použití implicitního typu lokálních proměnných a polí ve výrazu dotazu (C# Průvodce programováním)
Můžete použít implicitně typované lokální proměnné, kdykoli chcete, aby kompilátor určil typ místní proměnné. Pro uložení anonymních typů, které se často používají ve výrazech dotazů, je nutné použít implicitní typové lokální proměnné. Následující příklady ilustrují volitelná i požadovaná použití implicitních typů místních proměnných v dotazech.  
  
 Implicitně typované lokální proměnné jsou deklarovány pomocí klíčového slova [var](../../language-reference/keywords/var.md) . Další informace naleznete v tématu [implicitně typované lokální proměnné](./implicitly-typed-local-variables.md) a [implicitně typované pole](../arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje běžný scénář, ve kterém je klíčové slovo `var` požadováno: výraz dotazu, který vytváří sekvenci anonymních typů. V tomto scénáři musí být proměnná dotazu a proměnná iterace v příkazu `foreach` implicitně typované pomocí `var`, protože nemáte přístup k názvu typu pro anonymní typ. Další informace o anonymních typech naleznete v tématu [anonymní typy](./anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá klíčové slovo `var` v situaci, která je podobná, ale použití `var` je volitelné. Protože `student.LastName` je řetězec, provádění dotazu vrátí sekvenci řetězců. Proto by typ `queryID` mohl být deklarován jako `System.Collections.Generic.IEnumerable<string>` namísto `var`. Klíčové slovo `var` se používá pro pohodlí. V příkladu je proměnná iterace v příkazu `foreach` explicitně zadána jako řetězec, ale lze ji deklarovat pomocí `var`. Vzhledem k tomu, že typ proměnné iterace není anonymní typ, použití `var` je možnost, nikoli požadavek. Nezapomeňte, `var` sám o sobě není typu, ale instrukci kompilátoru pro odvození a přiřazení typu.  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Rozšiřující metody](./extension-methods.md)
- [LINQ (jazykově integrovaný dotaz)](../../linq/index.md)
- [var](../../language-reference/keywords/var.md)
- [LINQ v jazyce C#](../../linq/index.md)
