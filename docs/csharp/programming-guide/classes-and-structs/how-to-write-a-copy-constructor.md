---
title: Postup psaní konstruktoru kopírování – Průvodce programováním v C#
description: Naučte se, jak napsat kopírovací konstruktor v jazyce C#, který přebírá instanci třídy a vrací novou instanci s hodnotami vstupu.
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: beb2fcfaa36303eeaabd5278cf5e7a128282270e
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864225"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a>Zápis kopírovacího konstruktoru (Průvodce programováním v C#)
C# neposkytuje kopírovací konstruktor pro objekty, ale můžete si ho napsat sami.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Person` [Třída](../../language-reference/keywords/class.md) definuje kopírovací konstruktor, který přebírá jako svůj argument instanci `Person` . Hodnoty vlastností argumentu jsou přiřazeny vlastnostem nové instance `Person` . Kód obsahuje alternativní kopírovací konstruktor, který odesílá `Name` `Age` vlastnosti a instance, kterou chcete zkopírovat do konstruktoru instance třídy.  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.ICloneable>
- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizační metody](./destructors.md)
