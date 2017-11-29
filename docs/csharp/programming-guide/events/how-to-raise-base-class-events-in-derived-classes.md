---
title: "Postupy: Vyvolávání událostí třídy Base v odvozených třídách (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 548409d3f632213f3ff1de0a27a70b9f42b18332
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Postupy: Vyvolávání událostí třídy Base v odvozených třídách (Průvodce programováním v C#)
Následující jednoduchý příklad ukazuje standardní způsob deklarace události v základní třídě tak, aby se mohou být vyvolány z odvozené třídy. Tento vzor je často používány v třídách Windows Forms v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd.  
  
 Když vytváříte třídu, která lze použít jako základní třída pro jiné třídy, měli byste zvážit skutečnost, že události jsou zvláštním typem delegáta, který jde volat jenom z v rámci třídy, který je deklarován. Odvozené třídy nemohou vyvolat přímo události, které jsou deklarované v rámci základní třídy. I když můžete někdy událost, která mohou být vyvolány pouze v základní třídě, ve většině případů, měli byste povolit odvozené třídy k vyvolání události základní třídy. K tomuto účelu můžete vytvořit chráněnou volajícím metodu v základní třídě, která zabalí události. Volání metody nebo potlačení této metody volajícím, odvozené třídy vyvolat událost nepřímo.  
  
> [!NOTE]
>  Nezadávejte deklarovat virtuálních událostí v základní třídě a jejich přepsání v odvozené třídě. Kompilátor jazyka C# nezpracovává tyto správně a zda odběratele odvozené události bude ve skutečnosti se přihlášení k odběru událostí – základní třída nepředvídatelným.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Události](../../../csharp/programming-guide/events/index.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
 [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Vytváření obslužných rutin událostí v systému Windows Forms](https://msdn.microsoft.com/library/dacysss4.aspx)
