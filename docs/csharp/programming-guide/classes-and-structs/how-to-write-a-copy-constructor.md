---
title: "Postupy: Zápis kopírovacího konstruktoru (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f15d8fabc49cbff5515b78a7d2fb6f9e49d0704e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Postupy: Zápis kopírovacího konstruktoru (Průvodce programováním v C#)
C# neposkytuje kopírovacího konstruktoru pro objekty, ale můžete napsat vlastní.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Person` [třída](../../../csharp/language-reference/keywords/class.md) definuje kopie konstruktor, který přijímá, jako její argument instanci `Person`. Hodnoty vlastnosti argumentu přiřazené k vlastnosti novou instanci třídy `Person`. Kód obsahuje alternativní kopírovací konstruktor, který odesílá `Name` a `Age` vlastnosti instance, kterou chcete zkopírovat do konstruktoru instance třídy.  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ICloneable>  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)
