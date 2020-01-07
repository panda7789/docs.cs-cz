---
title: Explicitní implementace členů rozhraní – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 4efc325b3587ee790cce739727506a28c3a1f524
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635402"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Postup explicitní implementace členů rozhraní (C# Průvodce programováním)
Tento příklad deklaruje [rozhraní](../../language-reference/keywords/interface.md), `IDimensions`a třídu, `Box`, která explicitně implementuje členy rozhraní `getLength` a `getWidth`. Členové jsou k dispozici prostřednictvím instance rozhraní `dimensions`.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Robustní programování  
  
- Všimněte si, že následující řádky v metodě `Main` jsou zakomentovány, protože by vznikly chyby při kompilaci. Člen rozhraní, který je explicitně implementován, není k dispozici z instance [třídy](../../language-reference/keywords/class.md) :  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Všimněte si také, že následující řádky v metodě `Main` úspěšně vytiskly rozměry pole, protože metody jsou volány z instance rozhraní:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](../classes-and-structs/index.md)
- [Rozhraní](./index.md)
- [Postup explicitní implementace členů dvou rozhraní](./how-to-explicitly-implement-members-of-two-interfaces.md)
