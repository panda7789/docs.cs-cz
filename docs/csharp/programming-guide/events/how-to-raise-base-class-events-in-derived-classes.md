---
title: Jak zvýšit události základní třídy v odvozených třídách - Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 48f95871aa8a5a33923286262093a143cbd16d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712322"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Jak zvýšit události základní třídy v odvozených třídách (Průvodce programováním jazyka C#)
Následující jednoduchý příklad ukazuje standardní způsob deklarování událostí v základní třídě tak, aby mohly být také vyvolány z odvozených tříd. Tento vzor se používá ve velké míře ve třídách Windows Forms v knihovně tříd rozhraní .NET Framework.  
  
 Při vytváření třídy, která může být použita jako základní třída pro jiné třídy, měli byste zvážit skutečnost, že události jsou zvláštní typ delegáta, který lze vyvolat pouze z třídy, která je deklarovala. Odvozené třídy nelze přímo vyvolat události, které jsou deklarovány v rámci základní třídy. I když někdy můžete chtít událost, která může být vyvolána pouze základní třídy, většinu času, měli byste povolit odvozené třídy vyvolat události základní třídy. Chcete-li to provést, můžete vytvořit chráněnou metodu vyvolání v základní třídě, která zabalí událost. Voláním nebo přepsáním této metody vyvolání mohou odvozené třídy vyvolat událost nepřímo.  
  
> [!NOTE]
> Nedeklarujte virtuální události v základní třídě a přepsat je v odvozené třídě. Kompilátor Jazyka C# nezpracovává tyto správně a je nepředvídatelné, zda odběratel odvozené události bude skutečně přihlášení k odběru události základní třídy.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Akce](./index.md)
- [Delegáty](../delegates/index.md)
- [Modifikátory přístupu](../classes-and-structs/access-modifiers.md)
- [Vytváření obslužných rutin událostí ve Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
