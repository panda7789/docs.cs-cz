---
title: ?? – Operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 03d81d4216dabce2ea75b9fdcf6ef0971cc32490
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388856"
---
# <a name="-operator-c-reference"></a>?? – Operátor (referenční dokumentace jazyka C#)
`??` Operátor se nazývá operátoru nulového sjednocení.  Vrátí levý operand, pokud hodnota operandu není null; v opačném případě vrátí pravý operand.  
  
## <a name="remarks"></a>Poznámky  
 Typ povolené hodnoty null představuje hodnotu z domény typu, hodnotu lze také definovat (v takovém případě je hodnota null). Můžete použít `??` syntaktické expresivity obsluhy se vraťte na příslušnou hodnotu (pravý operand) Pokud levý operand má typ s možnou hodnotou Null, jehož hodnota je null. Pokud se pokusíte přiřadit typ s možnou hodnotou Null typu hodnotu Null bez použití `??` operátoru, vygeneruje chybu v době kompilace. Pokud použijete přetypování a typ s možnou hodnotou Null není aktuálně definován `InvalidOperationException` , bude vyvolána výjimka.  
  
 Další informace najdete v tématu [typy připouštějící hodnotu Null](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Výsledek?? operátor není považována za konstantu, i když jsou oba argumenty konstanty.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
- [Typy s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)  
- [Co přesně se pojem "zrušeno" znamenají?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
