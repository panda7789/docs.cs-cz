---
title: 'Postupy: Vyvolávání událostí třídy Base v odvozených třídách - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 11f34e230a1f953ba3d886e416f1ece4253e3c8d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239615"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Postupy: Vyvolávání událostí třídy Base v odvozených třídách (C# Průvodce programováním v)
Následující jednoduchý příklad ukazuje standardní způsob pro deklaraci události v základní třídě tak, aby se také mohou být vyvolány z odvozených tříd. Tento model je často používána ve Windows Forms třídy v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd.  
  
 Když vytváříte třídu, která slouží jako základní třída pro jiné třídy, měli byste zvážit vzhledem k tomu, že události mají speciální typ delegáta, který lze vyvolat pouze z v rámci třídy, která je deklarována. Odvozené třídy nelze přímo vyvolat události, které jsou deklarovány v základní třídě. I když v některých případech může být vhodné událost, která může být vyvolána pouze základní třídy, ve většině případů, měli byste povolit odvozené třídy, která se má vyvolat události základní třídy. K tomuto účelu můžete vytvořit chráněné vyvolání metody základní třídy, která obaluje události. Při volání nebo potlačení této vyvolání metody, mohou odvozené třídy vyvolat událost nepřímo.  
  
> [!NOTE]
>  Nezadávejte deklarování virtuálních událostí v základní třídě a přepsat v odvozené třídě. Kompilátor jazyka C# nezpracovává tyto správně a zda předplatiteli odvozené událostí bude ve skutečnosti se přihlášení k odběru události základní třídy nepředvídatelné.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Události](../../../csharp/programming-guide/events/index.md)  
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
- [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [Vytváření obslužných rutin událostí ve Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
