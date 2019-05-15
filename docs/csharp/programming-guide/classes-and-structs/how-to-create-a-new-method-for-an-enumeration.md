---
title: 'Postupy: Vytvoření nové metody pro výčet - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: 2ca388d19c0e4e1b098076caa5baa0a83cc0dd4c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585875"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>Postupy: Vytvoření nové metody pro výčet (C# Průvodce programováním v)
Rozšiřující metody slouží k přidání funkce specifické pro typ konkrétní výčtu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Grades` výčet představuje možné písmeno tříd, které student může zobrazit ve třídě. Rozšiřující metody s názvem `Passing` se přidá do `Grades` tak, aby každá instance daného typu nyní "ví", zda představuje na podnikové úrovni předávání nebo ne.  
  
 [!code-csharp[csProgGuideExtensionMethods#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#2)]  
  
 Všimněte si, `Extensions` třída také obsahuje statickou proměnnou, která se dynamicky aktualizuje a že návratová hodnota metody rozšíření odpovídá aktuální hodnotě proměnné. Tento příklad ukazuje, že na pozadí jsou rozšiřující metody vyvolány přímo u statické třídy, ve kterém jsou definovány.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
