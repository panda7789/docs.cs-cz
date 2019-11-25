---
title: Zápis kopírovacího konstruktoru – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 4ac7ccb55775019eb86d5345797d2fd74d3b9527
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970389"
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
