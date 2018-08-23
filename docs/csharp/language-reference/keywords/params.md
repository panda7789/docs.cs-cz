---
title: params (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 692c2f61ae99f1c1c8e04a5a1bcad08814d286fe
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753978"
---
# <a name="params-c-reference"></a>params (Referenční dokumentace jazyka C#)
S použitím `params` – klíčové slovo, můžete zadat [parametr metody](../../../csharp/language-reference/keywords/method-parameters.md) , která přijímá proměnný počet argumentů.  
  
 Můžete odeslat čárkami oddělený seznam argumentů typ zadaný v deklaraci parametru nebo pole argumentů zadaného typu. Můžete také odeslat žádné argumenty. Pokud odešlete bez argumentů, délka `params` seznamu je nula.  
  
 Žádné další parametry nejsou povoleny po `params` – klíčové slovo v deklaraci metody a pouze jeden `params` – klíčové slovo je povolený v deklaraci metody.  
 
 Deklarovaný typ `params` parametr musí být jednorozměrné pole, jak ukazuje následující příklad. V opačném případě chybu kompilátoru [CS0225](../../../csharp/misc/cs0225.md) vyvolá.
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje různé způsoby, jimiž lze argumenty odesílat do `params` parametru.  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)
