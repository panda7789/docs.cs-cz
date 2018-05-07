---
title: 'Postupy: Použití slovníku k ukládání instancí událostí (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: 97a7b0f168e4a1c81ec396f42b731dabb45b3516
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>Postupy: Použití slovníku k ukládání instancí událostí (Průvodce programováním v C#)
Jedno použití pro `accessor-declarations` je vystavit mnoho událostí bez přidělování pole pro každou jednotlivou událost, ale místo toho pomocí slovníku k ukládání instancí událostí. To je užitečné pouze v případě, že máte mnoho událostí, ale očekáváte, že se neprovádí, většina události.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Události](../../../csharp/programming-guide/events/index.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)
