---
title: 'Postupy: Použití slovníku k instancí událostí Store - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: 819c81aed3a6f09a20e51285058dcc77749dd33a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245139"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>Postupy: Použití slovníku k události instance Store (C# Průvodce programováním v)
Jedním použitím `accessor-declarations` je zveřejnit mnoho událostí bez přidělování pole pro každou událost, ale místo toho použití slovníku k ukládání instancí událostí. To je užitečné pouze, pokud máte mnoho událostí, ale očekáváte, že většina události se nebude implementovat.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Události](../../../csharp/programming-guide/events/index.md)  
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)
