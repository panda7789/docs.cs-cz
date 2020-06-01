---
title: Události – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: e15c3d124b4d1c30e2f9bb9f44b40e25b6a72346
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240718"
---
# <a name="events-c-programming-guide"></a>Události (Průvodce programováním v C#)
Události umožňují [třídě](../../language-reference/keywords/class.md) nebo objektu upozornit jiné třídy nebo objekty, když dojde k nějakému zájmu. Třída, která odesílá (nebo *vyvolává*) událost, se nazývá *Vydavatel* a třídy, které přijmou (nebo *zpracovávají*) událost se nazývají *předplatitelé*.  
  
V typické model Windows Forms v C# nebo webové aplikaci se přihlásíte k odběru událostí vyvolaných ovládacími prvky, jako jsou tlačítka a seznamy. Pomocí integrovaného vývojového prostředí (IDE) jazyka Visual C# můžete procházet události, které ovládací prvek publikuje, a vybrat ty, které chcete zpracovat. Rozhraní IDE poskytuje snadný způsob, jak automaticky přidat prázdnou metodu obslužné rutiny události a kód pro přihlášení k odběru události. Další informace najdete v tématu [jak se přihlásit k odběru událostí a odhlásit se z](./how-to-subscribe-to-and-unsubscribe-from-events.md)nich.
  
## <a name="events-overview"></a>Přehled událostí  
 Události mají následující vlastnosti:  
  
- Vydavatel určí, kdy se událost vyvolá; Předplatitelé určují, jakou akci provádí v reakci na událost.  
  
- Událost může mít více odběratelů. Předplatitel může zpracovávat více událostí od více vydavatelů.  
  
- Události, které nemají žádné předplatitele, nejsou nikdy vyvolány.  
  
- Události se obvykle používají k signalizaci uživatelských akcí, jako například kliknutí na tlačítko nebo výběry nabídky v grafickém uživatelském rozhraní.  
  
- Pokud má událost více odběratelů, obslužné rutiny události jsou vyvolány synchronně při vyvolání události. Chcete-li vyvolat události asynchronně, přečtěte si téma [asynchronní volání synchronních metod](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
- V knihovně tříd .NET Framework jsou události založeny na <xref:System.EventHandler> delegátu a <xref:System.EventArgs> základní třídě.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace naleznete v tématu:  
  
- [Jak přihlásit a odhlásit odběr událostí](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [Jak publikovat události, které jsou v souladu s pokyny pro .NET](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [Jak vyvolávat události základní třídy v odvozených třídách](./how-to-raise-base-class-events-in-derived-classes.md)

- [Jak implementovat události rozhraní](./how-to-implement-interface-events.md)

- [Jak implementovat vlastní přístupové objekty událostí](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v tématu [události](~/_csharplang/spec/classes.md#events) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="featured-book-chapters"></a>Doporučené kapitoly knihy  
 [Delegáti, události a výrazy lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [C# 3,0 kuchařka, třetí edice: více než 250 řešení pro c# 3,0 programátory](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegáti a události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) v [kurzu C# 3,0: hlavní základy jazyka c# 3,0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Viz také

- <xref:System.EventHandler>
- [Průvodce programováním v C#](../index.md)
- [Delegáti](../delegates/index.md)
- [Vytváření obslužných rutin událostí ve Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
