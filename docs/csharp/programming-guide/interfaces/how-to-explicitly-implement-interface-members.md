---
title: Explicitní implementace členů rozhraní – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: dff094aca237ed6146bd9b52813c40549bc99b9b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627782"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Postup explicitní implementace členů rozhraní (C# Průvodce programováním)
Tento příklad deklaruje [rozhraní](../../language-reference/keywords/interface.md), `IDimensions`a třídu, `Box`, která explicitně implementuje členy rozhraní `GetLength` a `GetWidth`. Členové jsou k dispozici prostřednictvím instance rozhraní `dimensions`.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a>Robustní programování  
  
- Všimněte si, že následující řádky v metodě `Main` jsou zakomentovány, protože by vznikly chyby při kompilaci. Člen rozhraní, který je explicitně implementován, není k dispozici z instance [třídy](../../language-reference/keywords/class.md) :  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- Všimněte si také, že následující řádky v metodě `Main` úspěšně vytiskly rozměry pole, protože metody jsou volány z instance rozhraní:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](../classes-and-structs/index.md)
- [Rozhraní](./index.md)
- [Postup explicitní implementace členů dvou rozhraní](./how-to-explicitly-implement-members-of-two-interfaces.md)
