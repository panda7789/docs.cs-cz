---
title: 'Postupy: Explicitní implementace členů rozhraní – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 5ef8b42fe5ca07548d52b88720ea4845d2408bb1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589203"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Postupy: Explicitní implementace členů rozhraní (C# Průvodce programováním)
Tento příklad deklaruje [rozhraní](../../language-reference/keywords/interface.md), `IDimensions`, a třídu, `Box`,, která explicitně implementuje členy `getLength` rozhraní a `getWidth`. Členové jsou k dispozici prostřednictvím instance `dimensions`rozhraní.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Robustní programování  
  
- Všimněte si, že následující řádky v `Main` metodě jsou zakomentovány, protože by vznikly chyby při kompilaci. Člen rozhraní, který je explicitně implementován, není k dispozici z instance [třídy](../../language-reference/keywords/class.md) :  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Všimněte si také, že následující řádky v `Main` metodě úspěšně vytiskly rozměry pole, protože metody jsou volány z instance rozhraní:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](../classes-and-structs/index.md)
- [Rozhraní](./index.md)
- [Postupy: Explicitní implementace členů dvou rozhraní](./how-to-explicitly-implement-members-of-two-interfaces.md)
