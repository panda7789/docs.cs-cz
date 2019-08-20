---
title: 'Postupy: Zápis kopírovacího konstruktoru – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: bdc352566052f4cec1686176131e9b1e1b768794
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596603"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Postupy: Zápis kopírovacího konstruktoru (C# Průvodce programováním)
C#neposkytuje kopírovací konstruktor pro objekty, ale můžete si ho napsat sami.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Person` [Třída](../../language-reference/keywords/class.md) definuje kopírovací konstruktor, který přebírá jako svůj argument instanci `Person`. Hodnoty vlastností argumentu jsou přiřazeny vlastnostem nové instance `Person`. Kód obsahuje alternativní kopírovací konstruktor, který odesílá `Name` vlastnosti a `Age` instance, kterou chcete zkopírovat do konstruktoru instance třídy.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ICloneable>
- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizační metody](./destructors.md)
