---
title: "Události (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 10213597fa65c44a56b30c37e2e6f4e732d96954
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="events-visual-basic"></a>Události (Visual Basic)
Při může vizualizovat [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] projektu jako řadu postupů, které jsou spouštěny v pořadí, ve skutečnosti většiny programů, jsou události řízené – znamená tok provádění je dáno externí výskytů názvem *události*.  
  
 Událost je signál, která informuje o aplikaci, která něco důležité došlo k chybě. Například když uživatel klikne na ovládací prvek na formuláři, formuláře může být spojeno `Click` událostí a volání procedury, která zpracovává událost. Události povolit také samostatné úkoly ke komunikaci. Řekněme například, že aplikace provede úlohu řazení samostatně v hlavní aplikaci. Pokud uživatel zruší řazení, vaše aplikace může odesílat události cancel instruující proces řazení zastavit.  
  
## <a name="event-terms-and-concepts"></a>Událost podmínky a koncepty  
 Tato část popisuje podmínky a koncepty používané s událostmi v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
### <a name="declaring-events"></a>Deklarace událostí  
 Deklarování událostí v rámci třídy, struktury, moduly a rozhraní pomocí `Event` – klíčové slovo, jako v následujícím příkladu:  
  
 [!code-vb[VbVbalrEvents#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_1.vb)]  
  
### <a name="raising-events"></a>Vyvolání událostí  
 Událost je jako zprávu oznamující, že něco důležité došlo k chybě. Je volána v rámci všesměrové vysílání zprávy *vyvolání* události. V [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], vyvolávání událostí s `RaiseEvent` příkaz jako v následujícím příkladu:  
  
 [!code-vb[VbVbalrEvents#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_2.vb)]  
  
 Události musí být vyvolány v rámci oboru třídu, modul nebo struktura, kde jsou deklarovány. Například do odvozené třídy nemohou vyvolat události zděděn ze základní třídy.  
  
### <a name="event-senders"></a>Odesílatelé událostí  
 Jakýkoli objekt podporující vyvolání události je *událostí odesílatele*, také známé jako *zdroj události*. Formuláře, ovládací prvky a uživatelem definované objekty jsou příklady odesílatelé událostí.  
  
### <a name="event-handlers"></a>Obslužné rutiny událostí  
 *Obslužné rutiny událostí* postupy, které se nazývají případě je odpovídající událost. Můžete vytvořit žádné platné podprogramu s odpovídajícím podpisem jako obslužnou rutinu události. Funkci nelze však použít jako obslužnou rutinu události, protože jej nelze vrátit hodnotu ke zdroji událostí.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]používá standardní zásady vytváření názvů pro obslužné rutiny událostí, které kombinuje název odesílatele událostí, podtržítko, název události. Například `Click` událostí tlačítko s názvem `button1` by s názvem `Sub button1_Click`.  
  
> [!NOTE]
>  Doporučujeme použít tyto zásady vytváření názvů při definování obslužné rutiny události pro vlastní události, ale není nutné; můžete použít libovolný platný podprogramu název.  
  
## <a name="associating-events-with-event-handlers"></a>Přidružení událostí k obslužné rutiny událostí  
 Předtím, než obslužná rutina události použitelný, je třeba nejprve přidružit ho k události pomocí `Handles` nebo `AddHandler` příkaz.  
  
### <a name="withevents-and-the-handles-clause"></a>WithEvents a klauzule Handles  
 `WithEvents` Příkaz a `Handles` klauzule poskytují deklarativní způsob zadávání obslužné rutiny událostí. Událost vyvolaná objektem deklarovat s `WithEvents` – klíčové slovo lze zpracovat žádné procedurou s `Handles` příkaz pro tuto událost, jak je znázorněno v následujícím příkladu:  
  
 [!code-vb[VbVbalrEvents#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_3.vb)]  
  
 `WithEvents` Příkaz a `Handles` klauzule jsou často nejlepší volbou pro obslužné rutiny událostí protože deklarativní syntaxi používají usnadňuje zpracování událostí do kódu, přečtěte si a ladění. Nicméně, mějte na paměti následující omezení na použití `WithEvents` proměnné:  
  
-   Nelze použít `WithEvents` proměnné jako objektovou proměnnou. To znamená, nelze jej jako deklarovat `Object`– při deklarovat proměnnou musíte zadat název třídy.  
  
-   Protože sdílené události nejsou svázané s instancí třídy, nemůžete použít `WithEvents` deklarativně zpracování sdílené událostí. Podobně nelze použít `WithEvents` nebo `Handles` ke zpracování událostí z `Structure`. V obou případech můžete použít `AddHandler` příkaz ke zpracování těchto událostí.  
  
-   Nelze vytvořit pole `WithEvents` proměnné.  
  
 `WithEvents`Proměnné umožňují jedné obslužné rutině událostí zpracovat jeden nebo více druh událostí nebo jeden nebo více obslužných rutin událostí pro zpracování je stejný typ události.  
  
 I když `Handles` klauzule standardní způsob přiřazení událost obslužnou rutinu, je omezený na přidružení událostí k obslužné rutiny událostí v době kompilace.  
  
 V některých případech například s událostmi přidružené formuláře nebo ovládací prvky, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automaticky zástupných procedur se prázdné obslužné rutiny a přidruží ji k události. Například když dvakrát kliknete na příkaz tlačítko ve formuláři v režimu návrhu, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vytvoří prázdné obslužné rutiny a `WithEvents` proměnné příkazového tlačítka, jako v následujícím kódu:  
  
 [!code-vb[VbVbalrEvents#26](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_4.vb)]  
  
### <a name="addhandler-and-removehandler"></a>AddHandler a RemoveHandler  
 `AddHandler` Je podobná příkazu `Handles` klauzuli v, že oba umožňují určit obslužné rutiny události. Ale `AddHandler`, používá se s `RemoveHandler`, poskytuje větší flexibilitu, než `Handles` klauzule, což umožňuje dynamicky přidat, odebrat a změňte obslužné rutiny události přidružený k události. Pokud chcete zpracovat sdílené události nebo události z strukturu, musíte použít `AddHandler`.  
  
 `AddHandler`přebírá dva argumenty: název události od odesílatele událostí například ovládací prvek a výraz, který se vyhodnotí jako delegáta. Není potřeba explicitně zadat třídu delegáta při použití `AddHandler`, protože `AddressOf` příkaz vždy vrátí odkaz na delegáta. Následující příklad přidruží obslužnou rutinu události vyvolané objektu:  
  
 [!code-vb[VbVbalrEvents#28](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_5.vb)]  
  
 `RemoveHandler`, který událost odpojí od obslužné rutiny události, používá stejnou syntaxi jako `AddHandler`. Příklad:  
  
 [!code-vb[VbVbalrEvents#29](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_6.vb)]  
  
 V následujícím příkladu obslužné rutiny události je přidruženo události a je aktivována událost. Obslužné rutiny události zachytává událost a zobrazí zprávu.  
  
 Pak se odebere první obslužná rutina události a obslužné rutiny různé události je přidruženo k události. Když znovu je vydána událost, se zobrazí různé zpráva.  
  
 Nakonec se odebere Druhá obslužná rutina události a třetí dobu se vyvolá událost. Protože je už přidružená k události obslužné rutiny události, nebyla provedena žádná akce.  
  
 [!code-vb[VbVbalrEvents#38](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_7.vb)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a>Zpracování událostí zděděn ze základní třídy  
 *Odvozené třídy*– třídy, které dědí vlastnosti ze základní třídy – dokáže zpracovat události vyvolané službou jejich základní třídy pomocí `Handles``MyBase` příkaz.  
  
#### <a name="to-handle-events-from-a-base-class"></a>Zpracování událostí ze základní třídy  
  
-   Deklarovat obslužné rutiny události v odvozené třídě přidáním `Handles MyBase.` *eventname* příkaz na řádek deklarace procedury vaší obslužné rutiny události, kde *eventname* je název události v základní třídy, které jsou zpracování. Příklad:  
  
     [!code-vb[VbVbalrEvents#12](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_8.vb)]  
  
## <a name="related-sections"></a>Související oddíly  
  
|Název|Popis|  
|-----------|-----------------|  
|[Návod: Deklarace a vyvolávání událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|Poskytuje podrobný popis toho, jak deklarace a vyvolávání událostí třídy.|  
|[Návod: Zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|Ukazuje, jak napsat proceduru obslužných rutin událostí.|  
|[Postupy: deklarování vlastních událostí k zabránění blokování](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|Ukazuje, jak definovat vlastní událost, která umožňuje jeho obslužné rutiny událostí k volání asynchronně.|  
|[Postupy: deklarování vlastních událostí pro konzervaci paměti](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|Ukazuje, jak definovat vlastní událost, která používá paměť jenom v případě, že se zpracovává událost.|  
|[Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|Jsou uvedeny běžné problémy, které nastat u obslužné rutiny událostí v zděděné součásti.|  
|[Události](../../../../standard/events/index.md)|Obsahuje základní informace o modelu událostí v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].|  
|[Vytváření obslužných rutin událostí v systému Windows Forms](../../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)|Popisuje, jak pracovat s události související s objekty Windows Forms.|  
|[Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)|Poskytuje přehled Delegáti v jazyce Visual Basic.|
