---
title: 'Postupy: Zápis kopírovacího konstruktoru (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 8a7cc85d40272918f4839d13fcccb79b558eeac7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Postupy: Zápis kopírovacího konstruktoru (Průvodce programováním v C#)
C# neposkytuje kopírovacího konstruktoru pro objekty, ale můžete napsat vlastní.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Person` [třída](../../../csharp/language-reference/keywords/class.md) definuje kopie konstruktor, který přijímá, jako její argument instanci `Person`. Hodnoty vlastnosti argumentu přiřazené k vlastnosti novou instanci třídy `Person`. Kód obsahuje alternativní kopírovací konstruktor, který odesílá `Name` a `Age` vlastnosti instance, kterou chcete zkopírovat do konstruktoru instance třídy.  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ICloneable>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)
