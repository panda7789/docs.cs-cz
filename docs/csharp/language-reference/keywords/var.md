---
title: var (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e0df25eb46bb769214412646d0ac3a7a576b3b73
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="var-c-reference"></a>var (Referenční dokumentace jazyka C#)
Od verze Visual C# 3.0, proměnné, které jsou deklarované v oboru metoda může mít implicitní "typ" `var`. Implicitně typovaná místní proměnné je silného typu stejně, jako kdyby měl typ deklarovaný sami, ale kompilátor Určuje typ. Následujících dvou prohlášení `i` stejné funkce:  
  
```  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 Další informace najdete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [vztahy typů v operacích dotazu LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva výrazy dotazů. V prvním výrazu, použití `var` je povoleno, ale není vyžadována, protože typ výsledku dotazu může být výslovně uvedeny jako `IEnumerable<string>`. Ale v druhý výraz `var` umožňuje výsledek, který má být kolekce anonymní typy a název tohoto typu není přístupný kromě kompilátoru sám sebe. Použití `var` eliminuje požadavek na vytvoření nové třídy pro výsledek. Všimněte si, že v příkladu č. 2, `foreach` proměnné iterace `item` musí také být implicitně typované.  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
