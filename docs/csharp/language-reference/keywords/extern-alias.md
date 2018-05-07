---
title: externí alias (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: a2803d09ee64af854cad352f6a158fb84bb6d410
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova oboru názvů](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [:: – operátor](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [/ Reference (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
