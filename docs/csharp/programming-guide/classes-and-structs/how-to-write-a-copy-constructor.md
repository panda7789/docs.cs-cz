---
title: 'Postupy: Zápis kopírovacího konstruktoru (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: d6ecfc3659dcf533db0f4e7b67fdffd620a584fd
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2018
ms.locfileid: "46705274"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Postupy: Zápis kopírovacího konstruktoru (Průvodce programováním v C#)
C# neposkytuje konstruktor kopírování pro objekty, ale můžete jej napsat sami.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Person` [třídy](../../../csharp/language-reference/keywords/class.md) definuje kopírovacího konstruktora představujícího společně s argumentem instanci `Person`. Hodnoty vlastností argumentu jsou přiřazeny novým vlastnostem nové instance `Person`. Kód obsahuje alternativní kopírovací konstruktor, který odešle `Name` a `Age` vlastnosti instance, kterou chcete zkopírovat do konstruktoru instance třídy.  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.ICloneable>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)
