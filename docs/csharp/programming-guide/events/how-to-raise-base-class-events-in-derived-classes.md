---
title: Postup vyvolání událostí třídy Base v odvozených třídách C# – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 6176b94b15edccb139ddd7de3101930b505d98a8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346296"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Postup vyvolání událostí třídy Base v odvozených třídáchC# (Průvodce programováním)
Následující jednoduchý příklad ukazuje standardní způsob, jak deklarovat události v základní třídě tak, aby mohly být také vyvolány z odvozených tříd. Tento model se používá rozsáhle v model Windows Forms třídy v knihovně tříd .NET Framework.  
  
 Když vytvoříte třídu, která může být použita jako základní třída pro jiné třídy, měli byste zvážit skutečnost, že události jsou speciálním typem delegáta, který lze volat pouze z třídy, která je deklarována. Odvozené třídy nemohou přímo vyvolat události, které jsou deklarovány v rámci základní třídy. I když v některých případech můžete chtít událost, která může být vyvolána pouze základní třídou, měla by tato odvozená třída umožňovat vyvolání událostí základní třídy. K tomu můžete vytvořit chráněnou metodu vyvolání v základní třídě, která zabalí událost. Voláním nebo přepsáním této metody vyvolání mohou odvozené třídy událost vyvolat nepřímo.  
  
> [!NOTE]
> Nedeklarujte virtuální události v základní třídě a přepište je v odvozené třídě. C# Kompilátor tyto správně nezpracovává a je nepředvídatelné, zda bude předplatitelem odvozené události ve skutečnosti přihlášena k odběru události základní třídy.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Události](./index.md)
- [Delegáti](../delegates/index.md)
- [Modifikátory přístupu](../classes-and-structs/access-modifiers.md)
- [Vytváření obslužných rutin událostí ve Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
