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
ms.openlocfilehash: d7e0094d0f60aa201ae7229983f3e4b9764d2cbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="params-c-reference"></a>params (Referenční dokumentace jazyka C#)
Pomocí `params` – klíčové slovo, můžete zadat [parametru metody](../../../csharp/language-reference/keywords/method-parameters.md) , která má proměnný počet argumentů.  
  
 Můžete odeslat textový soubor s oddělovači seznam argumentů typ zadaný v deklaraci parametru nebo pole argumentů zadaného typu. Můžete také odeslat žádné argumenty. Pokud odesíláte bez argumentů, délka `params` seznamu je nulová.  
  
 Žádné další parametry jsou povoleny po `params` – klíčové slovo v deklaraci metody a jenom jedna `params` – klíčové slovo smí obsahovat deklaraci metody.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje různé způsoby, ve kterých lze odeslat argumenty `params` parametr.  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)
