---
title: Jak explicitně implementovat členy dvou rozhraní - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c7adc08f62a7f8a14b8e10f8b5ecdd6e37db811d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75701235"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>Jak explicitně implementovat členy dvou rozhraní (C# Programming Guide)
Explicitní implementace [rozhraní](../../language-reference/keywords/interface.md) také umožňuje programátorovi implementovat dvě rozhraní, která mají stejné názvy členů a poskytují každému členovi rozhraní samostatnou implementaci. Tento příklad zobrazuje rozměry pole v metrických i anglických jednotkách. Třída [Box](../../language-reference/keywords/class.md) implementuje dvě rozhraní IEnglishDimensions a IMetricDimensions, které představují různé systémy měření. Obě rozhraní mají identické názvy členů, Délka a Šířka.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud chcete provést výchozí měření v anglických jednotkách, implementujte metody Délka a šířka normálně a explicitně implementujte metody Length and Width z rozhraní IMetricDimensions:  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 V takovém případě můžete přistupovat k anglickým jednotkám z instance třídy a přistupovat k jednotkám metrik y z instance rozhraní:  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](../classes-and-structs/index.md)
- [Rozhraní](./index.md)
- [Jak explicitně implementovat členy rozhraní](./how-to-explicitly-implement-interface-members.md)
