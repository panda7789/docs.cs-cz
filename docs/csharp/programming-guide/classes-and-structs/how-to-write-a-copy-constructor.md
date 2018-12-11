---
title: 'Postupy: Zápis kopírovacího konstruktoru - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: daf0683060d7df5dc5e644b4b84aac3dcdea939f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240681"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Postupy: Zápis kopírovacího konstruktoru (C# Průvodce programováním v)
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
