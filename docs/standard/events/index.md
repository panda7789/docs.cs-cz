---
title: Zpracování a generování událostí
description: Naučte se zpracovávat a přivolávat události .NET, které jsou založené na modelu delegáta. Tento model umožňuje předplatitelům registrovat se nebo přijímat oznámení od zprostředkovatelů.
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
ms.openlocfilehash: 8cf0ff323e9bf7305e3d9cbb6dabd8f685059e97
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447105"
---
# <a name="handling-and-raising-events"></a>Zpracování a vyvolávání událostí

Události v rozhraní .NET jsou založené na modelu delegáta. Model delegáta dodržuje [vzor návrhu pozorovatele](observer-design-pattern.md), který umožňuje předplatiteli zaregistrovat se a přijímat oznámení od poskytovatele. Odesílatel události vloží oznámení, že k události došlo, a příjemce události obdrží toto oznámení a definuje odpověď na ni. Tento článek popisuje hlavní komponenty modelu delegáta, způsob, jak spotřebovávat události v aplikacích a jak implementovat události v kódu.  
  
 Informace o zpracování událostí v aplikacích Windows 8. x Store najdete v tématu [Přehled událostí a směrovaných událostí](https://docs.microsoft.com/previous-versions/windows/apps/hh758286(v=win.10)).  
  
## <a name="events"></a>Události

Událost je zpráva odeslaná objektem k signalizaci výskytu akce. Tato akce může být způsobena zásahem uživatele, například kliknutím na tlačítko, nebo může být výsledkem některé jiné logiky programu, jako je například změna hodnoty vlastnosti. Objekt, který vyvolává událost, se nazývá *odesílatel události*. Odesílatel události neví, který objekt nebo metoda obdrží (zpracuje) události, které vyvolá. Událost je obvykle členem odesílatele události; například <xref:System.Web.UI.WebControls.Button.Click> událost je členem <xref:System.Web.UI.WebControls.Button> třídy a <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> událost je členem třídy, která implementuje <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní.  
  
Chcete-li definovat událost, použijte [`event`](../../csharp/language-reference/keywords/event.md) klíčové slovo C# nebo Visual Basic [`Event`](../../visual-basic/language-reference/statements/event-statement.md) v signatuře třídy Event a určete typ delegáta pro událost. Delegáti jsou popsáni v následující části.  
  
Pro vyvolání události obvykle přidáte metodu, která je označena jako `protected` a `virtual` (v jazyce C#) nebo `Protected` a `Overridable` (v Visual Basic). Pojmenujte tuto metodu `On` *EventName*; například `OnDataReceived` . Metoda by měla přijmout jeden parametr, který určuje datový objekt události, což je objekt typu <xref:System.EventArgs> nebo odvozený typ. Tuto metodu můžete zadat, chcete-li povolit odvozené třídy pro přepsání logiky pro vyvolání události. Odvozená třída by měla vždy volat `On` metodu *EventName* základní třídy, aby se zajistilo, že registrovaní delegáti obdrží událost.  

Následující příklad ukazuje, jak deklarovat událost s názvem `ThresholdReached` . Událost je přidružena k <xref:System.EventHandler> delegátovi a vyvolána v metodě s názvem `OnThresholdReached` .  
  
 [!code-csharp[EventsOverview#1](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Delegáti

Delegát je typ, který obsahuje odkaz na metodu. Delegát je deklarován s signaturou, která zobrazuje návratový typ a parametry pro metody, na které odkazuje, a může uchovávat odkazy pouze na metody, které odpovídají jejímu podpisu. Delegát je tedy ekvivalentní k ukazateli funkce bezpečnému pro typ nebo zpětnému volání. Deklarace delegáta postačuje k definování třídy delegáta.  
  
Delegáti mají spoustu použití v .NET. V kontextu událostí delegát je zprostředkovatel (nebo mechanismus podobný ukazateli) mezi zdrojem události a kódem, který událost zpracovává. Delegáta můžete přidružit k události zahrnutím typu delegáta v deklaraci události, jak je znázorněno v příkladu v předchozí části. Další informace o delegátech naleznete v tématu <xref:System.Delegate> Třída.  
  
Rozhraní .NET poskytuje <xref:System.EventHandler> <xref:System.EventHandler%601> delegáty a pro podporu většiny scénářů událostí. Použijte <xref:System.EventHandler> delegáta pro všechny události, které neobsahují data události. Použijte <xref:System.EventHandler%601> delegáta pro události, které obsahují data o události. Tito Delegáti nemají žádnou hodnotu návratového typu a přebírají dva parametry (objekt pro zdroj události a objekt pro data události).  
  
Delegáti jsou [vícesměrové vysílání](xref:System.MulticastDelegate), což znamená, že mohou obsahovat odkazy na více než jednu metodu zpracování událostí. Podrobnosti najdete na <xref:System.Delegate> referenční stránce. Delegáti poskytují flexibilitu a jemně odstupňovaný ovládací prvek pro zpracování událostí. Delegát funguje jako dispečer události pro třídu, která vyvolává událost tím, že udržuje seznam registrovaných obslužných rutin událostí pro událost.  
  
U scénářů <xref:System.EventHandler> , kde <xref:System.EventHandler%601> Delegáti a nefungují, můžete definovat delegáta. Scénáře, které vyžadují, abyste definovali delegáta, jsou velmi vzácné, například když musíte pracovat s kódem, který nerozpozná obecné typy. Označíte delegáta pomocí [`delegate`](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) [`Delegate`](../../visual-basic/language-reference/statements/delegate-statement.md) klíčového slova C# a Visual Basic v deklaraci. Následující příklad ukazuje, jak deklarovat delegáta s názvem `ThresholdReachedEventHandler` .  
  
[!code-csharp[EventsOverview#4](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
[!code-vb[EventsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Data událostí

Data přidružená k události lze poskytnout prostřednictvím třídy dat události. Rozhraní .NET poskytuje mnoho datových tříd událostí, které můžete použít ve svých aplikacích. <xref:System.IO.Ports.SerialDataReceivedEventArgs>Třída je například třída dat události pro <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType> událost. Rozhraní .NET se řídí vzorem pojmenování všech tříd dat událostí pomocí `EventArgs` . Určíte, která třída dat události je přidružena k události, a to tak, že se podíváte na delegáta události. Například <xref:System.IO.Ports.SerialDataReceivedEventHandler> delegát obsahuje <xref:System.IO.Ports.SerialDataReceivedEventArgs> třídu jako jeden z jeho parametrů.  
  
<xref:System.EventArgs>Třída je základní typ pro všechny třídy dat událostí. <xref:System.EventArgs>je také třída, kterou použijete v případě, že k události nejsou přidružena žádná data. Když vytvoříte událost, která má pouze upozornit jiné třídy, k nimž došlo, a není nutné předávat žádná data, zahrňte <xref:System.EventArgs> třídu jako druhý parametr delegáta. Hodnotu můžete předat, <xref:System.EventArgs.Empty?displayProperty=nameWithType> Pokud nejsou k dispozici žádná data. <xref:System.EventHandler>Delegát obsahuje <xref:System.EventArgs> třídu jako parametr.  
  
Chcete-li vytvořit přizpůsobenou třídu dat události, vytvořte třídu, která je odvozena z <xref:System.EventArgs> a poté poskytněte jakékoli členy potřebné k předání dat, která se vztahují k události. Obvykle byste měli použít stejný vzor pro pojmenování jako .NET a ukončit název třídy dat události pomocí `EventArgs` .  
  
Následující příklad ukazuje třídu dat události s názvem `ThresholdReachedEventArgs` . Obsahuje vlastnosti, které jsou specifické pro vyvolání události.  
  
[!code-csharp[EventsOverview#3](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
[!code-vb[EventsOverview#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Obslužné rutiny událostí

Chcete-li reagovat na událost, definujte metodu obslužné rutiny události v přijímači událostí. Tato metoda se musí shodovat s signaturou delegáta události, kterou zpracováváte. V obslužné rutině události provedete akce, které jsou požadovány při vyvolání události, jako je například shromažďování uživatelského vstupu, poté, co uživatel klikne na tlačítko. Chcete-li dostávat oznámení, když dojde k události, metoda obslužné rutiny události musí být přihlášena k odběru události.  
  
Následující příklad ukazuje metodu obslužné rutiny události s názvem `c_ThresholdReached` , která odpovídá signatuře <xref:System.EventHandler> delegáta. Metoda se přihlašuje k odběru `ThresholdReached` události.  
  
[!code-csharp[EventsOverview#2](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
[!code-vb[EventsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Statické a dynamické obslužné rutiny událostí  

.NET umožňuje předplatitelům registrovat se pro oznamování událostí staticky nebo dynamicky. Statické obslužné rutiny událostí jsou platné pro celou dobu života třídy, jejíž události zpracovávají. Dynamické obslužné rutiny událostí jsou explicitně aktivovány a dezaktivovány během provádění programu, obvykle v reakci na určitou logickou logiku programu. Můžete je například použít, pokud jsou oznámení o událostech nutná pouze za určitých podmínek nebo pokud aplikace poskytuje více obslužných rutin událostí a běhových podmínek definují příslušné rozhraní, které se má použít. Příklad v předchozím oddílu ukazuje, jak dynamicky přidat obslužnou rutinu události. Další informace naleznete v tématu [události](../../visual-basic/programming-guide/language-features/events/index.md) (v Visual Basic) a [události](../../csharp/programming-guide/events/index.md) (v jazyce C#).  
  
## <a name="raising-multiple-events"></a>Vyvolání více událostí  
 Pokud vaše třída vyvolá více událostí, kompilátor vygeneruje jedno pole pro každou instanci delegáta události. Pokud je počet událostí velký, nemusí být náklady na úložiště jednoho pole na delegáta přijatelné. V těchto situacích poskytuje .NET vlastnosti události, které můžete použít s jinou datovou strukturou dle vašeho výběru k ukládání delegátů událostí.  
  
 Vlastnosti události se skládají z deklarací událostí spolu s přístupovými objekty událostí. Přístupové objekty událostí jsou metody, které definujete pro přidání nebo odebrání instancí delegátů událostí z datové struktury úložiště. Všimněte si, že vlastnosti události jsou pomalejší než pole události, protože každý delegát události musí být načten předtím, než může být vyvolán. Kompromis mezi pamětí a rychlostí. Pokud vaše třída definuje mnoho událostí, které jsou zřídka vyvolány, budete chtít implementovat vlastnosti události. Další informace najdete v tématu [Postupy: zpracování více událostí pomocí vlastností události](how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Postupy: Vyvolávání a zpracovávání událostí](how-to-raise-and-consume-events.md)|Obsahuje příklady vyvolání a využívání událostí.|  
|[Postupy: Zpracování více událostí pomocí vlastností událostí](how-to-handle-multiple-events-using-event-properties.md)|Ukazuje, jak používat vlastnosti událostí pro zpracování více událostí.|  
|[Vzor návrhu pozorovatele](observer-design-pattern.md)|Popisuje vzor návrhu, který umožňuje předplatiteli zaregistrovat se a přijímat oznámení od poskytovatele.|  
|[Postupy: Příjem událostí v aplikaci Web Forms](how-to-consume-events-in-a-web-forms-application.md)|Ukazuje, jak zpracovat událost, která je vyvolána ovládacím prvkem webového formuláře.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.EventHandler>
- <xref:System.EventHandler%601>
- <xref:System.EventArgs>
- <xref:System.Delegate>
- [Události (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)
- [Události (Průvodce programováním v C#)](../../csharp/programming-guide/events/index.md)
- [Přehled událostí a směrovaných událostí (aplikace pro UWP)](/windows/uwp/xaml-platform/events-and-routed-events-overview)
