---
title: Zápis kopírovacího konstruktoru – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: aa6feb1b07f491a90a78684e254910d387b9bccd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714844"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Zápis kopírovacího konstruktoru (C# Průvodce programováním)
C#neposkytuje kopírovací konstruktor pro objekty, ale můžete si ho napsat sami.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu [třída](../../language-reference/keywords/class.md) `Person`definuje kopírovací konstruktor, který přebírá jako svůj argument instanci `Person`. Hodnoty vlastností argumentu jsou přiřazeny vlastnostem nové instance `Person`. Kód obsahuje alternativní kopírovací konstruktor, který odesílá `Name` a vlastnosti `Age` instance, kterou chcete zkopírovat do konstruktoru instance třídy.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ICloneable>
- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizační metody](./destructors.md)
