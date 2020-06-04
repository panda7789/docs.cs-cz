---
title: Události
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: c61e960078557282de39bdc30f1d614ce8a77f29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405116"
---
# <a name="events-visual-basic"></a>Události (Visual Basic)
I když může být projekt sady Visual Studio vizualizuje jako série procedur, které jsou spouštěny v sekvenci, je ve skutečnosti řízeno událostmi, což znamená, že tok provádění je určen externími výskyty nazývanými *události*.  
  
 Událost je signál, který informuje aplikaci, že došlo k nějaké důležitosti. Například když uživatel klikne na ovládací prvek ve formuláři, může formulář vyvolat `Click` událost a zavolat proceduru, která událost zpracovává. Události také umožňují komunikaci mezi různými úkoly. Řekněme například, že vaše aplikace provádí řazení úkolů odděleně od hlavní aplikace. Pokud uživatel zruší řazení, může aplikace odeslat událost zrušení pokynu k zastavení procesu řazení.  
  
## <a name="event-terms-and-concepts"></a>Výrazy a koncepty událostí  
 Tato část popisuje pojmy a koncepty používané s událostmi v Visual Basic.  
  
### <a name="declaring-events"></a>Deklarace událostí  
 Události deklarujete ve třídách, strukturách, modulech a rozhraních pomocí `Event` klíčového slova, jako v následujícím příkladu:  
  
 [!code-vb[VbVbalrEvents#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#24)]  
  
### <a name="raising-events"></a>Vyvolávání událostí  
 Událost je jako zpráva oznamující, že došlo k nějaké důležitosti. Zpráva o vysílání zprávy se nazývá *vyvolání* události. V Visual Basic události vyvoláte pomocí `RaiseEvent` příkazu, jako v následujícím příkladu:  
  
 [!code-vb[VbVbalrEvents#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#25)]  
  
 Události musí být vyvolány v rozsahu třídy, modulu nebo struktury, kde jsou deklarovány. Například odvozená třída nemůže vyvolat události děděné ze základní třídy.  
  
### <a name="event-senders"></a>Odesílatelé událostí  
 Libovolný objekt schopný vyvolání události je *odesílatel události*, označovaný také jako *zdroj události*. Příklady odesílatelů událostí jsou formuláře, ovládací prvky a uživatelem definované objekty.  
  
### <a name="event-handlers"></a>Obslužné rutiny událostí  
 *Obslužné rutiny událostí* jsou procedury, které jsou volány při výskytu odpovídající události. Můžete použít jakoukoli platnou podprogram s vyhovující signaturou jako obslužnou rutinu události. Funkci nelze použít jako obslužnou rutinu události, protože ale nemůže vrátit hodnotu do zdroje událostí.  
  
 Visual Basic používá standardní zásady vytváření názvů pro obslužné rutiny událostí, které kombinují jméno odesílatele události, podtržítko a název události. Například `Click` Událost tlačítka s názvem `button1` by měla být pojmenována `Sub button1_Click` .  
  
> [!NOTE]
> Doporučujeme používat tyto zásady vytváření názvů při definování obslužných rutin událostí pro vlastní události, ale není to nutné. můžete použít libovolný platný název subrutiny.  
  
## <a name="associating-events-with-event-handlers"></a>Přidružení událostí k obslužným rutinám událostí  
 Předtím, než může být obslužná rutina události použitelná, je nutné ji nejprve přidružit k události `Handles` pomocí `AddHandler` příkazu nebo.  
  
### <a name="withevents-and-the-handles-clause"></a>WithEvents a klauzule Handles  
 `WithEvents`Příkaz a `Handles` klauzule poskytují deklarativní způsob určení obslužných rutin událostí. Událost aktivovaná objektem deklarovaným pomocí `WithEvents` klíčového slova může být zpracována jakýmkoli postupem s `Handles` příkazem pro danou událost, jak je znázorněno v následujícím příkladu:  
  
 [!code-vb[VbVbalrEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#1)]  
  
 `WithEvents`Příkaz a `Handles` klauzule jsou často nejlepší volbou pro obslužné rutiny událostí, protože deklarativní syntaxe, kterou používají, zjednodušuje kód, číst a ladit. Mějte ale na paměti následující omezení pro použití `WithEvents` proměnných:  
  
- Proměnnou nelze použít `WithEvents` jako proměnnou objektu. To znamená, že jej nelze deklarovat jako `Object` – při deklaraci proměnné je nutné zadat název třídy.  
  
- Vzhledem k tomu, že sdílené události nejsou svázány s instancemi třídy, nelze použít `WithEvents` k deklarativnímu zpracování sdílených událostí. Podobně nemůžete použít `WithEvents` nebo `Handles` pro zpracování událostí z `Structure` . V obou případech můžete pomocí `AddHandler` příkazu tyto události zpracovat.  
  
- Nemůžete vytvořit pole `WithEvents` proměnných.  
  
 `WithEvents`proměnné umožňují jedné obslužné rutině události zpracovat jeden nebo více typů události nebo jednu nebo více obslužných rutin událostí pro zpracování stejného typu události.  
  
 I když `Handles` je klauzule standardní způsob, jak přidružit událost k obslužné rutině události, je omezena na přidružení událostí s obslužnými rutinami události v době kompilace.  
  
 V některých případech, například s událostmi přidruženými k formulářům nebo ovládacím prvkům, Visual Basic automaticky odblokovat prázdnou obslužnou rutinu události a přidruží ji k události. Například když dvakrát kliknete na příkazové tlačítko ve formuláři v režimu návrhu, Visual Basic vytvoří prázdnou obslužnou rutinu události a `WithEvents` proměnnou pro příkazové tlačítko, jak je uvedeno v následujícím kódu:  
  
 [!code-vb[VbVbalrEvents#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#26)]  
  
### <a name="addhandler-and-removehandler"></a>AddHandler a RemoveHandler  
 `AddHandler`Příkaz je podobný `Handles` klauzuli v tom, že umožňuje zadat obslužnou rutinu události. Nicméně `AddHandler` , používá se s `RemoveHandler` , poskytuje větší flexibilitu než `Handles` klauzule, což vám umožní dynamicky přidávat, odebírat a měnit obslužné rutiny událostí přidružené k události. Pokud chcete zpracovávat sdílené události nebo události ze struktury, je nutné použít `AddHandler` .  
  
 `AddHandler`přebírá dva argumenty: název události od odesílatele události, jako je například ovládací prvek, a výraz, který je vyhodnocen jako delegát. Třídu delegáta není nutné explicitně určovat při použití `AddHandler` , protože `AddressOf` příkaz vždy vrací odkaz na delegáta. Následující příklad přidruží obslužnou rutinu události k události vyvolané objektem:  
  
 [!code-vb[VbVbalrEvents#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#28)]  
  
 `RemoveHandler`, který odpojuje událost od obslužné rutiny události, používá stejnou syntaxi jako `AddHandler` . Příklad:  
  
 [!code-vb[VbVbalrEvents#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#29)]  
  
 V následujícím příkladu je obslužná rutina události přidružena k události a událost je vyvolána. Obslužná rutina události zachytí událost a zobrazí zprávu.  
  
 Pak je první obslužná rutina události odebrána a k události je přidružena jiná obslužná rutina události. Po opětovném vyvolání události se zobrazí jiná zpráva.  
  
 Nakonec se druhá obslužná rutina události odebere a událost se vygeneruje po dobu třetího času. Vzhledem k tomu, že k události již není přidružena obslužná rutina události, není provedena žádná akce.  
  
 [!code-vb[VbVbalrEvents#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class2.vb#38)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a>Zpracování událostí zděděných ze základní třídy  
 *Odvozené třídy*– třídy, které dědí vlastnosti ze základní třídy, mohou zpracovávat události vyvolané jejich základní třídou pomocí `Handles MyBase` příkazu.  
  
### <a name="to-handle-events-from-a-base-class"></a>Zpracování událostí ze základní třídy  
  
- Deklarujte obslužnou rutinu události v odvozené třídě přidáním příkazu `Handles MyBase.` *EventName* do řádku deklarace procedury obslužné rutiny události, kde *EventName* je název události v základní třídě, kterou zpracováváte. Příklad:  
  
     [!code-vb[VbVbalrEvents#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#12)]  
  
## <a name="related-sections"></a>Související oddíly  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Návod: Deklarace a vyvolávání událostí](walkthrough-declaring-and-raising-events.md)|Poskytuje podrobný popis způsobu, jak deklarovat a vyvolat události pro třídu.|  
|[Návod: Zpracování událostí](walkthrough-handling-events.md)|Ukazuje, jak napsat proceduru obslužné rutiny události.|  
|[Postupy: Deklarování vlastních událostí k zabránění blokování](how-to-declare-custom-events-to-avoid-blocking.md)|Ukazuje, jak definovat vlastní událost, která umožňuje, aby obslužné rutiny události byly volány asynchronně.|  
|[Postupy: Deklarování vlastních událostí pro konzervaci paměti](how-to-declare-custom-events-to-conserve-memory.md)|Ukazuje, jak definovat vlastní událost, která používá paměť pouze v případě, že je událost zpracována.|  
|[Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](troubleshooting-inherited-event-handlers.md)|Uvádí běžné problémy, které vznikají u obslužných rutin událostí ve zděděných součástech.|  
|[Události](../../../../standard/events/index.md)|Obsahuje přehled modelu události v rozhraní .NET Framework.|  
|[Vytváření obslužných rutin událostí ve Windows Forms](../../../../framework/winforms/creating-event-handlers-in-windows-forms.md)|Popisuje, jak pracovat s událostmi přidruženými k objektům model Windows Forms.|  
|[Delegáti](../delegates/index.md)|Poskytuje přehled o delegátech v Visual Basic.|
