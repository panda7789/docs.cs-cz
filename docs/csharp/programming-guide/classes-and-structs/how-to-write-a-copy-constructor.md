---
title: 'Postupy: Zápis kopírovacího konstruktoru - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 169bdfc53d0c30ffc14e5a9525920679a94fbf23
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56982138"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Postupy: Zápis kopírovacího konstruktoru (C# Průvodce programováním v)
C# neposkytuje konstruktor kopírování pro objekty, ale můžete jej napsat sami.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Person` [třídy](../../../csharp/language-reference/keywords/class.md) definuje kopírovacího konstruktora představujícího společně s argumentem instanci `Person`. Hodnoty vlastností argumentu jsou přiřazeny novým vlastnostem nové instance `Person`. Kód obsahuje alternativní kopírovací konstruktor, který odešle `Name` a `Age` vlastnosti instance, kterou chcete zkopírovat do konstruktoru instance třídy.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ICloneable>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)
