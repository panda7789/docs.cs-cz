---
title: 'Postupy: Identifikace typu s povolenou hodnotou Null (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: f3ac4ebd77fc92a133eb326919d5ba55264ced97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333180"
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
 [Typy s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md)  
 [Zabalení typů s povolenou hodnotou Null](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)
