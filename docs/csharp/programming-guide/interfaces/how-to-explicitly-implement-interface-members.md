---
title: Jak explicitně implementovat členy rozhraní - Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: dff094aca237ed6146bd9b52813c40549bc99b9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627782"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Jak explicitně implementovat členy rozhraní (Průvodce programováním jazyka C#)
Tento příklad deklaruje [rozhraní](../../language-reference/keywords/interface.md) `IDimensions`a třídu , `Box`která `GetLength` `GetWidth`explicitně implementuje členy rozhraní a . Členové jsou přístupné prostřednictvím `dimensions`instance rozhraní .  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Robustní programování  
  
- Všimněte si, že `Main` následující řádky v metodě jsou zakomentovány, protože by způsobit chyby kompilace. Člen rozhraní, který je explicitně implementován nelze získat přístup z instance [třídy:](../../language-reference/keywords/class.md)  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Všimněte si také, že `Main` následující řádky v metodě úspěšně vytisknout rozměry pole, protože metody jsou volány z instance rozhraní:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](../classes-and-structs/index.md)
- [Rozhraní](./index.md)
- [Jak explicitně implementovat členy dvou rozhraní](./how-to-explicitly-implement-members-of-two-interfaces.md)
