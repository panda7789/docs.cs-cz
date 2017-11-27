---
title: "Události (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f714bded446e62ac6165d691d2404249275178e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="events-c-programming-guide"></a>Události (Průvodce programováním v C#)
Povolit události [třídy](../../../csharp/language-reference/keywords/class.md) nebo objekt, který chcete upozornit jiné třídy nebo objekty něco zájmu případě. Třídu, která odešle (nebo *vyvolá*) událost se nazývá *vydavatele* a třídy, které přijímají (nebo *zpracování*) se označují jako událost *odběratele* .  
  
 V typické aplikaci Windows Forms C# nebo webové přihlášení k odběru události vyvolané ovládacími prvky, jako jsou tlačítka a seznamy. Můžete použít [!INCLUDE[csprcs](~/includes/csprcs-md.md)] integrované vývojové prostředí (IDE) a procházejte události, které publikuje ovládacího prvku a vyberte ty, které chcete zpracovat. Rozhraní IDE automaticky přidá metodu obslužné rutiny události prázdný a kód k odběru události. Další informace najdete v tématu [postupy: přihlášení a odhlášení odběru událostí](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="events-overview"></a>Přehled událostí  
 Události mít následující vlastnosti:  
  
-   Vydavatel Určuje, kdy je vyvolána událost; odběratele určit, jaké akce se provede v reakci na událost.  
  
-   Událost může mít více odběrateli. Odběratel může zpracovat více událostí z více vydavatele.  
  
-   Události, které mají žádné Odběratelé, kteří jsou nikdy vyvolána.  
  
-   Události jsou obvykle používány signál uživatele akcí, například kliknutí na tlačítko nebo nabídky výběrů v grafickém uživatelském rozhraní.  
  
-   Událost má více odběrateli, obslužné rutiny událostí jsou vyvolány synchronně, když událost se vyvolá. Vyvolání událostí asynchronně, najdete v tématu [volání synchronních metod asynchronně](https://msdn.microsoft.com/library/2e08f6yc).  
  
-   V [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd události jsou založené na <xref:System.EventHandler> delegovat a <xref:System.EventArgs> základní třídy.  
  
## <a name="related-sections"></a>Související oddíly  
 Další informace naleznete v tématu:  
  
-   [Postupy: přihlášení a odhlášení odběru událostí](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [Postupy: publikování událostí odpovídajících směrnicím rozhraní .NET Framework pokyny](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [Postupy: vyvolávání událostí třídy Base v odvozených třídách](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [Postupy: implementace událostí rozhraní](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Synchronizace vláken](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [Postupy: použití slovníku k ukládání instancí událostí](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [Postupy: implementace vlastních přístupových objektů událostí](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>Doporučené kapitoly knihy  
 [Výrazy Lambda, delegáti a události](http://go.microsoft.com/fwlink/?LinkId=195395) v [C# 3.0 Cookbook, Third Edition: víc než 250 řešení pro programátory v jazyce C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195369)  
  
 [Delegáti a události](http://go.microsoft.com/fwlink/?LinkId=195418) v [Learning C# 3.0: Master Základy C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.EventHandler>  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
 [Vytváření obslužných rutin událostí v systému Windows Forms](https://msdn.microsoft.com/library/dacysss4.aspx)  
 [Vícevláknové programování s asynchronním vzorem založený na událostech](https://msdn.microsoft.com/library/hkasytyf)
