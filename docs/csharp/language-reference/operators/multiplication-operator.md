---
title: "* Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 64c32def0935f4347f9aaccc2865b9cd33dd8a70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>* – operátor (Referenční dokumentace jazyka C#)
Operátor násobení (`*`), která vypočítá produktu jejími operandy.  Navíc dereference operátor, který umožňuje čtení a zápis do ukazatel.  
  
## <a name="remarks"></a>Poznámky  
 Všechny číselné typy obsahuje předdefinované operátory násobení.  
  
 `*` Operátor slouží také k deklaraci typy ukazatelů a dereference ukazatele. Tento operátor lze použít pouze v kontextu unsafe, odlišené použití [unsafe](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo a vyžadující [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.  Operátor dereference se taky říká deferenční operátor.  
  
 Uživatelem definované typy může přetížit binárního souboru `*` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)). Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
