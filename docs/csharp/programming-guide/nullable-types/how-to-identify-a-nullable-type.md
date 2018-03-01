---
title: "Postupy: Identifikace typu s povolenou hodnotou Null (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 610ed18308df02c5632361cd09ef94330dea598b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>Postupy: Identifikace typu s povolenou hodnotou Null (Průvodce programováním v C#)
Můžete použít jazyka C# [typeof](../../../csharp/language-reference/keywords/typeof.md) operátor k vytvoření <xref:System.Type> objekt, který představuje typ s možnou hodnotou NULL:  
  
```  
System.Type type = typeof(int?);  
```  
  
 Můžete také použít třídy a metody <xref:System.Reflection> obor názvů pro generování <xref:System.Type> objekty, které reprezentují typy s možnou hodnotou Null. Ale pokud pokusí získat informace o typu ze s možnou hodnotou Null proměnné za běhu pomocí <xref:System.Object.GetType%2A> metoda nebo `is` operátor, výsledkem je, <xref:System.Type> typ objektu, který představuje základní typ, není Nullable sám sebe.  
  
 Volání metody `GetType` v Nullable typ způsobí, že zabalení operaci provést, když je typ implicitně převést na <xref:System.Object>. Proto <xref:System.Object.GetType%2A> vždy vrátí hodnotu <xref:System.Type> objekt, který představuje základní typ, není typ s možnou hodnotou Null.  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 C# [je](../../../csharp/language-reference/keywords/is.md) operátor taky pracuje Nullable podkladovým typem. Proto nelze použít `is` k určení, zda je proměnná typu s povolenou hodnotou Null. Následující příklad ukazuje, že `is` operátor považuje Nullable\<int > proměnné jako typ int.  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## <a name="example"></a>Příklad  
 Pomocí následujícího kódu rozhodnout, jestli <xref:System.Type> objekt představuje typ s možnou hodnotou Null. Mějte na paměti, že tento kód vždy vrátí hodnotu false, pokud `Type` volání byl vrácen objekt <xref:System.Object.GetType%2A>, jak je popsáno výše v tomto tématu.  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## <a name="see-also"></a>Viz také  
 [Typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)  
 [Zabalení typů s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)
