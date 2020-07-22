---
title: Jak vracet podmnožiny vlastností elementu v dotazu – Průvodce programováním v C#
description: Naučte se používat anonymní typ ve výrazu dotazu v jazyce C# pro vrácení některých vlastností každého zdrojového elementu.
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 882d94bc82527c14bd6c038f4bf574c2211b9089
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864368"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Vrácení podmnožin vlastností elementu v dotazu (Průvodce programováním v C#)
Použít anonymní typ ve výrazu dotazu, když platí obě tyto podmínky:  
  
- Chcete vrátit pouze některé vlastnosti každého zdrojového elementu.  
  
- Výsledky dotazu není nutné ukládat mimo rozsah metody, ve které je dotaz proveden.  
  
 Pokud chcete pouze vrátit jednu vlastnost nebo pole z každého elementu zdroje, můžete pouze použít operátor tečka v `select` klauzuli. Například pro vrácení pouze `ID` každého z nich `student` zapište `select` klauzuli následujícím způsobem:  
  
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
  
Chcete-li spustit tento kód, zkopírujte a vložte třídu do konzolové aplikace v jazyce C# s `using` direktivou pro System. Linq.
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Anonymní typy](./anonymous-types.md)
- [LINQ v jazyku C#](../../linq/index.md)
