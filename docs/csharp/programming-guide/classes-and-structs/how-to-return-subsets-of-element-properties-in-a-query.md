---
title: Vrácení podmnožiny vlastností elementu v dotazu – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 27a2626fc46307a7195040adf746d8d8757d2f82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714860"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Vrácení podmnožiny vlastností elementu v dotazu (Průvodce programováním jazyka C#)
Pokud platí obě tyto podmínky, použijte ve výrazu dotazu anonymní typ:  
  
- Chcete vrátit pouze některé vlastnosti každého zdrojového prvku.  
  
- Není třeba ukládat výsledky dotazu mimo rozsah metody, ve kterém je dotaz spuštěn.  
  
 Pokud chcete vrátit pouze jednu vlastnost nebo pole z každého zdrojového prvku, `select` můžete použít operátor tečka v klauzuli. Chcete-li například `ID` vrátit `student`pouze každý `select` z nich , napište klauzuli takto:  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí anonymního typu vrátit pouze podmnožinu vlastností každého zdrojového prvku, který odpovídá zadané podmínce.  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 Všimněte si, že anonymní typ používá názvy zdrojového prvku pro jeho vlastnosti, pokud nejsou zadány žádné názvy. Chcete-li vlastnostem anonymního typu přidělit `select` nové názvy, napište příkaz takto:  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Pokud se pokusíte v předchozím `Console.WriteLine` příkladu, pak příkaz musí také změnit:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
Chcete-li spustit tento kód, zkopírujte a vložte `using` třídu do aplikace konzoly Jazyka C# se směrnicí pro System.Linq.
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Anonymní typy](./anonymous-types.md)
- [LINQ v jazyce C#](../../linq/index.md)
