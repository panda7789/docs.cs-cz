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
ms.openlocfilehash: aee80b3262ccd9432d7c311dddec47185b66d05f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46695407"
---
# <a name="as-c-reference"></a>as (Referenční dokumentace jazyka C#)
Můžete použít `as` operátor pro provádění určitých typů převody mezi typy kompatibilní odkazů nebo [typy připouštějící hodnotu Null](../../../csharp/programming-guide/nullable-types/index.md). Následující kód ukazuje příklad.  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]
  
## <a name="remarks"></a>Poznámky  
 `as` Operátor je jako operace přetypování. Nicméně, pokud převod není možný, `as` vrátí `null` namísto vyvolání výjimky. Vezměte v úvahu v následujícím příkladu:  
  
```csharp  
expression as type  
```  
  
 Je ekvivalentem následujícího výrazu s výjimkou, že kód `expression` proměnná je vyhodnocen pouze jednou.  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 Všimněte si, `as` operátor provádí pouze převody odkazů, s možnou hodnotou Null převody a převody zabalení. `as` Operátor nelze provádět jiné převody, jako je například uživatelem definované převody, které by místo toho provádět pomocí výrazy přetypování.  
  
## <a name="example"></a>Příklad  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [is](../../../csharp/language-reference/keywords/is.md)  
- [?: – operátor](../../../csharp/language-reference/operators/conditional-operator.md)  
- [Klíčová slova operátorů](../../../csharp/language-reference/keywords/operator-keywords.md)
