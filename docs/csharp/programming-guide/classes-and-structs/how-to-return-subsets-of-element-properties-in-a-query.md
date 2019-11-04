---
title: 'Postupy: vrácení podmnožiny vlastností elementu v dotazu – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 196383731507137bf4309d38d27b36f29b23a06c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419305"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a>Postupy: Vrácení podmnožin vlastností elementu v dotazu (Průvodce programováním v C#)
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
