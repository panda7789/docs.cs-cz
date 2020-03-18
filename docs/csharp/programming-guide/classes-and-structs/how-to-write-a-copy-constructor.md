---
title: Jak napsat konstruktor kopie - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: aa6feb1b07f491a90a78684e254910d387b9bccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714844"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Jak napsat konstruktor kopie (C# Programovací průvodce)
C# neposkytuje konstruktor kopie pro objekty, ale můžete napsat sami.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Person` [třída](../../language-reference/keywords/class.md) definuje konstruktor kopie, který bere jako `Person`svůj argument instanci . Hodnoty vlastností argumentu jsou přiřazeny vlastnostem nové `Person`instance . Kód obsahuje alternativní kopie konstruktor, `Name` `Age` který odešle a vlastnosti instance, které chcete zkopírovat do konstruktorinstance třídy.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.ICloneable>
- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizační metody](./destructors.md)
