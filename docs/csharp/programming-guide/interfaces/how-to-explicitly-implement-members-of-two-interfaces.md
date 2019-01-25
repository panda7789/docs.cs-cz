---
title: 'Postupy: Explicitní implementace členů dvou rozhraní - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: b0725d63f77fbe0b9f3151c0b742777667e93311
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701245"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>Postupy: Explicitní implementace členů dvou rozhraní (C# Průvodce programováním v)
Explicitní [rozhraní](../../../csharp/language-reference/keywords/interface.md) implementace také umožňuje programátorovi, aby implementovat dvě rozhraní, které mají stejné názvy členů a poskytnout samostatné implementace každého člena rozhraní. Tento příklad zobrazuje rozměry pole v metriky a angličtině jednotky. Do pole [třídy](../../../csharp/language-reference/keywords/class.md) implementuje dvě rozhraní IEnglishDimensions a IMetricDimensions, které představují systémy různých měření. Obě rozhraní mají názvy členů identické, délku a šířku.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud chcete provést měření výchozí v angličtině jednotky, obvykle implementují metody délku a šířku a explicitní implementace metody délku a šířku IMetricDimensions rozhraní:  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 V takovém případě můžete přístup k anglické jednotky z instance třídy a přístup k metriky jednotky z instance rozhraní:  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)
- [Postupy: Explicitní implementace členů rozhraní](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
