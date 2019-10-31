---
title: Zpracování a generování událostí
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- delegate model for events
- application development [.NET], events
- application development [.NET Framework], events
- application development [.NET Core], events
- events [.NET]
- events [.NET Core]
- events [.NET Framework]
ms.assetid: b6f65241-e0ad-4590-a99f-200ce741bb1f
ms.openlocfilehash: 67cba143957b50e8e8d7fa68e62b52775ca2f144
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131623"
---
# <a name="handling-and-raising-events"></a>Zpracování a vyvolávání událostí

Události v rozhraní .NET jsou založené na modelu delegáta. Model delegáta dodržuje [vzor návrhu pozorovatele](observer-design-pattern.md), který umožňuje předplatiteli zaregistrovat se a přijímat oznámení od poskytovatele. Odesílatel události vloží oznámení, že k události došlo, a příjemce události obdrží toto oznámení a definuje odpověď na ni. Tento článek popisuje hlavní komponenty modelu delegáta, způsob, jak spotřebovávat události v aplikacích a jak implementovat události v kódu.  
  
 Informace o zpracování událostí v aplikacích Windows 8. x Store najdete v tématu [Přehled událostí a směrovaných událostí](https://docs.microsoft.com/previous-versions/windows/apps/hh758286(v=win.10)).  
  
## <a name="events"></a>Události

Událost je zpráva odeslaná objektem k signalizaci výskytu akce. Tato akce může být způsobena zásahem uživatele, například kliknutím na tlačítko, nebo může být výsledkem některé jiné logiky programu, jako je například změna hodnoty vlastnosti. Objekt, který vyvolává událost, se nazývá *odesílatel události*. Odesílatel události neví, který objekt nebo metoda obdrží (zpracuje) události, které vyvolá. Událost je obvykle členem odesílatele události; Například událost <xref:System.Web.UI.WebControls.Button.Click> je členem třídy <xref:System.Web.UI.WebControls.Button> a událost <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> je členem třídy, která implementuje rozhraní <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
Chcete-li definovat událost, použijte C# [`event`](../../csharp/language-reference/keywords/event.md) nebo klíčové slovo [`Event`](../../visual-basic/language-reference/statements/event-statement.md) Visual Basic v signatuře třídy události a určete typ delegáta pro událost. Delegáti jsou popsáni v následující části.  
  
K vyvolání události obvykle přidáte metodu, která je označena jako `protected` a `virtual` (in C#) nebo `Protected` a `Overridable` (v Visual Basic). Pojmenování této metody `On`*EventName*; například `OnDataReceived`. Metoda by měla přijmout jeden parametr, který určuje datový objekt události, což je objekt typu <xref:System.EventArgs> nebo odvozený typ. Tuto metodu můžete zadat, chcete-li povolit odvozené třídy pro přepsání logiky pro vyvolání události. Odvozená třída by měla vždy volat metodu `On`*EventName* základní třídy, aby zajistila, že registrovaní delegáti obdrží událost.  

Následující příklad ukazuje, jak deklarovat událost s názvem `ThresholdReached`. Událost je přidružena k delegátu <xref:System.EventHandler> a vyvolána v metodě s názvem `OnThresholdReached`.  
  
 [!code-csharp[EventsOverview#1](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Delegáty

Delegát je typ, který obsahuje odkaz na metodu. Delegát je deklarován s signaturou, která zobrazuje návratový typ a parametry pro metody, na které odkazuje, a může uchovávat odkazy pouze na metody, které odpovídají jejímu podpisu. Delegát je tedy ekvivalentní k ukazateli funkce bezpečnému pro typ nebo zpětnému volání. Deklarace delegáta postačuje k definování třídy delegáta.  
  
Delegáti mají spoustu použití v .NET. V kontextu událostí delegát je zprostředkovatel (nebo mechanismus podobný ukazateli) mezi zdrojem události a kódem, který událost zpracovává. Delegáta můžete přidružit k události zahrnutím typu delegáta v deklaraci události, jak je znázorněno v příkladu v předchozí části. Další informace o delegátech naleznete v tématu Třída <xref:System.Delegate>.  
  
Rozhraní .NET poskytuje <xref:System.EventHandler> a <xref:System.EventHandler%601> delegáty pro podporu většiny scénářů událostí. Použijte delegáta <xref:System.EventHandler> pro všechny události, které neobsahují data události. Použijte delegáta <xref:System.EventHandler%601> pro události, které obsahují data o události. Tito Delegáti nemají žádnou hodnotu návratového typu a přebírají dva parametry (objekt pro zdroj události a objekt pro data události).  
  
Delegáti jsou [vícesměrové vysílání](xref:System.MulticastDelegate), což znamená, že mohou obsahovat odkazy na více než jednu metodu zpracování událostí. Podrobnosti najdete na stránce s referenčními informacemi pro <xref:System.Delegate>. Delegáti poskytují flexibilitu a jemně odstupňovaný ovládací prvek pro zpracování událostí. Delegát funguje jako dispečer události pro třídu, která vyvolává událost tím, že udržuje seznam registrovaných obslužných rutin událostí pro událost.  
  
U scénářů, kde Delegáti <xref:System.EventHandler> a <xref:System.EventHandler%601> nefungují, můžete definovat delegáta. Scénáře, které vyžadují, abyste definovali delegáta, jsou velmi vzácné, například když musíte pracovat s kódem, který nerozpozná obecné typy. Označíte delegáta pomocí C# klíčového slova [`delegate`](../../csharp/language-reference/keywords/delegate.md) a Visual Basic [`Delegate`](../../visual-basic/language-reference/statements/delegate-statement.md) v deklaraci. Následující příklad ukazuje, jak deklarovat delegáta s názvem `ThresholdReachedEventHandler`.  
  
[!code-csharp[EventsOverview#4](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
[!code-vb[EventsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Data události

Data přidružená k události lze poskytnout prostřednictvím třídy dat události. Rozhraní .NET poskytuje mnoho datových tříd událostí, které můžete použít ve svých aplikacích. Například třída <xref:System.IO.Ports.SerialDataReceivedEventArgs> je třída dat události pro událost <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType>. Rozhraní .NET se řídí vzorem pojmenování všech tříd dat událostí pomocí `EventArgs`. Určíte, která třída dat události je přidružena k události, a to tak, že se podíváte na delegáta události. Například delegát <xref:System.IO.Ports.SerialDataReceivedEventHandler> obsahuje třídu <xref:System.IO.Ports.SerialDataReceivedEventArgs> jako jeden z jeho parametrů.  
  
Třída <xref:System.EventArgs> je základní typ pro všechny třídy dat událostí. <xref:System.EventArgs> je také třída, kterou použijete v případě, že k události nejsou přidružena žádná data. Když vytvoříte událost, která má pouze upozornit jiné třídy, k nimž došlo, a není nutné předávat žádná data, zahrňte třídu <xref:System.EventArgs> jako druhý parametr delegáta. Pokud nejsou k dispozici žádná data, můžete hodnotu <xref:System.EventArgs.Empty?displayProperty=nameWithType> předat. Delegát <xref:System.EventHandler> obsahuje třídu <xref:System.EventArgs> jako parametr.  
  
Chcete-li vytvořit přizpůsobenou třídu dat události, vytvořte třídu, která je odvozena z <xref:System.EventArgs>, a poté poskytněte jakékoli členy potřebné k předání dat, která se vztahují k události. Obvykle byste měli použít stejný vzor pro pojmenování jako .NET a ukončit název třídy dat události pomocí `EventArgs`.  
  
Následující příklad ukazuje třídu dat události s názvem `ThresholdReachedEventArgs`. Obsahuje vlastnosti, které jsou specifické pro vyvolání události.  
  
[!code-csharp[EventsOverview#3](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
[!code-vb[EventsOverview#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Obslužné rutiny událostí

Chcete-li reagovat na událost, definujte metodu obslužné rutiny události v přijímači událostí. Tato metoda se musí shodovat s signaturou delegáta události, kterou zpracováváte. V obslužné rutině události provedete akce, které jsou požadovány při vyvolání události, jako je například shromažďování uživatelského vstupu, poté, co uživatel klikne na tlačítko. Chcete-li dostávat oznámení, když dojde k události, metoda obslužné rutiny události musí být přihlášena k odběru události.  
  
Následující příklad ukazuje metodu obslužné rutiny události s názvem `c_ThresholdReached`, která odpovídá podpisu pro <xref:System.EventHandler> delegáta. Metoda se přihlašuje k odběru události `ThresholdReached`.  
  
[!code-csharp[EventsOverview#2](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
[!code-vb[EventsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Statické a dynamické obslužné rutiny událostí  
 
.NET umožňuje předplatitelům registrovat se pro oznamování událostí staticky nebo dynamicky. Statické obslužné rutiny událostí jsou platné pro celou dobu života třídy, jejíž události zpracovávají. Dynamické obslužné rutiny událostí jsou explicitně aktivovány a dezaktivovány během provádění programu, obvykle v reakci na určitou logickou logiku programu. Můžete je například použít, pokud jsou oznámení o událostech nutná pouze za určitých podmínek nebo pokud aplikace poskytuje více obslužných rutin událostí a běhových podmínek definují příslušné rozhraní, které se má použít. Příklad v předchozím oddílu ukazuje, jak dynamicky přidat obslužnou rutinu události. Další informace naleznete v tématu [události](../../visual-basic/programming-guide/language-features/events/index.md) (v Visual Basic) a [události](../../csharp/programming-guide/events/index.md) (v C#).  
  
## <a name="raising-multiple-events"></a>Vyvolání více událostí  
 Pokud vaše třída vyvolá více událostí, kompilátor vygeneruje jedno pole pro každou instanci delegáta události. Pokud je počet událostí velký, nemusí být náklady na úložiště jednoho pole na delegáta přijatelné. V těchto situacích poskytuje .NET vlastnosti události, které můžete použít s jinou datovou strukturou dle vašeho výběru k ukládání delegátů událostí.  
  
 Vlastnosti události se skládají z deklarací událostí spolu s přístupovými objekty událostí. Přístupové objekty událostí jsou metody, které definujete pro přidání nebo odebrání instancí delegátů událostí z datové struktury úložiště. Všimněte si, že vlastnosti události jsou pomalejší než pole události, protože každý delegát události musí být načten předtím, než může být vyvolán. Kompromis mezi pamětí a rychlostí. Pokud vaše třída definuje mnoho událostí, které jsou zřídka vyvolány, budete chtít implementovat vlastnosti události. Další informace najdete v tématu [Postupy: zpracování více událostí pomocí vlastností události](how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Vyvolávání a zpracovávání událostí](how-to-raise-and-consume-events.md)|Obsahuje příklady vyvolání a využívání událostí.|  
|[Postupy: Zpracování více událostí pomocí vlastností událostí](how-to-handle-multiple-events-using-event-properties.md)|Ukazuje, jak používat vlastnosti událostí pro zpracování více událostí.|  
|[Návrhový vzor Pozorovatel](observer-design-pattern.md)|Popisuje vzor návrhu, který umožňuje předplatiteli zaregistrovat se a přijímat oznámení od poskytovatele.|  
|[Postupy: Zpracování událostí v aplikaci Web Forms](how-to-consume-events-in-a-web-forms-application.md)|Ukazuje, jak zpracovat událost, která je vyvolána ovládacím prvkem webového formuláře.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.EventHandler>
- <xref:System.EventHandler%601>
- <xref:System.EventArgs>
- <xref:System.Delegate>
- [Události (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)
- [Události (C# Průvodce programováním)](../../csharp/programming-guide/events/index.md)
- [Přehled událostí a směrovaných událostí (aplikace pro UWP)](/windows/uwp/xaml-platform/events-and-routed-events-overview)
