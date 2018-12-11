---
title: 'Postupy: Vrácení podmnožin vlastností elementu v dotazu - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 27f0df14fef7c261828040d905c9f624f02eddfe
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243826"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Postupy: Vrácení podmnožin vlastností elementu v dotazu (C# Průvodce programováním v)
Použijte anonymního typu ve výrazu dotazu, pokud obě tyto podmínky:  
  
-   Chcete vrátit jenom některé vlastnosti jednotlivých zdrojových elementů.  
  
-   Není nutné pro ukládání výsledků dotazu nad rámec metoda spuštění dotazu.  
  
 Pokud chcete vrátit jednu vlastnost nebo pole z jednotlivých zdrojových elementů, pak tečka v můžete použít jenom `select` klauzuli. Například vrátit pouze `ID` jednotlivých `student`, zapisovat `select` klauzule následujícím způsobem:  
  
```  
select student.ID;  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít anonymní typ, který vrátí pouze podmnožinu vlastností jednotlivých zdrojových elementů, který odpovídá zadané podmínce.  
  
 [!code-csharp[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 Všimněte si, že používá anonymní typ zdrojového prvku názvy vlastností Pokud nejsou zadány žádné názvy. Chcete-li pojmenovat nové vlastnosti v anonymním typu, napište `select` příkaz následujícím způsobem:  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Pokud se to pokusíte v předchozím příkladu, pak bude `Console.WriteLine` musí také změňte příkaz:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Tento kód spustit, zkopírujte a vložte třídy v jazyce Visual C# projekt konzolové aplikace, který nebyl vytvořen v sadě Visual Studio. Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a bude mít odkaz na System.Core.dll a `using` směrnice pro System.Linq. Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.   
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
- [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)
