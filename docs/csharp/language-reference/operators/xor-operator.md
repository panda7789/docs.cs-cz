---
title: ^ – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: f6f09f197502af1bc38bcdef97dd1db0ad9c7c08
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236944"
---
# <a name="-operator-c-reference"></a>^ – operátor (Referenční dokumentace jazyka C#)
Binární `^` pro integrální typy jsou předdefinované operátory a `bool`. Pro integrální typy `^` vypočítá bitový exkluzivní operátor OR z operandů. Pro `bool` operandy, `^` vypočítá exkluzivní logické- nebo z operandů; to znamená, výsledek je `true` pouze v případě právě jeden z operandů je `true`.  
  
## <a name="remarks"></a>Poznámky  
 Lze přetěžovat uživatelsky definované typy `^` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)). Operace interních typů jsou obecně povoleny na výčet.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 Výpočet `0xf8 ^ 0x3f` v předchozím příkladu provádí logické bitové exkluzivní disjunkce OR následující dvě binárních hodnot, které odpovídají šestnáctkových hodnot F8 a 3F:  
  
 `1111 1000`  
  
 `0011 1111`  
  
 Výsledek exkluzivní disjunkce OR je `1100 0111`, který je kompatibilní s C7 v šestnáctkové soustavě.  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
