---
title: 'Postupy: Vyvolávání událostí třídy Base v odvozených třídách - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: bc968ea9c6f60ea6efda807bf254f595c61f8d4a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976080"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Postupy: Vyvolávání událostí třídy Base v odvozených třídách (C# Průvodce programováním v)
Následující jednoduchý příklad ukazuje standardní způsob pro deklaraci události v základní třídě tak, aby se také mohou být vyvolány z odvozených tříd. Tento model je často používána ve Windows Forms třídy v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd.  
  
 Když vytváříte třídu, která slouží jako základní třída pro jiné třídy, měli byste zvážit vzhledem k tomu, že události mají speciální typ delegáta, který lze vyvolat pouze z v rámci třídy, která je deklarována. Odvozené třídy nelze přímo vyvolat události, které jsou deklarovány v základní třídě. I když v některých případech může být vhodné událost, která může být vyvolána pouze základní třídy, ve většině případů, měli byste povolit odvozené třídy, která se má vyvolat události základní třídy. K tomuto účelu můžete vytvořit chráněné vyvolání metody základní třídy, která obaluje události. Při volání nebo potlačení této vyvolání metody, mohou odvozené třídy vyvolat událost nepřímo.  
  
> [!NOTE]
>  Nezadávejte deklarování virtuálních událostí v základní třídě a přepsat v odvozené třídě. Kompilátor jazyka C# nezpracovává tyto správně a zda předplatiteli odvozené událostí bude ve skutečnosti se přihlášení k odběru události základní třídy nepředvídatelné.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Události](../../../csharp/programming-guide/events/index.md)
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)
- [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [Vytváření obslužných rutin událostí ve Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
