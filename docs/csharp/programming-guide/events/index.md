---
title: Události – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 183f53a579bdd9f70deb16ca9157c377fa3aff3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75712309"
---
# <a name="events-c-programming-guide"></a>Události (Průvodce programováním v C#)
Události umožňují [třídy](../../language-reference/keywords/class.md) nebo objekt upozorňovat jiné třídy nebo objekty, když dojde k něčemu zajímavého. Třída, která odesílá (nebo *vyvolává*) událost se nazývá *vydavatel* a třídy, které přijímají (nebo *zpracování*) události se nazývají *předplatitelé*.  
  
V typické C# Windows Forms nebo webové aplikace se přihlásíte k odběru událostí vyzdvižených ovládacími prvky, jako jsou tlačítka a seznamy. Integrované vývojové prostředí Visual C# (IDE) můžete procházet události, které ovládací prvek publikuje a vyberte ty, které chcete zpracovat. IDE poskytuje snadný způsob, jak automaticky přidat prázdnou metodu obslužné rutiny události a kód k přihlášení k odběru události. Další informace naleznete v tématu [Jak se přihlásit k odběru a odhlásit z odběru událostí](./how-to-subscribe-to-and-unsubscribe-from-events.md).
  
## <a name="events-overview"></a>Přehled událostí  
 Události mají následující vlastnosti:  
  
- Vydavatel určuje, kdy je vyvolána událost; odběratelé určit, jaká akce je přijata v reakci na událost.  
  
- Událost může mít více odběratelů. Odběratel může zpracovávat více událostí od více vydavatelů.  
  
- Události, které nemají žádné odběratele jsou nikdy aktivována.  
  
- Události se obvykle používají k signalizaci akcí uživatele, jako jsou kliknutí na tlačítko nebo výběr nabídky v grafických uživatelských rozhraních.  
  
- Pokud událost má více odběratelů, obslužné rutiny události jsou vyvolány synchronně při vyvolání události. Chcete-li vyvolat události asynchronně, naleznete [v tématu volání synchronní metody asynchronně](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
- V knihovně třídy rozhraní .NET <xref:System.EventHandler> Framework jsou <xref:System.EventArgs> události založeny na delegátovi a základní třídě.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace naleznete v tématu:  
  
- [Jak přihlásit a odhlásit odběr událostí](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [Jak publikovat události vyhovující pravidlům rozhraní .NET Framework](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [Jak vyvolávat události základní třídy v odvozených třídách](./how-to-raise-base-class-events-in-derived-classes.md)

- [Jak implementovat události rozhraní](./how-to-implement-interface-events.md)

- [Jak implementovat vlastní přístupové objekty událostí](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a>Specifikace jazyka C#  

For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="featured-book-chapters"></a>Doporučené kapitoly knihy  
 [Delegáti, události a Lambda výrazy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [C# 3.0 Kuchařka, Třetí vydání: Více než 250 řešení pro C# 3.0 programátory](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
 [Delegáti a události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) v [učení C# 3.0: Master základy C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)  
  
## <a name="see-also"></a>Viz také

- <xref:System.EventHandler>
- [Programovací příručka jazyka C#](../index.md)
- [Delegáty](../delegates/index.md)
- [Vytváření obslužných rutin událostí ve Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
