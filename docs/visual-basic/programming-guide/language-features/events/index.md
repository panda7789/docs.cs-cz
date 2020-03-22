---
title: Akce
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: 666e138a747c480ef9e8b593f8c6233105fcdc93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400839"
---
# <a name="events-visual-basic"></a>Události (Visual Basic)
Zatímco můžete vizualizovat projekt sady Visual Studio jako řadu postupů, které se provádějí v pořadí, ve skutečnosti je většina programů řízena událostmi – což znamená, že tok provádění je určen externími výskyty nazývanými *události*.  
  
 Událost je signál, který informuje aplikaci, že došlo k něčemu důležitému. Pokud například uživatel klepne na ovládací prvek ve formuláři, může formulář vyvolat `Click` událost a volat proceduru, která událost zpracovává. Události také umožňují komunikaci samostatných úkolů. Řekněme například, že vaše aplikace provádí úlohu řazení odděleně od hlavní aplikace. Pokud uživatel zruší řazení, aplikace může odeslat událost zrušení pokyn proces řazení zastavit.  
  
## <a name="event-terms-and-concepts"></a>Podmínky a koncepty událostí  
 Tato část popisuje termíny a koncepty používané s událostmi v jazyce Visual Basic.  
  
### <a name="declaring-events"></a>Deklarace událostí  
 Deklarovat události v rámci třídy, struktury, `Event` moduly a rozhraní pomocí klíčového slova, jako v následujícím příkladu:  
  
 [!code-vb[VbVbalrEvents#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#24)]  
  
### <a name="raising-events"></a>Zvyšování událostí  
 Událost je jako zpráva oznamující, že došlo k něčemu důležitému. Akt vysílání zprávy se nazývá *vyvolání* události. V jazyce Visual Basic `RaiseEvent` můžete vyvolat události s příkazem, jako v následujícím příkladu:  
  
 [!code-vb[VbVbalrEvents#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#25)]  
  
 Události musí být vyvolány v rámci třídy, modulu nebo struktury, kde jsou deklarovány. Například odvozené třídy nemůže vyvolat události zděděné ze základní třídy.  
  
### <a name="event-senders"></a>Odesílatelé událostí  
 Libovolný objekt, který může vyvolat událost, je *odesílatel událostí*, označovaný také jako *zdroj události*. Formuláře, ovládací prvky a uživatelem definované objekty jsou příklady odesílatelů událostí.  
  
### <a name="event-handlers"></a>Obslužné rutiny událostí  
 *Obslužné rutiny událostí jsou procedury,* které jsou volány při výskytu odpovídající události. Jako obslužnou rutinu události můžete použít libovolný platný podprogram s odpovídajícím podpisem. Funkci však nelze použít jako obslužnou rutinu události, protože nemůže vrátit hodnotu zdroji události.  
  
 Visual Basic používá standardní konvence pojmenování pro obslužné rutiny událostí, který kombinuje název odesílatele události, podtržítko a název události. Například `Click` událost tlačítka s `button1` názvem by `Sub button1_Click`se s názvem .  
  
> [!NOTE]
> Doporučujeme použít tuto konvenci pojmenování při definování obslužné rutiny událostí pro vlastní události, ale není to nutné; můžete použít libovolný platný název podprogramu.  
  
## <a name="associating-events-with-event-handlers"></a>Přisuzování událostí k obslužným rutinám událostí  
 Před obslužná rutina události se stane použitelným, `Handles` `AddHandler` musíte nejprve přidružit k události pomocí příkazu nebo.  
  
### <a name="withevents-and-the-handles-clause"></a>WithEvents a klauzule popisovače  
 Příkaz `WithEvents` a `Handles` klauzule poskytují deklarativní způsob určení obslužné rutiny událostí. Událost vyzdvižená objektem deklarovaným klíčovým slovem `WithEvents` může být zpracována libovolným postupem s příkazem `Handles` pro tuto událost, jak je znázorněno v následujícím příkladu:  
  
 [!code-vb[VbVbalrEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#1)]  
  
 Příkaz `WithEvents` a `Handles` klauzule jsou často nejlepší volbou pro obslužné rutiny událostí, protože deklarativní syntaxe, kterou používají, usnadňuje zpracování událostí kódu, čtení a ladění. Mějte však na paměti následující omezení `WithEvents` používání proměnných:  
  
- Proměnnou `WithEvents` nelze použít jako proměnnou objektu. To znamená, že jej `Object`nelze deklarovat jako – při deklarování proměnné je nutné zadat název třídy.  
  
- Vzhledem k tomu, že sdílené události `WithEvents` nejsou vázány na instance třídy, nelze použít k deklarativně zpracování sdílených událostí. Podobně nelze použít `WithEvents` nebo `Handles` zpracovat události `Structure`z . V obou případech můžete `AddHandler` použít příkaz ke zpracování těchto událostí.  
  
- Nelze vytvořit pole `WithEvents` proměnných.  
  
 `WithEvents`proměnné umožňují jedné obslužné rutině události zpracovat jeden nebo více druhů událostí nebo jeden nebo více obslužných rutin událostí pro zpracování stejného druhu události.  
  
 Přestože `Handles` klauzule je standardní způsob asociace události s obslužnou rutinou události, je omezena na asociaci událostí s obslužnými rutinami událostí v době kompilace.  
  
 V některých případech, například s událostmi přidruženými k formulářům nebo ovládacím prvkům, visual basic automaticky vytvoří zakázaný kód prázdnou obslužnou rutinu události a přidruží ji k události. Pokud například poklepete na příkazové tlačítko ve formuláři v návrhovém `WithEvents` režimu, vytvoří jazyk Visual Basic prázdnou obslužnou rutinu události a proměnnou pro příkazové tlačítko, jako v následujícím kódu:  
  
 [!code-vb[VbVbalrEvents#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#26)]  
  
### <a name="addhandler-and-removehandler"></a>AddHandler a RemoveHandler  
 Příkaz `AddHandler` je podobný `Handles` klauzuli v tom, že oba umožňují zadat obslužnou rutinu události. Však `AddHandler`, `RemoveHandler`používá s , poskytuje `Handles` větší flexibilitu než klauzule, což umožňuje dynamicky přidávat, odebírat a měnit obslužnou rutinu události přidružené k události. Pokud chcete zpracovávat sdílené události nebo události ze `AddHandler`struktury, musíte použít .  
  
 `AddHandler`trvá dva argumenty: název události od odesílatele události, jako je například ovládací prvek a výraz, který je vyhodnocen delegát. Při použití `AddHandler`není nutné explicitně zadávat třídu delegáta , protože `AddressOf` příkaz vždy vrací odkaz na delegáta. Následující příklad přidruží obslužnou rutinu události k události vyvolané objektem:  
  
 [!code-vb[VbVbalrEvents#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#28)]  
  
 `RemoveHandler`, který odpojí událost od obslužné rutiny události, používá stejnou syntaxi jako `AddHandler`. Například:  
  
 [!code-vb[VbVbalrEvents#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#29)]  
  
 V následujícím příkladu je obslužná rutina události přidružena k události a událost je vyvolána. Obslužná rutina události zachytí událost a zobrazí zprávu.  
  
 Potom je odebrána první obslužná rutina události a k události je přidružena jiná obslužná rutina události. Při znovu vyvolání události se zobrazí jiná zpráva.  
  
 Nakonec druhá obslužná rutina události je odebrána a událost je vyvolána potřetí. Vzhledem k tomu, že již není k události přidružena obslužná rutina události, není provedena žádná akce.  
  
 [!code-vb[VbVbalrEvents#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class2.vb#38)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a>Zpracování událostí zděděných ze základní třídy  
 *Odvozené třídy*– třídy, které dědí vlastnosti ze základní `Handles MyBase` třídy – mohou zpracovávat události vyvolané jejich základní třídou pomocí příkazu.  
  
### <a name="to-handle-events-from-a-base-class"></a>Zpracování událostí ze základní třídy  
  
- Deklarujte obslužnou rutinu události v odvozené třídě přidáním příkazu `Handles MyBase.` *eventname* do řádku deklarace procedury obslužné rutiny události, kde název *události* v základní třídě, kterou zpracováváte. Například:  
  
     [!code-vb[VbVbalrEvents#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#12)]  
  
## <a name="related-sections"></a>Související oddíly  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Návod: Deklarace a vyvolávání událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|Obsahuje podrobný popis, jak deklarovat a vyvolávat události pro třídu.|  
|[Návod: Zpracování událostí](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|Ukazuje, jak napsat proceduru obslužné rutiny události.|  
|[Postupy: Deklarování vlastních událostí k zabránění blokování](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|Ukazuje, jak definovat vlastní událost, která umožňuje jeho obslužné rutiny událostí, které mají být volány asynchronně.|  
|[Postupy: Deklarování vlastních událostí pro konzervaci paměti](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|Ukazuje, jak definovat vlastní událost, která používá paměť pouze při zpracování události.|  
|[Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|Uvádí běžné problémy, které vznikají s obslužnými rutinami událostí v zděděných součástech.|  
|[Akce](../../../../standard/events/index.md)|Obsahuje přehled modelu události v rozhraní .NET Framework.|  
|[Vytváření obslužných rutin událostí ve Windows Forms](../../../../framework/winforms/creating-event-handlers-in-windows-forms.md)|Popisuje, jak pracovat s událostmi přidruženými k objektům windows forms.|  
|[Delegáty](../../../../visual-basic/programming-guide/language-features/delegates/index.md)|Obsahuje přehled delegátů v jazyce Visual Basic.|
