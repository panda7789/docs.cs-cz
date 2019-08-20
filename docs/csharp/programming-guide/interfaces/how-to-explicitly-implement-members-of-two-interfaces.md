---
title: 'Postupy: Explicitní implementace členů dvou rozhraní – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 1d4dd0485be1d859e3e9594ab1558a907b8f1f7a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589192"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>Postupy: Explicitní implementace členů dvou rozhraní (C# Průvodce programováním)
Explicitní implementace [rozhraní](../../language-reference/keywords/interface.md) také umožňuje programátorovi implementovat dvě rozhraní, která mají stejné názvy členů a dávají každému členu rozhraní samostatnou implementaci. Tento příklad zobrazuje rozměry pole v jednotkách metriky a angličtiny. [Třída](../../language-reference/keywords/class.md) box implementuje dvě rozhraní IEnglishDimensions a IMetricDimensions, která představuje různé měřicí systémy. Obě rozhraní mají stejné názvy členů, délku a šířku.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Pokud chcete nastavit výchozí míry v anglických jednotkách, implementujte její délku a šířku obvyklým způsobem a explicitně Implementujte metody délky a šířky z rozhraní IMetricDimensions:  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 V tomto případě máte přístup k anglickou jednotkám z instance třídy a získáte přístup ke jednotkám metrik z instance rozhraní:  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](../classes-and-structs/index.md)
- [Rozhraní](./index.md)
- [Postupy: Explicitní implementace členů rozhraní](./how-to-explicitly-implement-interface-members.md)
