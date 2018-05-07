---
title: 'Postupy: Explicitní implementace členů dvou rozhraní (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c73089fdbf1350c1aff68ac3e8e78be00e21b931
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>Postupy: Explicitní implementace členů dvou rozhraní (Průvodce programováním v C#)
Explicitní [rozhraní](../../../csharp/language-reference/keywords/interface.md) implementace také umožňuje programátorů implementovat dvě rozhraní, které mají stejné názvy členů a poskytnout každý člen rozhraní samostatné implementace. Tento příklad zobrazí rozměry pole v metrika i anglické jednotky. Do pole [třída](../../../csharp/language-reference/keywords/class.md) implementuje dvě rozhraní IEnglishDimensions a IMetricDimensions, které představují různých měrná systémy. Obě rozhraní mít názvy identické členů, délku a šířku.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud chcete, aby měření výchozí v anglické jednotky, obvykle implementovat metody délku a šířku a explicitní implementace metody délku a šířku z rozhraní IMetricDimensions:  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 V takovém případě můžete používat anglické jednotky z instance třídy a přístup k metriky jednotky z instance rozhraní:  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)  
 [Postupy: Explicitní implementace členů rozhraní](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
