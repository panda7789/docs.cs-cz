---
title: as (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: 092c30a858df7baeb35bdf28bae53802fb0916d4
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172016"
---
# <a name="as-c-reference"></a>as (Referenční dokumentace jazyka C#)
Můžete použít `as` operátor provést určité typy převody mezi kompatibilní odkazové typy nebo [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md). Následující kód ukazuje příklad.  
  
 [!code-csharp[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a>Poznámky  
 `as` Operátor je jako operaci přetypování. Nicméně, pokud není možné, převod `as` vrátí `null` místo vyvolání k výjimce. Podívejte se na následující příklad:  
  
```csharp  
expression as type  
```  
  
 Kód je ekvivalentní výrazu následující vyjma toho, že `expression` proměnná vyhodnotí pouze jednou.  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 Všimněte si, že `as` operátor provádí pouze převody odkazů, s možnou hodnotou Null převody a zabalení převody. `as` Operátor nelze provádět jiné převody, jako je například uživatelem definované převody, které by měli místo toho provádět pomocí výrazů přetypování.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [is](../../../csharp/language-reference/keywords/is.md)  
 [?: – operátor](../../../csharp/language-reference/operators/conditional-operator.md)  
 [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)
