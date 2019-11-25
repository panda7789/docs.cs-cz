---
title: Jak vracet podmnožiny vlastností elementu v dotazu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 1266b866d671854c787d907b91f654c128681de9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970460"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Vrácení podmnožiny vlastností elementu v dotazu (C# Průvodce programováním)
Použít anonymní typ ve výrazu dotazu, když platí obě tyto podmínky:  
  
- Chcete vrátit pouze některé vlastnosti každého zdrojového elementu.  
  
- Výsledky dotazu není nutné ukládat mimo rozsah metody, ve které je dotaz proveden.  
  
 Pokud chcete pouze vrátit jednu vlastnost nebo pole z každého elementu zdroje, můžete pouze použít operátor tečka v klauzuli `select`. Například chcete-li vrátit pouze `ID` každého `student`, napište klauzuli `select` následujícím způsobem:  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít anonymní typ pro vrácení pouze podmnožiny vlastností každého zdrojového prvku, který odpovídá zadané podmínce.  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 Všimněte si, že anonymní typ používá názvy zdrojového elementu pro jeho vlastnosti, pokud nejsou zadány žádné názvy. Chcete-li zadat nové názvy vlastností v anonymním typu, zapište příkaz `select` následujícím způsobem:  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Pokud to zkusíte v předchozím příkladu, musí se také změnit příkaz `Console.WriteLine`:  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
Chcete-li spustit tento kód, zkopírujte a vložte třídu do C# konzolové aplikace s direktivou `using` pro třídu System. Linq.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Anonymní typy](./anonymous-types.md)
- [LINQ v jazyce C#](../../linq/index.md)
