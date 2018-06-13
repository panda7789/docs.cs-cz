---
title: Zpracování a generování událostí
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- delegate model for events
- application development [.NET Framework], events
- events [.NET Framework]
ms.assetid: b6f65241-e0ad-4590-a99f-200ce741bb1f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbb7793c1c510c9b1b303e6b568f105a958c27cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578581"
---
# <a name="handling-and-raising-events"></a>Zpracování a generování událostí
Události v rozhraní .NET Framework jsou založené na modelu delegáta. Model delegátů následuje návrhový vzor pozorovatel, která umožňuje odběratele k registraci nebo dostávat oznámení od zprostředkovatele. Události odesílatele doručí oznámení, že došlo k události a přijímače událostí přijetí tohoto oznámení a definuje odpověď na něj. Tento článek popisuje hlavní součásti modelu delegáta, jak zpracovávat události v aplikacích a postupy implementace událostí v kódu.  
  
 Informace o zpracování událostí v aplikacích pro Windows 8.x Store najdete v tématu [přehled směrované události a události](/previous-versions/windows/apps/hh758286(v=win.10)).  
  
## <a name="events"></a>Události  
 Událost je zpráva odeslána objektem signál výskyt akce. Akce může být způsobeno interakci s uživatelem, například klikněte na tlačítko nebo může být aktivováno některé další program logiku, jako je například změna vlastnosti na hodnotu. Objekt, který vyvolá událost, se nazývá *odesílatele událostí*. Odesílatel událostí není známo, který objekt nebo metoda obdrží (zpracuje) události, které vyvolá. Událost je obvykle členem odesílatele událostí; například <xref:System.Web.UI.WebControls.Button.Click> událostí je členem skupiny <xref:System.Web.UI.WebControls.Button> třída a <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> událostí je členem skupiny třídu, která implementuje <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní.  
  
 Definujte událost pomocí `event` (v jazyku C#) nebo `Event` (v jazyce Visual Basic) – klíčové slovo v podpis událost třídy a zadejte typ delegát pro událost. Delegáti jsou popsané v další části.  
  
 Obvykle se vyvolat událost, přidáte metodu, která je označena jako `protected` a `virtual` (v jazyku C#) nebo `Protected` a `Overridable` (v jazyce Visual Basic). Název této metody `On` *EventName*, například `OnDataReceived`. Metoda by měla trvat jeden parametr, který určuje objekt data události. Poskytnete tuto metodu za účelem povolení odvozených tříd pro přepsání logiku pro vyvolání události. Odvozené třídě by měly volat vždy `On` *EventName* metoda základní třídy, chcete-li zajistit, že registrovaný Delegáti události.  
  
 Následující příklad ukazuje, jak deklarovat událost s názvem `ThresholdReached`. Událost je přidružena <xref:System.EventHandler> delegovat a vyvolá v metodu s názvem `OnThresholdReached`.  
  
 [!code-csharp[EventsOverview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Delegáty  
 Delegát je typ, který obsahuje odkaz na metodu. Delegát je deklarovaný s podpisem, který ukazuje návratový typ a parametry pro metody odkazuje a mohou obsahovat odkazy jenom na metody, které odpovídají podpis. Delegát je tedy ekvivalentní ukazatel na funkci zajišťující bezpečnost typů nebo zpětné volání. Deklarace delegáta stačí definovat třídu delegáta.  
  
 Delegáti mají mnoho používá v rozhraní .NET Framework. V kontextu události, delegát je prostředník (nebo mechanismus ukazatel) mezi zdroji událostí a kód, který zpracovává událost. Přidružíte delegáta událost zahrnutím typ delegáta v deklaraci události, jak je znázorněno v příkladu v předchozí části. Další informace o delegáti najdete v tématu <xref:System.Delegate> třídy.  
  
 Poskytuje rozhraní .NET Framework <xref:System.EventHandler> a <xref:System.EventHandler%601> delegáty pro podporu Většina scénářů událostí. Použití <xref:System.EventHandler> delegovat pro všechny události, které neobsahují data události. Použití <xref:System.EventHandler%601> delegovat pro události, které zahrnují data o události. Tyto delegáti nemají hodnotu návratový typ a proveďte dva parametry (objekt pro zdroj události) a objektu pro data události.  
  
 Delegáti jsou vícesměrové vysílání, což znamená, že mohou obsahovat odkazy na více než jedna metoda zpracování událostí. Podrobnosti najdete v tématu <xref:System.Delegate> stránka s referencemi k. Delegáti zajistit flexibilitu a jemně odstupňovanou kontrolu při zpracování událostí. Delegát funguje jako dispečer události pro třídu, která vyvolává událost seznam registrovaných obslužných rutin události pro událost.  
  
 Pro scénáře, kde <xref:System.EventHandler> a <xref:System.EventHandler%601> delegáti nefungují, můžete definovat delegáta. Scénáře, které vyžadují, abyste definovat delegáta jsou velmi výjimečných, například když, musíte pracovat se kód, který nebyl rozpoznán obecné typy. Označit delegáta s `delegate` v (C#) a `Delegate` (v jazyce Visual Basic) – klíčové slovo v deklaraci. Následující příklad ukazuje, jak deklarovat delegáta s názvem `ThresholdReachedEventHandler`.  
  
 [!code-csharp[EventsOverview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
 [!code-vb[EventsOverview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Data události  
 Data, která je přidruženo události lze zadat prostřednictvím třídu dat události. Rozhraní .NET Framework poskytuje mnoho událostí datových tříd, které můžete použít ve svých aplikacích. Například <xref:System.IO.Ports.SerialDataReceivedEventArgs> třídy je třída dat události pro <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType> událostí. Rozhraní .NET Framework odpovídá vzoru pro pojmenovávání ukončit všechny třídy data události s `EventArgs`. Můžete určit, které třída dat události je přidruženo události prohlížením delegát pro událost. Například <xref:System.IO.Ports.SerialDataReceivedEventHandler> zahrnuje delegáta <xref:System.IO.Ports.SerialDataReceivedEventArgs> třídy jako jeden z jeho parametrů.  
  
 <xref:System.EventArgs> Třída je základní typ pro všechny třídy data události. <xref:System.EventArgs> je také třída, kterou použijete při událost nemá všechna data související s ním. Při vytváření události, které je určeno pouze pro oznámení jiné třídy, které něco se stalo a není potřeba předat žádná data, zahrnout <xref:System.EventArgs> třída jako druhý parametr v delegát. Můžete předat <xref:System.EventArgs.Empty?displayProperty=nameWithType> hodnotu, pokud je k dispozici žádná data. <xref:System.EventHandler> Zahrnuje delegáta <xref:System.EventArgs> třída jako parametr.  
  
 Pokud chcete vytvořit třídu dat vlastní události, vytvořte třídu, která je odvozena z <xref:System.EventArgs>a pak zadejte žádné členy potřebné k předávání dat, která souvisí s události. Obvykle musí používat stejné vzoru pro pojmenovávání jako rozhraní .NET Framework a končit váš název třídy data události s `EventArgs`.  
  
 Následující příklad ukazuje třídu dat události s názvem `ThresholdReachedEventArgs`. Obsahuje vlastnosti, které jsou specifické pro událost se vyvolá.  
  
 [!code-csharp[EventsOverview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
 [!code-vb[EventsOverview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Obslužné rutiny událostí  
 Reagovat na událost, definujte metodu obslužné rutiny události v příjemce událostí. Tato metoda musí odpovídat podpis delegát pro událost, které jsou zpracování. Události obslužnou rutinu, můžete provést akce, které jsou potřeba při vyvolání události, jako je například shromažďování vstupu uživatele po kliknutí na tlačítko. Pokud chcete dostávat oznámení, když dojde k události, musí se vaše metoda obslužné rutiny události přihlásit k události.  
  
 Následující příklad ukazuje metodu obslužné rutiny události s názvem `c_ThresholdReached` odpovídající podpis pro <xref:System.EventHandler> delegovat. Metoda přihlásí k odběru `ThresholdReached` událostí.  
  
 [!code-csharp[EventsOverview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
 [!code-vb[EventsOverview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Statické a dynamické obslužné rutiny událostí  
 Rozhraní .NET Framework umožňuje odběratelům registraci pro oznamování událostí staticky nebo dynamicky. Obslužné rutiny statických událostí jsou platné po celou dobu životnosti třídy, jejíž události zpracovávají. Dynamické obslužné rutiny událostí jsou explicitně aktivovat a deaktivovat během spuštění programu, obvykle v reakci na podmíněnou logiku programu. Například můžete používají potřeby oznamování událostí pouze za určitých podmínek, nebo pokud aplikace obsahuje více obslužných rutin událostí a podmínky spuštění definovat odpovídající jeden používat. V příkladu v předchozí části ukazuje, jak chcete-li dynamicky přidat obslužné rutiny události. Další informace najdete v tématu [události](../../visual-basic/programming-guide/language-features/events/index.md) a [události](../../csharp/programming-guide/events/index.md).  
  
## <a name="raising-multiple-events"></a>Vyvolání více událostí  
 Pokud vaše třída vyvolá více událostí, kompilátor vygeneruje jedno pole pro každou instanci delegáta události. Pokud je velký počet událostí, nemusí být přijatelné náklady na úložiště jedno pole na každý delegáta. Pro tyto situace rozhraní .NET Framework poskytuje vlastnosti události můžete k uložení – delegáti událostí můžete použít jinou strukturu dat podle svého výběru.  
  
 Vlastnosti události se skládají z deklarace události doplněny přístupových objektů událostí. Přístupové objekty událostí jsou metody, které definujete, aby přidat nebo odebrat instancí delegáta událostí z datové struktury úložiště. Upozorňujeme, že jsou vlastnosti události pomalejší než pole události, protože každý delegát události musí být načtena předtím, než může být volána. Je nejvhodnější poměr mezi paměť a rychlost. Pokud vaše třída definuje mnoho událostí, které jsou vyvolávány, můžete implementovat vlastnosti události. Další informace najdete v tématu [postupy: zpracování více událostí pomocí vlastností události](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Vyvolávání a zpracovávání událostí](../../../docs/standard/events/how-to-raise-and-consume-events.md)|Obsahuje příklady vyvolání a pracovat s nimi události.|  
|[Postupy: Zpracování více událostí pomocí vlastností událostí](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md)|Ukazuje, jak pomocí vlastností události pro zpracování více událostí.|  
|[Návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern.md)|Popisuje návrhový vzor, který umožňuje odběratele k registraci nebo dostávat oznámení od zprostředkovatele.|  
|[Postupy: Zpracování událostí v aplikaci Web Forms](../../../docs/standard/events/how-to-consume-events-in-a-web-forms-application.md)|Ukazuje, jak zpracovat událost, která se vyvolá pomocí ovládacího prvku na webové formuláře.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.EventHandler>  
 <xref:System.EventHandler%601>  
 <xref:System.EventArgs>  
 <xref:System.Delegate>  
 [Události a přehled směrované události (aplikace UWP)](/windows/uwp/xaml-platform/events-and-routed-events-overview)  
 [Události (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)  
 [Události (programování průvodce v C#)](../../csharp/programming-guide/events/index.md)
