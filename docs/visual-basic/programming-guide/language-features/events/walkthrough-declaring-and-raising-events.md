---
title: Deklarace a vyvolávání událostí (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: f792109f1d1117b5b112e06da1510938e4b8a5ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580492"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Průvodce: Deklarace a vyvolávání událostí (Visual Basic)
Tento návod ukazuje, jak deklarovat a vyvolávání událostí pro třídu s názvem `Widget`. Po dokončení kroků se můžete chtít přečíst téma doprovodná [názorný postup: Zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), který ukazuje, jak používat události z `Widget` objekty poskytnout informace o stavu v aplikaci.  
  
## <a name="the-widget-class"></a>Třída widgetu  
 Předpokládejme, že máte nyní `Widget` třídy. Vaše `Widget` třída nemá metodu, která může trvat dlouhou dobu spuštění, a chcete, aby vaše aplikace bude moct vyvěste určitého druhu dokončení indikátoru.  
  
 Samozřejmě můžete provést `Widget` objekt zobrazit dokončeno % dialogovému oknu, ale pak jste by zablokuje se tohoto dialogového okna v každém projektu, ve které jste použili `Widget` třídy. Dobré zásady navrhování objektu je umožnit aplikaci, která používá popisovač objektu uživatelského rozhraní – Pokud je účelem objektu ke správě pole formuláře nebo dialogového okna.  
  
 Účelem `Widget` je a provádět další úlohy, tak, aby byl lepší přidat `PercentDone` událostí a umožňují proceduru, která volá `Widget`uživatele metody zpracovávají, události a zobrazení stavu aktualizace. `PercentDone` Události můžete taky mělo poskytovat mechanismus pro zrušení úkolu.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Chcete-li vytvořit příklad kódu pro toto téma  
  
1.  Otevřete nový projekt aplikace Windows jazyka Visual Basic a vytvořte formulář s názvem `Form1`.  
  
2.  Přidání dvou tlačítek a popisek pro `Form1`.  
  
3.  Jak je znázorněno v následující tabulce, pojmenujte objekty.  
  
    |Objekt|Vlastnost|Nastavení|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Spouštěcí úkol|  
    |`Button2`|`Text`|Zrušit|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4.  Na **projektu** nabídce zvolte **přidat třídu** přidat třídu s názvem `Widget.vb` do projektu.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Chcete-li deklarovat události pro třídu widgetu  
  
-   Použití `Event` – klíčové slovo pro deklaraci události v `Widget` třídy. Všimněte si, že událost může mít `ByVal` a `ByRef` argumenty, jako `Widget`společnosti `PercentDone` ukazuje událostí:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 Když se obdrží objektem neúčastnícím se volání `PercentDone` událostí, `Percent` argument obsahuje procento dokončení úkolu. `Cancel` Argument může být nastaven na `True` zrušit metodu, která vyvolala událost.  
  
> [!NOTE]
>  Je možné deklarovat argumenty události, stejně jako argumenty procedur, s následujícími výjimkami: Události nemohou mít `Optional` nebo `ParamArray` argumenty a události nemají návratové hodnoty.  
  
 `PercentDone` Vyvolá událost `LongTask` metodu `Widget` třídy. `LongTask` přebírá dva argumenty: doba metodu předstírá, že se to práci a minimální časový interval před `LongTask` možné zvýšit `PercentDone` událostí.  
  
#### <a name="to-raise-the-percentdone-event"></a>Aby se vyvolala událost PercentDone  
  
1.  Pro zjednodušení přístupu k `Timer` přidat vlastnost použitou touto třídou `Imports` příkaz do horní části deklarace třídy modulu, výše `Class Widget` příkazu.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  Přidejte následující kód, který `Widget` třídy:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 Když vaše aplikace volá `LongTask` metody `Widget` třídy vyvolá `PercentDone` událost každých `MinimumInterval` sekund. Po návratu události `LongTask` kontroluje, jestli `Cancel` argument byl nastaven na `True`.  
  
 Zde je potřeba několik omezení. Pro zjednodušení `LongTask` postupu se předpokládá můžete předem vědět, jak dlouho bude trvat úkolu. To platí téměř nikdy. Dělení do bloků velikosti i úlohy může být složité a často to nejdůležitější uživatelů je jednoduše množství času, který uplyne, než se jim zobrazí jako ukazatel toho, že se něco děje.  
  
 Může mít další vadou nanese v této ukázce. `Timer` Vlastnost vrátí počet sekund, které uplynuly od půlnoci; proto aplikace zasekne, pokud je spuštěna těsně před půlnocí. Více opatrní přístup k měření doby by přijmout podmínky hranice takovou situaci v úvahu, nebo jim zabránit zcela, například pomocí vlastnosti `Now`.  
  
 Teď, když `Widget` třída může vyvolat události, můžete přesunout do dalšího názorného postupu. [Návod: Zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) ukazuje, jak používat `WithEvents` přidružení obslužné rutiny události s `PercentDone` událostí.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [Návod: Zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)
