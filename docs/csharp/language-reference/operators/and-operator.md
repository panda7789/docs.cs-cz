---
title: '&amp; – Operátor (referenční dokumentace jazyka C#)'
ms.date: 04/04/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: b257c7d41618464e26ab3b54bcfb1f1e2c2e420e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467371"
---
# <a name="amp-operator-c-reference"></a>&amp; – Operátor (referenční dokumentace jazyka C#)
`&` Operátor může fungovat jako unární nebo binární operátor.  
  
## <a name="remarks"></a>Poznámky  
 Unární `&` operátor vrátí adresu svého operandu (vyžaduje [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md) kontext).  
  
 Binární `&` pro integrální typy jsou předdefinované operátory a `bool`. Pro integrální typy & vypočítá logické bitové operace AND operandů. Pro `bool` operandy & logický výpočetní prostředí a jeho operandy; to znamená, výsledek je `true` pouze v případě jsou oba operandy jeho `true`.  
  
 Binární soubor `&` operátor vyhodnotí oba operandy bez ohledu na to první hodnotu, oproti k [podmiňovací operátor AND](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`. Příklad:  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 Uživatelem definované typy mohou přetížit binárního souboru `&` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)). Operace interních typů jsou obecně povoleny na výčet. Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
