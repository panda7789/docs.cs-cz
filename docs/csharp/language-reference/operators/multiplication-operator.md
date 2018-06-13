---
title: '* Operátor (referenční dokumentace jazyka C#)'
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 6c5d4de587b67e5ade158c163a87e8dea6bece5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275838"
---
# <a name="-operator-c-reference"></a>* – operátor (Referenční dokumentace jazyka C#)
Operátor násobení (`*`) vypočítá produktu jejími operandy. Všechny číselné typy obsahuje předdefinované operátory násobení.  

`*` slouží také jako dereference operátor, který umožňuje čtení a zápis do ukazatel.
  
## <a name="remarks"></a>Poznámky  
 `*` Operátor slouží také k deklaraci typy ukazatelů a dereference ukazatele. Tento operátor lze použít pouze v kontextu unsafe, odlišené použití [unsafe](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo a vyžadující [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.  Operátor dereference se taky říká deferenční operátor.  
  
 Uživatelem definované typy může přetížit binárního souboru `*` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)). Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Nebezpečný kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
