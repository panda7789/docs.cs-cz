---
title: externí alias (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4e995586c08659853538726a12679770cd1ada37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="extern-alias-c-reference"></a>externí alias (Referenční dokumentace jazyka C#)
Máte tak, aby odkazovaly dvě verze sestavení, které mají stejné názvy plně kvalifikovaný typ. Například budete muset použít dvě nebo více verzí sestavení, ve stejné aplikaci. Pomocí externí sestavení alias obory názvů v každé sestavení může zalomit uvnitř obory názvů kořenové úrovně s názvem podle alias, který umožňuje jim použít ve stejném souboru.  
  
> [!NOTE]
>  [Extern](../../../csharp/language-reference/keywords/extern.md) – klíčové slovo slouží také jako metoda modifikátor, deklarace metodu napsané v nespravovaném kódu.  
  
 Chcete-li dvou sestavení se stejnými názvy plně kvalifikovaný typ, musí být zadán alias v příkazovém řádku následujícím způsobem:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Tím se vytvoří externí aliasy `GridV1` a `GridV2`. Pokud chcete použít tyto aliasy z v rámci programu, odkaz je pomocí `extern` – klíčové slovo. Příklad:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Každý extern alias deklarace zavádí další kořenové úrovni oboru názvů, který je paralelní (ale není v rámci) globální obor názvů. Proto typů z každé sestavení lze odkazovat bez nejednoznačnosti pomocí jejich plně kvalifikovaný název root v příslušné alias oboru názvů.  
  
 V předchozím příkladu `GridV1::Grid` by být z ovládacího prvku mřížky `grid.dll`, a `GridV2::Grid` by být z ovládacího prvku mřížky `grid20.dll`.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Namespace klíčová slova](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [:: – Operátor](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [/ Reference (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
