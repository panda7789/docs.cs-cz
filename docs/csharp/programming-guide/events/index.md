---
title: Události – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 7a8a8e6b6a393f151d69d1879f475e04f44df5fa
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590380"
---
# <a name="events-c-programming-guide"></a>Události (Průvodce programováním v C#)
Události umožňují [třídě](../../language-reference/keywords/class.md) nebo objektu upozornit jiné třídy nebo objekty, když dojde k nějakému zájmu. Třída, která odesílá (nebo *vyvolává*) událost, se nazývá *Vydavatel* a třídy, které přijmou (nebo *zpracovávají*) událost se nazývají předplatitelé.  
  
 V typické C# model Windows Forms nebo webové aplikaci se přihlásíte k odběru událostí vyvolaných ovládacími prvky, jako jsou tlačítka a seznamy. Pomocí integrovaného vývojového C# prostředí (IDE) jazyka Visual můžete procházet události, které ovládací prvek publikuje, a vybrat ty, které chcete zpracovat. Rozhraní IDE poskytuje snadný způsob, jak automaticky přidat prázdnou metodu obslužné rutiny události a kód pro přihlášení k odběru události. Další informace najdete v tématu [jak: Přihlášení a odhlášení odběru událostí](./how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
## <a name="events-overview"></a>Přehled událostí  
 Události mají následující vlastnosti:  
  
- Vydavatel určí, kdy se událost vyvolá; Předplatitelé určují, jakou akci provádí v reakci na událost.  
  
- Událost může mít více odběratelů. Předplatitel může zpracovávat více událostí od více vydavatelů.  
  
- Události, které nemají žádné předplatitele, nejsou nikdy vyvolány.  
  
- Události se obvykle používají k signalizaci uživatelských akcí, jako například kliknutí na tlačítko nebo výběry nabídky v grafickém uživatelském rozhraní.  
  
- Pokud má událost více odběratelů, obslužné rutiny události jsou vyvolány synchronně při vyvolání události. Chcete-li vyvolat události asynchronně, přečtěte si téma [asynchronní volání synchronních metod](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
- V knihovně tříd .NET Framework jsou události založeny na <xref:System.EventHandler> delegátu <xref:System.EventArgs> a základní třídě.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace naleznete v tématu:  
  
- [Postupy: Přihlášení a odhlášení odběru událostí](./how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
- [Postupy: Publikovat události, které jsou v souladu s pokyny pro .NET Framework](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
- [Postupy: Vyvolat události třídy Base v odvozených třídách](./how-to-raise-base-class-events-in-derived-classes.md)  
  
- [Postupy:  Implementace událostí rozhraní](./how-to-implement-interface-events.md)  
  
- [Postupy: Implementace vlastních přístupových objektů událostí](./how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace najdete v tématu [události](~/_csharplang/spec/classes.md#events) ve [ C# specifikaci jazyka](../../language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="featured-book-chapters"></a>Doporučené kapitoly knihy  
 [Delegáti, události a výrazy lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [ C# 3,0 kuchařka, třetí vydání: Více než 250 řešení pro C# 3,0 programátory](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegáti a události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) [ve C# studiu 3,0: Hlavní základy C# 3,0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.EventHandler>
- [Průvodce programováním v jazyce C#](../index.md)
- [Delegáti](../delegates/index.md)
- [Vytváření obslužných rutin událostí ve Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
