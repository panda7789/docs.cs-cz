---
title: "Deklarace a vyvolávání událostí (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0bf75cfba5102be5d837af385e2d3578f78a03c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Návod: Deklarace a vyvolávání událostí (Visual Basic)
Tento návod ukazuje, jak deklarace a vyvolávání událostí třídy s názvem `Widget`. Po dokončení kroků, můžete chtít přečíst téma doprovodné [návod: zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), který ukazuje způsob použití události z `Widget` objekty, které chcete poskytnout informace o stavu v aplikaci.  
  
## <a name="the-widget-class"></a>Pomůcka – třída  
 Předpokládejme, ke které máte nyní `Widget` třídy. Vaše `Widget` třída obsahuje metody, která může trvat dlouhou dobu spuštění a má vaše aplikace moci uvést do určitého druhu dokončení indikátoru.  
  
 Samozřejmě můžete dokonce vytvářet `Widget` objekt zobrazit procento dokončení dialogové okno, ale pak můžete by zablokuje se toto okno zobrazené v každém projektu, ve které jste použili `Widget` třídy. Dobrý Princip návrhu objektu je umožnit aplikaci, která používá popisovač objektu uživatelské rozhraní – Pokud celý účelem objektu je spravovat pole formuláře nebo dialogového okna.  
  
 Účelem `Widget` je provést další úlohy, proto je lepší pro přidání `PercentDone` událostí a umožňují procedury, která volá `Widget`je metody zpracování, že stav události a zobrazení aktualizací. `PercentDone` Událost můžete také poskytují mechanismus pro zrušení úlohy.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>K vytvoření příklad kódu pro toto téma  
  
1.  Otevřete nový [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] aplikace Windows projektu a vytvořte formulář s názvem `Form1`.  
  
2.  Přidat dvě tlačítka a štítek pro `Form1`.  
  
3.  Název objekty, jak je znázorněno v následující tabulce.  
  
    |Objekt|Vlastnost|Nastavení|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Spouštěcí úkol|  
    |`Button2`|`Text`|Zrušit|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4.  Na **projektu** nabídce zvolte **přidat třídu** přidat třídu s názvem `Widget.vb` do projektu.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Deklarovat událost pro pomůcky – třída  
  
-   Použití `Event` – klíčové slovo deklarovat událost v `Widget` třídy. Všimněte si, že událost může mít `ByVal` a `ByRef` argumenty, jako `Widget`na `PercentDone` ukazuje událostí:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 Při volání objektu obdrží `PercentDone` událostí, `Percent` argument obsahuje procento dokončení úkolu. `Cancel` Argument může být nastaven na `True` zrušit metodu, která se vyvolá událost.  
  
> [!NOTE]
>  Argumenty událostí můžou deklarovat, stejným způsobem jako argumenty procedur, s následujícími výjimkami: události nemůže mít `Optional` nebo `ParamArray` argumentů a události nemají návratové hodnoty.  
  
 `PercentDone` Událost vyvolána pomocí `LongTask` metodu `Widget` třídy. `LongTask`přebírá dva argumenty: doba metodu předstírá, že by práci a minimální časový interval před `LongTask` pozastaví zvýšit `PercentDone` událostí.  
  
#### <a name="to-raise-the-percentdone-event"></a>Pro vyvolání události PercentDone  
  
1.  Zjednodušení přístupu k `Timer` vlastnost použitou touto třídou, přidejte `Imports` příkaz do horní části deklarace modulů tříd výše `Class Widget` příkaz.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  Přidejte následující kód, který `Widget` třídy:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 Pokud aplikace zavolá `LongTask` metody `Widget` třídy vyvolá `PercentDone` událostí každých `MinimumInterval` sekund. Po návratu událost `LongTask` kontroluje, pokud `Cancel` argument byl nastaven na hodnotu `True`.  
  
 Tady jsou nezbytné několik omezení. Pro jednoduchost `LongTask` postupu se předpokládá můžete předem vědět, jak dlouho bude trvat úlohu. Toto je téměř žádné případu. Rozdělení úloh do bloků i velikost může být složité a často nejdůležitějším uživatelům je jednoduše množství času, který uplyne, než získají jako ukazatel toho, že se něco děje.  
  
 Může mít další vadou nanese v této ukázce. `Timer` Vlastnost vrátí počet sekund, které uplynuly od půlnoci; proto aplikaci vázne, pokud je spuštěno těsně před půlnoci. Více pečlivě přístup k měření doby by podmínky hranice například to v úvahu, nebo zabránění jejímu provedení je zcela, pomocí vlastnosti, jako třeba `Now`.  
  
 Teď, když `Widget` třídy můžete vyvolávání událostí, můžete přesunout na další návod. [Návod: Zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) ukazuje, jak používat `WithEvents` přidružit obslužné rutiny události s `PercentDone` událostí.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>  
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>  
 [Návod: Zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)  
 [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)
