---
title: 'Postupy: Vrácení podmnožiny vlastností elementu v dotazu – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 2c9fea2189819058187020c2e67b8826659fbed4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205443"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Postupy: Vrácení podmnožiny vlastností elementu v dotazu (C# Průvodce programováním)
Použít anonymní typ ve výrazu dotazu, když platí obě tyto podmínky:  
  
- Chcete vrátit pouze některé vlastnosti každého zdrojového elementu.  
  
- Výsledky dotazu není nutné ukládat mimo rozsah metody, ve které je dotaz proveden.  
  
 Pokud chcete pouze vrátit jednu vlastnost nebo pole z každého elementu zdroje, můžete pouze použít operátor tečka v `select` klauzuli. Například pro vrácení pouze `ID` každého z nich `student`zapište `select` klauzuli následujícím způsobem:  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít anonymní typ pro vrácení pouze podmnožiny vlastností každého zdrojového prvku, který odpovídá zadané podmínce.  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 Všimněte si, že anonymní typ používá názvy zdrojového elementu pro jeho vlastnosti, pokud nejsou zadány žádné názvy. Chcete-li zadat nové názvy vlastností v anonymním typu, zapište `select` příkaz následujícím způsobem:  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Pokud to zkusíte v předchozím příkladu, `Console.WriteLine` příkaz se musí také změnit:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
Chcete-li spustit tento kód, zkopírujte a vložte třídu do C# konzolové aplikace s `using` direktivou pro System. Linq.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Anonymní typy](./anonymous-types.md)
- [Výrazy dotazů LINQ](../linq-query-expressions/index.md)
