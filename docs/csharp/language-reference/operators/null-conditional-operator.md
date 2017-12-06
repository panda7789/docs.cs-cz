---
title: "?? Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6c2372380d8162d3e7760bba4a43cdb1c568bf5b
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2017
---
# <a name="-operator-c-reference"></a>?? Operátor (referenční dokumentace jazyka C#)
`??` Operátor se označuje jako operátor slučování hodnotu null.  Vrátí levý operand, pokud hodnota operandu není null; v opačném případě vrátí pravý operand.  
  
## <a name="remarks"></a>Poznámky  
 Typ povolené hodnoty null představuje hodnotu z domény typu, hodnotu lze také definovat (v takovém případě je hodnota null). Můžete použít `??` operátor je syntaktická expressiveness vrátit hodnotu odpovídající (pravém operand) Pokud má levý operand typu s povolenou hodnotou Null, jehož hodnota je null. Pokud se pokusíte přiřadit typ s možnou hodnotou Null hodnoty typu hodnot neumožňující hodnotu Null bez použití `??` operátor, vygeneruje chyby kompilace. Pokud používáte přetypování a typ s možnou hodnotou Null hodnoty je aktuálně definován `InvalidOperationException` dojde k výjimce.  
  
 Další informace najdete v tématu [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Výsledek?? operátor se nepovažuje za konstanta, i když jsou oba argumenty konstanty.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
 [Typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)  
 [Jaké přesně nemá 'Zrušit' znamená?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
