---
title: 'Postupy: Explicitní implementace členů rozhraní - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 064061b44cca3adb5dde89ecc71fb1f8ea3abf8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562901"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Postupy: Explicitní implementace členů rozhraní (C# Průvodce programováním v)
V tomto příkladu deklaruje [rozhraní](../../../csharp/language-reference/keywords/interface.md), `IDimensions`a třídu, `Box`, které explicitně implementuje členy rozhraní `getLength` a `getWidth`. Členy jsou přístupné prostřednictvím instance rozhraní `dimensions`.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a>Robustní programování  
  
-   Všimněte si, že následující řádky v `Main` metody, jsou zakomentované vzhledem k tomu, že se vytvoří chyby kompilace. Explicitně implementovaný člen rozhraní, není přístupná z [třídy](../../../csharp/language-reference/keywords/class.md) instance:  
  
     [!code-csharp[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   Všimněte si také, že následující řádky v `Main` metoda úspěšně vytiskne rozměry pole vzhledem k tomu, že se z instance rozhraní volání těchto metod:  
  
     [!code-csharp[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Rozhraní](../../../csharp/programming-guide/interfaces/index.md)
- [Postupy: Explicitní implementace členů dvou rozhraní](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
