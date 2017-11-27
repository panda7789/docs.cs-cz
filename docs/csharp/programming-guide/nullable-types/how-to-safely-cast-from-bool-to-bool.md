---
title: "Postupy: Bezpečné přetypování z typu bool? na bool (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a6fa65c15bb5f1da9960dbc17bd25b4087ab862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a>Postupy: Bezpečné přetypování z typu bool? na bool (Průvodce programováním v C#)
`bool?` Typ s možnou hodnotou Null může obsahovat tři různé hodnoty: `true`, `false`, a `null`. Proto `bool?` typ nelze použít v podmíněné příkazy, jako s `if`, `for`, nebo `while`. Chyba kompilátoru způsobí například následující kód.  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 To není povoleno, protože je při tom nejasné co `null` znamená v kontextu podmíněného. Použít `bool?` v podmíněného výrazu, nejprve zkontrolujte jeho <xref:System.Nullable%601.HasValue%2A> vlastnost zajistit, že její hodnota není `null`a pak vysílat `bool`. Další informace najdete v tématu [bool](../../../csharp/language-reference/keywords/bool.md). Pokud provádíte přetypování na `bool?` s hodnotou `null`, <xref:System.InvalidOperationException> bude vyvolána v podmíněného testu. Následující příklad ukazuje jeden ze způsobů bezpečné přetypování z `bool?` k `bool`:  
  
## <a name="example"></a>Příklad  
  
```csharp  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Literálová klíčová slova](../../../csharp/language-reference/keywords/literal-keywords.md)  
 [Typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)  
 [?? Operátor](../../../csharp/language-reference/operators/null-conditional-operator.md)
