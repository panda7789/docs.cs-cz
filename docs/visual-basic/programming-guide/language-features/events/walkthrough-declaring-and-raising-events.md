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
ms.openlocfilehash: 3da60014d7ac95189c5d56c3e339ff1b054a40dc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405090"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>Návod: Deklarace a vyvolávání událostí (Visual Basic)
Tento návod ukazuje, jak deklarovat a vyvolat události pro třídu s názvem `Widget` . Po dokončení kroků si můžete přečíst doprovodné téma, [Návod: zpracování událostí](walkthrough-handling-events.md), které ukazuje, jak používat události z `Widget` objektů k poskytnutí informací o stavu v aplikaci.  
  
## <a name="the-widget-class"></a>Widget – třída  
 Předpokládejme, kdy máte `Widget` třídu. Vaše `Widget` Třída má metodu, která může trvat dlouhou dobu, a chcete, aby aplikace mohla sestavit nějaký typ indikátoru dokončení.  
  
 Samozřejmě je možné nastavit, aby se v `Widget` objektu zobrazilo dialogové okno procento dokončení, ale pak byste zablokovali toto dialogové okno v každém projektu, ve kterém jste použili `Widget` třídu. Dobrým principem návrhu objektu je umožnit aplikaci, která používá objekt, zpracovat uživatelské rozhraní – Pokud celý účel objektu není spravovat formulář nebo dialogové okno.  
  
 Účelem `Widget` je provést jiné úkoly, takže je lepší přidat `PercentDone` událost a nechat proceduru, která volá `Widget` metody, zpracovávat tuto událost a zobrazovat aktualizace stavu. `PercentDone`Událost může také poskytovat mechanismus pro zrušení úlohy.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Postup sestavení příkladu kódu pro toto téma  
  
1. Otevřete nový Visual Basic projekt aplikace pro Windows a vytvořte formulář s názvem `Form1` .  
  
2. Přidejte dvě tlačítka a popisky do `Form1` .  
  
3. Pojmenujte objekty, jak je uvedeno v následující tabulce.  
  
    |Objekt|Vlastnost|Nastavení|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Spustit úkol|  
    |`Button2`|`Text`|Zrušit|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. V nabídce **projekt** vyberte možnost **Přidat třídu** a přidejte do projektu třídu s názvem `Widget.vb` .  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Deklarace události pro třídu widgetu  
  
- Použijte `Event` klíčové slovo k deklaraci události ve `Widget` třídě. Všimněte si, že událost může `ByVal` mít `ByRef` argumenty a a `Widget` jako `PercentDone` událost ukazuje:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Když volající objekt obdrží `PercentDone` událost, `Percent` argument obsahuje procento dokončeného úkolu. `Cancel`Argument lze nastavit na hodnotu `True` , chcete-li zrušit metodu, která událost vyvolala.  
  
> [!NOTE]
> Argumenty události lze deklarovat stejně jako argumenty procedur, s následujícími výjimkami: události nemohou mít `Optional` `ParamArray` argumenty nebo a události nemají návratové hodnoty.  
  
 `PercentDone`Událost je vyvolána `LongTask` metodou `Widget` třídy. `LongTask`přebírá dva argumenty: dobu, po kterou metoda zamýšlí pracovat, a minimální časový interval před `LongTask` pauzou pro vyvolání `PercentDone` události.  
  
#### <a name="to-raise-the-percentdone-event"></a>Vyvolání události PercentDone  
  
1. Chcete-li zjednodušit přístup k `Timer` vlastnosti, kterou používá tato třída, přidejte `Imports` příkaz na začátek oddílu deklarace v modulu třídy nad rámec `Class Widget` příkazu.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. Do třídy přidejte následující kód `Widget` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Když vaše aplikace volá `LongTask` metodu, `Widget` Třída vyvolá `PercentDone` událost každou `MinimumInterval` sekundou. Jakmile se událost vrátí, `LongTask` zkontroluje, zda `Cancel` byl argument nastaven na hodnotu `True` .  
  
 Tady je potřeba pár omezení. V zájmu jednoduchosti `LongTask` postup předpokládá, že jste předem věděli, jak dlouho bude úkol trvat. To téměř nikdy neplatí. Rozdělování úkolů do bloků rovnoměrné velikosti může být obtížné a často se jedná o většinu uživatelů, což je jednoduše doba, která se předá před tím, než získá indikaci, že se něco děje.  
  
 V této ukázce jste pravděpodobně spottedi jinou chybu. `Timer`Vlastnost vrátí počet sekund, které byly předány od půlnoci. proto je aplikace zablokovaná, pokud je spuštěna těsně před půlnocí. Lepším přístupem k měření času by došlo k tomu, že se jedná o podmínky pro hranici, jako je to vhodné, nebo se jim vyhnete úplně, a to pomocí vlastností jako `Now` .  
  
 Teď, `Widget` když třída může vyvolávat události, můžete přejít k dalšímu návodu. [Návod: zpracování událostí](walkthrough-handling-events.md) ukazuje, jak použít `WithEvents` k přidružení obslužné rutiny události k `PercentDone` události.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [Návod: Zpracování událostí](walkthrough-handling-events.md)
- [Události](index.md)
