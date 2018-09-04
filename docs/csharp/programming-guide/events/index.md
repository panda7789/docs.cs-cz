---
title: Události (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 03c2ffc37bc6c2e820b8e28599f415cde1be9be5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521954"
---
# <a name="events-c-programming-guide"></a>Události (Průvodce programováním v C#)
Události umožňují [třída](../../../csharp/language-reference/keywords/class.md) nebo objektům upozornit ostatní třídy nebo objektů, dojde-li něco, které vás zajímají. Třída, která odesílá (nebo *vyvolá*) události je volána *vydavatele* a třídy, které přijímají (nebo *zpracování*) události se nazývají *předplatitele* .  
  
 V typické aplikaci C# Windows Forms nebo Web se přihlásíte k odběru události vyvolané službou ovládací prvky jako tlačítka a pole se seznamem. Visual C# integrované vývojové prostředí (IDE) můžete procházet události, které publikuje ovládací prvek a vyberte ty, které chcete zpracovat. Rozhraní IDE automaticky přidá metodu obslužné rutiny události prázdný a kód, který se k události registrovat. Další informace najdete v tématu [postupy: přihlášení k odběru a zrušit její odběr události](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="events-overview"></a>Přehled událostí  
 Události mají následující vlastnosti:  
  
-   Vydavatel Určuje, kdy je vyvolána událost; předplatitele určit, jaká akce se provede v reakci na událost.  
  
-   Událost může mít několik předplatitelů. Odběratele můžete zpracování více událostí z více vydavatelé.  
  
-   Nikdy jsou vyvolány události, které mají žádné předplatitele.  
  
-   Události se obvykle používají k signalizaci uživatelské akce, jako je kliknutí na tlačítko nebo nabídku v grafickém uživatelském rozhraní.  
  
-   Pokud má událost několik předplatitelů, obslužné rutiny událostí jsou vyvolala synchronně, když je vyvolána událost. K vyvolání události asynchronně, naleznete v tématu [voláním synchronní metody asynchronně](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
-   V [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd, události jsou založeny na <xref:System.EventHandler> delegáta a <xref:System.EventArgs> základní třídy.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace naleznete v tématu:  
  
-   [Postupy: Přihlášení a odhlášení odběru událostí](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [Postupy: Vyvolávání událostí třídy Base v odvozených třídách](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [Postupy: implementace událostí rozhraní](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Synchronizace vláken](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [Postupy: Použití slovníku k ukládání instancí událostí](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [Postupy: Implementace vlastních přístupových objektů událostí](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>Doporučené kapitoly knihy  
 [Delegáty, události a výrazy Lambda](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) v [C# 3.0 Cookbook, Third Edition: víc než 250 řešení pro programátory v C# 3.0](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)  
  
 [Delegáti a události](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) v [Learning C# 3.0: Master Základy C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Viz také

- <xref:System.EventHandler>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
- [Vytváření obslužných rutin událostí ve Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
