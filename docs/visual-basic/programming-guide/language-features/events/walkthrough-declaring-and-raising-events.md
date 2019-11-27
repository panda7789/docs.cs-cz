---
title: Deklarace a vyvolávání událostí
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 6f4c303604f9cf55b4ecd500636e0d2772b6234c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345090"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Návod: Deklarace a vyvolávání událostí (Visual Basic)
Tento návod ukazuje, jak deklarovat a vyvolat události pro třídu s názvem `Widget`. Po dokončení kroků si můžete přečíst doprovodné téma, [Návod: zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), které ukazuje, jak používat události z `Widget` objektů k poskytnutí informací o stavu v aplikaci.  
  
## <a name="the-widget-class"></a>Widget – třída  
 Předpokládejme, kdy máte `Widget` třídu. Vaše třída `Widget` má metodu, která může trvat dlouhou dobu, a chcete, aby aplikace mohla sestavit nějaký typ indikátoru dokončení.  
  
 Samozřejmě můžete nastavit, aby objekt `Widget` zobrazoval dialogové okno procento dokončení, ale pak byste zablokovali toto dialogové okno v každém projektu, ve kterém jste použili třídu `Widget`. Dobrým principem návrhu objektu je umožnit aplikaci, která používá objekt, zpracovat uživatelské rozhraní – Pokud celý účel objektu není spravovat formulář nebo dialogové okno.  
  
 Účelem `Widget` je provést jiné úkoly, takže je lepší přidat událost `PercentDone` a nechat proceduru, která volá metody `Widget`, zpracovávat tyto události a zobrazovat aktualizace stavu. Událost `PercentDone` může také poskytovat mechanismus pro zrušení úlohy.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Postup sestavení příkladu kódu pro toto téma  
  
1. Otevřete nový Visual Basic projekt aplikace pro Windows a vytvořte formulář s názvem `Form1`.  
  
2. Přidejte dvě tlačítka a popisek pro `Form1`.  
  
3. Pojmenujte objekty, jak je uvedeno v následující tabulce.  
  
    |Objekt|Vlastnost|Nastavení|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Spustit úkol|  
    |`Button2`|`Text`|Zrušit|  
    |`Label`|`(Name)``Text`|lblPercentDone, 0|  
  
4. V nabídce **projekt** vyberte možnost **Přidat třídu** a přidejte do projektu třídu s názvem `Widget.vb`.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Deklarace události pro třídu widgetu  
  
- Použijte klíčové slovo `Event` k deklaraci události ve třídě `Widget`. Všimněte si, že událost může mít argumenty `ByVal` a `ByRef`, jak demonstruje `Widget``PercentDone` událost:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Když volající objekt obdrží událost `PercentDone`, argument `Percent` obsahuje procento dokončeného úkolu. Argument `Cancel` lze nastavit na hodnotu `True`, aby bylo možné zrušit metodu, která událost vyvolala.  
  
> [!NOTE]
> Argumenty události lze deklarovat stejně jako argumenty procedur, s následujícími výjimkami: události nemohou mít `Optional` ani `ParamArray` argumenty a události nemají návratové hodnoty.  
  
 Událost `PercentDone` je vyvolána metodou `LongTask` třídy `Widget`. `LongTask` přebírá dva argumenty: dobu, po kterou metoda zamýšlí pracovat, a minimální časový interval před tím, než `LongTask` pozastavení vyvolá událost `PercentDone`.  
  
#### <a name="to-raise-the-percentdone-event"></a>Vyvolání události PercentDone  
  
1. Chcete-li zjednodušit přístup k vlastnosti `Timer` používané touto třídou, přidejte příkaz `Imports` na začátek oddílu deklarace v rámci vašeho modulu třídy, nad příkaz `Class Widget`.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. Do `Widget` třídy přidejte následující kód:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Když vaše aplikace volá metodu `LongTask`, třída `Widget` vyvolá událost `PercentDone` každých `MinimumInterval` sekund. Po návratu události `LongTask` zkontroluje, zda byl argument `Cancel` nastaven na hodnotu `True`.  
  
 Tady je potřeba pár omezení. Pro zjednodušení `LongTask`ý postup předpokládá, že jste předem věděli, jak dlouho bude úkol trvat. To téměř nikdy neplatí. Rozdělování úkolů do bloků rovnoměrné velikosti může být obtížné a často se jedná o většinu uživatelů, což je jednoduše doba, která se předá před tím, než získá indikaci, že se něco děje.  
  
 V této ukázce jste pravděpodobně spottedi jinou chybu. Vlastnost `Timer` vrátí počet sekund, které uplynuly od půlnoci; Proto se aplikace zablokuje, pokud je spuštěná těsně před půlnocí. Opatrnější přístup k měření času by vyžadoval podmínky hranice, jako je to v úvahu, nebo jejich zcela neřešitelné pomocí vlastností, jako je `Now`.  
  
 Teď, když `Widget` třída může vyvolávat události, můžete přejít k dalšímu návodu. [Návod: zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) ukazuje, jak použít `WithEvents` k přidružení obslužné rutiny události `PercentDone` události.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [Návod: Zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)
