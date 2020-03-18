---
title: Použití implicitně zadávaných místních proměnných a polí ve výrazu dotazu - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: f4ff71fc4dc1a0b2affa1f032ab1d3d6bb04d297
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705558"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Použití implicitně zadávaných místních proměnných a polí ve výrazu dotazu (Průvodce programováním jazyka C#)
Implicitně zadané místní proměnné můžete použít vždy, když chcete, aby kompilátor určil typ místní proměnné. K ukládání anonymních typů, které se často používají ve výrazech dotazu, je nutné použít implicitně zadané místní proměnné. Následující příklady ilustrují volitelné i požadované použití implicitně zadaných místních proměnných v dotazech.  
  
 Implicitně zadané místní proměnné jsou deklarovány pomocí kontextového klíčového slova [var.](../../language-reference/keywords/var.md) Další informace naleznete [v tématu Implicitně zadané místní proměnné](./implicitly-typed-local-variables.md) a [implicitně zadaných polí](../arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje běžný scénář, `var` ve kterém je požadováno klíčové slovo: výraz dotazu, který vytváří posloupnost anonymních typů. V tomto scénáři musí být proměnná `foreach` dotazu i iterace `var` v příkazu implicitně zadána pomocí, protože nemáte přístup k názvu typu pro anonymní typ. Další informace o anonymních typech naleznete [v tématu Anonymous Types](./anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `var` klíčové slovo v situaci, která je `var` podobná, ale ve kterém je volitelné použití. Protože `student.LastName` je řetězec, spuštění dotazu vrátí posloupnost řetězců. Proto typ `queryID` by mohl být `System.Collections.Generic.IEnumerable<string>` deklarován jako místo `var`. Klíčové `var` slovo se používá pro pohodlí. V příkladu je iterace proměnné v příkazu `foreach` explicitně zadána jako `var`řetězec, ale místo toho může být deklarována pomocí . Vzhledem k tomu, že typ iterace `var` proměnné není anonymní typ, použití je možnost, nikoli požadavek. Pamatujte `var` si, že sama o sobě není typ, ale instrukce kompilátoru odvodit a přiřadit typ.  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Metody rozšíření](./extension-methods.md)
- [LINQ (dotaz integrovaný jazykem)](../../linq/index.md)
- [Var](../../language-reference/keywords/var.md)
- [LINQ v jazyce C#](../../linq/index.md)
