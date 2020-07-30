---
title: Postup explicitní implementace členů rozhraní – Průvodce programováním v C#
description: Naučte se explicitně implementovat členy rozhraní v tomto příkladu C#. Členové jsou k dispozici prostřednictvím instance rozhraní.
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 35b512ff6cbee1dd942f5b3476db660481808297
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303072"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Postup explicitní implementace členů rozhraní (Průvodce programováním v C#)
Tento příklad deklaruje [rozhraní](../../language-reference/keywords/interface.md), `IDimensions` , a třídu, `Box` ,, která explicitně implementuje členy rozhraní `GetLength` a `GetWidth` . Členové jsou k dispozici prostřednictvím instance rozhraní `dimensions` .  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Robustní programování  
  
- Všimněte si, že následující řádky v `Main` metodě jsou zakomentovány, protože by vznikly chyby při kompilaci. Člen rozhraní, který je explicitně implementován, není k dispozici z instance [třídy](../../language-reference/keywords/class.md) :  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Všimněte si také, že následující řádky v `Main` metodě úspěšně vytiskly rozměry pole, protože metody jsou volány z instance rozhraní:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](../classes-and-structs/index.md)
- [Rozhraní](./index.md)
- [Jak explicitně implementovat členy dvou rozhraní](./how-to-explicitly-implement-members-of-two-interfaces.md)
