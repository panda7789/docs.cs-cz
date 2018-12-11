---
title: '* Operator - C# odkaz'
ms.custom: seodec18
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 24ac4a99c48f1e8204b821bfbf5f7fbc0a2b2f1d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237347"
---
# <a name="-operator-c-reference"></a>* – operátor (Referenční dokumentace jazyka C#)
Operátor násobení (`*`) vypočítá součin z operandů. Všechny číselné typy obsahuje předdefinované operátory násobení.  

`*` slouží také jako operátor zrušení odkazu, který umožňuje čtení a zápis na ukazatel.
  
## <a name="remarks"></a>Poznámky  
 `*` Operátor se používá také, chcete-li deklarovat typy ukazatelů a ke zrušení ukazatele. Tento operátor jde použít jenom v kontextu unsafe, udávají použití [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo která vyžaduje [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.  Operátor zrušení odkazu se také označuje jako operátor dereference.  
  
 Uživatelem definované typy mohou přetížit binárního souboru `*` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)). Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.  
  
## <a name="example"></a>Příklad  
 [!code-csharp-interactive[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Nebezpečný kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
