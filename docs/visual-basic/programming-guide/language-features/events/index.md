---
title: Události (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: 76d074d2870a2d7efa62516b5868cdd7faaacd79
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586707"
---
# <a name="events-visual-basic"></a>Události (Visual Basic)
Projekt sady Visual Studio může vizualizovat jako série postupů, které jsou spouštěny v pořadí, ve skutečnosti, většina programů jsou řízené událostmi – to znamená toku provádění se určuje podle externí výskyty volá *události*.  
  
 Událost je signál, který informuje aplikaci, která něco důležitého došlo k chybě. Například když uživatel klikne na ovládací prvek na formuláři, formuláře může vyvolat `Click` událostí a volání procedury, která zpracovává událost. Události umožňují samostatné úkoly ke komunikaci. Řekněme například, že vaše aplikace provede úlohu řazení odděleně od hlavní aplikace. Pokud uživatel zruší řazení, vaše aplikace může odesílat události cancel pokyny procesu řazení zastavit.  
  
## <a name="event-terms-and-concepts"></a>Událost terminologie a koncepty  
 Tato část popisuje podmínky a koncepty používané s událostmi v jazyce Visual Basic.  
  
### <a name="declaring-events"></a>Deklarace událostí  
 Deklarování událostí v rámci třídy, struktury, modulů a rozhraní, která používají `Event` – klíčové slovo, jako v následujícím příkladu:  
  
 [!code-vb[VbVbalrEvents#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#24)]  
  
### <a name="raising-events"></a>Vyvolávání událostí  
 Událost je jako zpráva oznamující, že něco důležitého došlo k chybě. Je volána v rámci vysílání zprávy *vyvolání* události. V jazyce Visual Basic vyvolat události `RaiseEvent` příkazu, jako v následujícím příkladu:  
  
 [!code-vb[VbVbalrEvents#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#25)]  
  
 Události musí být vyvolány v rámci oboru třídy, modulu nebo struktury, ve kterém jsou deklarovány. Například odvozené třídy nemohou vyvolat události zděděné ze základní třídy.  
  
### <a name="event-senders"></a>Odesílatelé událostí  
 Libovolný objekt, který je schopný vyvolání události je *odesílatele události*, označované také jako *zdroj události*. Forms, ovládací prvky a uživatelem definované objekty jsou příkladem odesílatelé událostí.  
  
### <a name="event-handlers"></a>Obslužné rutiny událostí  
 *Obslužné rutiny událostí* postupy, které jsou volány při výskytu odpovídající události. Můžete použít libovolný platný podprogram s odpovídající signaturou jako obslužné rutiny události. Funkci nelze však použít jako obslužnou rutinu události, protože ho nemůže vracet hodnotu ke zdroji události.  
  
 Jazyk Visual Basic používá standardní zásady vytváření názvů pro obslužné rutiny událostí, které kombinuje název odesílatele události, podtržítka a název události. Například `Click` události tlačítko s názvem `button1` by se pojmenoval `Sub button1_Click`.  
  
> [!NOTE]
>  Doporučujeme použít tyto zásady vytváření názvů při definování obslužné rutiny událostí pro vlastní události, ale není vyžadován. můžete použít libovolný název platný podprogram.  
  
## <a name="associating-events-with-event-handlers"></a>Přidružení událostí k obslužné rutiny událostí  
 Předtím, než obslužná rutina události použitelné, je třeba nejprve přidružit ho k události pomocí `Handles` nebo `AddHandler` příkazu.  
  
### <a name="withevents-and-the-handles-clause"></a>WithEvents a klauzule Handles  
 `WithEvents` Příkazu a `Handles` klauzule poskytují deklarativní způsob zadání obslužné rutiny událostí. Události vyvolané objektem deklarována s `WithEvents` – klíčové slovo mohou být zpracovány všechny procedury s `Handles` příkaz pro tuto událost, jak je znázorněno v následujícím příkladu:  
  
 [!code-vb[VbVbalrEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#1)]  
  
 `WithEvents` Příkazu a `Handles` klauzule jsou často nejlepší volbou pro obslužné rutiny událostí, protože deklarativní syntaxe používají usnadňuje zpracování událostí na kód, čtení a ladění. Nicméně, mějte na paměti následující omezení týkající se použití `WithEvents` proměnné:  
  
- Nelze použít `WithEvents` proměnné jako objektovou proměnnou. To znamená, nelze deklarovat jako `Object`– když deklarujete proměnnou se musí zadat název třídy.  
  
- Protože sdílené události nejsou vázané na instance třídy, nemůžete použít `WithEvents` deklarativně zpracování sdílené událostí. Podobně nelze použít `WithEvents` nebo `Handles` zpracování událostí z `Structure`. V obou případech můžete použít `AddHandler` příkaz pro zpracování těchto událostí.  
  
- Nelze vytvořit pole `WithEvents` proměnné.  
  
 `WithEvents` Proměnné umožňují jedinou událost obslužnou rutinu pro zpracování minimálně jeden typ události, nebo jeden nebo více obslužných rutin událostí ke zpracování stejný druh událostí.  
  
 I když `Handles` klauzule je standardní způsob přidružení událost k obslužné rutině události, je omezený na přidružení událostí k obslužné rutiny událostí v době kompilace.  
  
 V některých případech například s událostí spojených s formuláře nebo ovládací prvky, Visual Basic automaticky tříd stub si prázdné obslužné rutiny a přidruží ji k události. Například když dvakrát kliknete na příkazové tlačítko na formulář v režimu návrhu, Visual Basic vytvoří prázdné obslužné rutiny a `WithEvents` proměnné příkazového tlačítka, stejně jako v následujícím kódu:  
  
 [!code-vb[VbVbalrEvents#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#26)]  
  
### <a name="addhandler-and-removehandler"></a>Metody AddHandler a RemoveHandler  
 `AddHandler` Příkaz je podobný `Handles` klauzuli v, jak vám umožňují určit obslužnou rutinu události. Ale `AddHandler`, která se používá s `RemoveHandler`, poskytuje větší flexibilitu než `Handles` klauzule vám umožňuje dynamicky přidat, odebrat a změnit obslužnou rutinu události, který je přidružený k události. Pokud chcete zpracovávat události ze struktury nebo sdílené události, je nutné použít `AddHandler`.  
  
 `AddHandler` přebírá dva argumenty: název události od odesílatele události jako je například ovládací prvek a výraz, který se vyhodnotí jako delegát. Není potřeba explicitně zadat třídu delegáta při použití `AddHandler`, protože `AddressOf` příkaz vždy vrátí odkaz na delegáta. Následující příklad přidruží události vyvolané objektem obslužné rutiny události:  
  
 [!code-vb[VbVbalrEvents#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#28)]  
  
 `RemoveHandler`, který událost odpojení od obslužné rutiny události, používá stejnou syntaxi jako `AddHandler`. Příklad:  
  
 [!code-vb[VbVbalrEvents#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#29)]  
  
 V následujícím příkladu obslužná rutina události je přidružena k události a je vyvolána událost. Obslužná rutina události události zachytí a zobrazí zprávu.  
  
 Pak je odebrán první obslužná rutina události a obslužná rutina různé události je přidruženo k události. Při znovu vyvolání události se zobrazí různé zprávy.  
  
 Nakonec se odebere Druhá obslužná rutina události a třetí dobu se vyvolá událost. Protože je už přidružený k události obslužnou rutinu události, nedojde k žádné akci.  
  
 [!code-vb[VbVbalrEvents#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class2.vb#38)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a>Zpracování událostí zděděné ze základní třídy  
 *Odvozené třídy*– třídy, které dědí vlastnosti ze základní třídy – můžete zpracovávat události vyvolané službou své základní třídy pomocí `Handles MyBase` příkazu.  
  
### <a name="to-handle-events-from-a-base-class"></a>Zpracování událostí ze základní třídy  
  
- Deklarovat přidáním obslužné rutiny události v odvozené třídě `Handles MyBase.` *eventname* příkaz řádek deklaraci procedury Obslužná rutina události, kde *eventname* je název události v Základní třída, kterou obsluhujete. Příklad:  
  
     [!code-vb[VbVbalrEvents#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#12)]  
  
## <a name="related-sections"></a>Související oddíly  
  
|Název|Popis|  
|-----------|-----------------|  
|[Návod: Deklarace a vyvolávání událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|Poskytuje podrobný popis toho, jak deklarace a vyvolávání událostí třídy.|  
|[Návod: Zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|Ukazuje, jak napsat obslužnou rutinu události proceduru.|  
|[Postupy: Deklarování vlastních událostí k zabránění blokování](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|Ukazuje, jak definovat vlastní události, které umožňuje její obslužné rutiny událostí má být volána asynchronně.|  
|[Postupy: Deklarování vlastních událostí pro konzervaci paměti](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|Ukazuje, jak definovat vlastní událost, která používá jenom v případě, že se zpracovává událost paměti.|  
|[Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|Uvádí seznam běžných problémů, které vznikají u obslužných rutin událostí v zděděné součásti.|  
|[Události](../../../../standard/events/index.md)|Obsahuje přehled modelu události v rozhraní .NET Framework.|  
|[Vytváření obslužných rutin událostí ve Windows Forms](../../../../framework/winforms/creating-event-handlers-in-windows-forms.md)|Popisuje, jak pracovat s událostí spojených s objekty Windows Forms.|  
|[Delegáti](../../../../visual-basic/programming-guide/language-features/delegates/index.md)|Poskytuje přehled delegátů v jazyce Visual Basic.|
