---
title: "params (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e66cfc8e7b131a4443ee227df5e39c7e3b775324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)
