---
title: Události (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 5b844b20ac62b4cbc2a73931eecab95f22b4b1de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339914"
---
# <a name="events-c-programming-guide"></a>Události (Průvodce programováním v C#)
Povolit události [třídy](../../../csharp/language-reference/keywords/class.md) nebo objekt, který chcete upozornit jiné třídy nebo objekty něco zájmu případě. Třídu, která odešle (nebo *vyvolá*) událost se nazývá *vydavatele* a třídy, které přijímají (nebo *zpracování*) se označují jako událost *odběratele* .  
  
 V typické aplikaci Windows Forms C# nebo webové přihlášení k odběru události vyvolané ovládacími prvky, jako jsou tlačítka a seznamy. Jazyce Visual C# integrované vývojové prostředí (IDE) můžete procházet události, které publikuje ovládacího prvku a vyberte ty, které chcete zpracovat. Rozhraní IDE automaticky přidá metodu obslužné rutiny události prázdný a kód k odběru události. Další informace najdete v tématu [postupy: přihlášení a odhlášení odběru událostí](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="events-overview"></a>Přehled událostí  
 Události mít následující vlastnosti:  
  
-   Vydavatel Určuje, kdy je vyvolána událost; odběratele určit, jaké akce se provede v reakci na událost.  
  
-   Událost může mít více odběrateli. Odběratel může zpracovat více událostí z více vydavatele.  
  
-   Události, které mají žádné Odběratelé, kteří jsou nikdy vyvolána.  
  
-   Události jsou obvykle používány signál uživatele akcí, například kliknutí na tlačítko nebo nabídky výběrů v grafickém uživatelském rozhraní.  
  
-   Událost má více odběrateli, obslužné rutiny událostí jsou vyvolány synchronně, když událost se vyvolá. Vyvolání událostí asynchronně, najdete v tématu [volání synchronních metod asynchronně](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
-   V [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd události jsou založené na <xref:System.EventHandler> delegovat a <xref:System.EventArgs> základní třídy.  
  
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
 [Výrazy Lambda, delegáti a události](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) v [C# 3.0 Cookbook, Third Edition: víc než 250 řešení pro programátory v jazyce C# 3.0](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)  
  
 [Delegáti a události](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) v [Learning C# 3.0: Master Základy C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.EventHandler>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
 [Vytváření obslužných rutin událostí ve Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Vícevláknové programování s asynchronním vzorem založeným na událostech](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
