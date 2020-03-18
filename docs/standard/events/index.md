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
ms.openlocfilehash: b8ed028bc1edabf14d7b2dd67d94b28d574d2eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159621"
---
# <a name="handling-and-raising-events"></a>Zpracování a vyvolání událostí

Události v rozhraní .NET jsou založeny na modelu delegáta. Model delegáta následuje [vzor návrhu pozorovatele](observer-design-pattern.md), který umožňuje odběrateli zaregistrovat a přijímat oznámení od zprostředkovatele. Odesílatel události odešle oznámení, že došlo k události a příjemce události obdrží toto oznámení a definuje odpověď na něj. Tento článek popisuje hlavní součásti modelu delegáta, jak využívat události v aplikacích a jak implementovat události v kódu.  
  
 Informace o zpracování událostí v aplikacích pro Windows 8.x Store najdete v [tématu Přehled událostí a směrovaných událostí](https://docs.microsoft.com/previous-versions/windows/apps/hh758286(v=win.10)).  
  
## <a name="events"></a>Akce

Událost je zpráva odeslaná objektem, která signalizuje výskyt akce. Akce může být způsobena interakcí uživatele, například kliknutím na tlačítko, nebo může být výsledkem jiné programové logiky, jako je například změna hodnoty vlastnosti. Objekt, který vyvolá událost se nazývá *odesílatel události*. Odesílatel události neví, který objekt nebo metoda obdrží (zpracovává) události, které vyvolá. Událost je obvykle členem odesílatele události; <xref:System.Web.UI.WebControls.Button.Click> například událost je členem <xref:System.Web.UI.WebControls.Button> třídy a <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> událost je členem třídy, která implementuje <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní.  
  
Chcete-li definovat událost, použijte [`event`](../../csharp/language-reference/keywords/event.md) c# [`Event`](../../visual-basic/language-reference/statements/event-statement.md) nebo visual basic klíčové slovo v podpisu třídy události a zadejte typ delegáta pro událost. Delegáti jsou popsány v další části.  
  
Obvykle chcete-li vyvolat událost, přidáte metodu, `protected` `virtual` která je označena `Protected` `Overridable` jako a (v jazyce C#) nebo (v jazyce Visual Basic). Pojmenujte `On`tuto metodu *EventName*; například `OnDataReceived`. Metoda by měla trvat jeden parametr, který určuje datový <xref:System.EventArgs> objekt události, který je objektem typu nebo odvozeného typu. Zadáte tuto metodu povolit odvozené třídy přepsat logiku pro vyvolání události. Odvozená třída by měla `On`vždy volat metodu *EventName* základní třídy, aby bylo zajištěno, že registrovaní delegáti obdrží událost.  

Následující příklad ukazuje, jak deklarovat událost s názvem `ThresholdReached`. Událost je přidružena <xref:System.EventHandler> k delegátovi a `OnThresholdReached`vyvolána metodou s názvem .  
  
 [!code-csharp[EventsOverview#1](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Delegáty

Delegát je typ, který obsahuje odkaz na metodu. Delegát je deklarován s podpisem, který zobrazuje návratový typ a parametry pro metody, na které odkazuje, a může obsahovat odkazy pouze na metody, které odpovídají jeho podpisu. Delegát je tedy ekvivalentní ukazatele funkce bezpečného typu nebo zpětné volání. Deklarace delegáta je dostatečná k definování třídy delegáta.  
  
Delegáti mají mnoho použití v rozhraní .NET. V kontextu událostí delegát je prostředníkem (nebo mechanismus podobný ukazateli) mezi zdrojem události a kódem, který zpracovává událost. Delegáta přidružíte k události zahrnutím typu delegáta do deklarace události, jak je znázorněno v příkladu v předchozí části. Další informace o delegátech <xref:System.Delegate> naleznete ve třídě.  
  
Rozhraní .NET <xref:System.EventHandler> <xref:System.EventHandler%601> poskytuje a delegáty pro podporu většiny scénářů událostí. Delegáta <xref:System.EventHandler> použijte pro všechny události, které neobsahují data událostí. Delegáta <xref:System.EventHandler%601> použijte pro události, které obsahují data o události. Tito delegáti nemají žádnou hodnotu návratového typu a berou dva parametry (objekt pro zdroj události a objekt pro data události).  
  
Delegáti jsou [vícesměrové vysílání](xref:System.MulticastDelegate), což znamená, že mohou obsahovat odkazy na více než jednu metodu zpracování událostí. Podrobnosti naleznete <xref:System.Delegate> na referenční stránce. Delegáti poskytují flexibilitu a jemně odstupňované řízení při zpracování událostí. Delegát funguje jako dispečer události pro třídu, která vyvolává událost udržováním seznamu registrovaných obslužných rutin událostí pro událost.  
  
Pro scénáře, <xref:System.EventHandler> <xref:System.EventHandler%601> kde a delegáti nefungují, můžete definovat delegáta. Scénáře, které vyžadují definovat delegáta jsou velmi vzácné, například když je nutné pracovat s kódem, který nerozpozná obecné typy. Delegáta označíte [`delegate`](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) klíčovým slovem Jazyka C# a Visual Basic [`Delegate`](../../visual-basic/language-reference/statements/delegate-statement.md) v deklaraci. Následující příklad ukazuje, jak deklarovat delegáta s názvem `ThresholdReachedEventHandler`.  
  
[!code-csharp[EventsOverview#4](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
[!code-vb[EventsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Data událostí

Data, která je přidružena k události lze poskytnout prostřednictvím třídy dat události. Rozhraní .NET poskytuje mnoho tříd dat událostí, které můžete použít ve svých aplikacích. Například <xref:System.IO.Ports.SerialDataReceivedEventArgs> třída je třída dat události <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType> pro událost. Rozhraní .NET sleduje vzor pojmenování ukončení `EventArgs`všech tříd dat událostí pomocí aplikace . Můžete určit, která třída dat události je přidružena k události pohledem na delegáta pro událost. Delegát například <xref:System.IO.Ports.SerialDataReceivedEventHandler> zahrnuje <xref:System.IO.Ports.SerialDataReceivedEventArgs> třídu jako jeden z jeho parametrů.  
  
Třída <xref:System.EventArgs> je základním typem pro všechny třídy dat událostí. <xref:System.EventArgs>je také třída, kterou používáte, když k události nejsou přidružena žádná data. Když vytvoříte událost, která je určena pouze k upozornění jiných tříd, že <xref:System.EventArgs> se něco stalo a nemusí předat žádná data, zahrňte třídu jako druhý parametr v delegátovi. Hodnotu můžete <xref:System.EventArgs.Empty?displayProperty=nameWithType> předat, pokud nejsou k dispozici žádná data. Delegát <xref:System.EventHandler> zahrnuje <xref:System.EventArgs> třídu jako parametr.  
  
Pokud chcete vytvořit vlastní třídu dat události, vytvořte <xref:System.EventArgs>třídu, která je odvozena z aplikace , a poté zadejte všechny členy potřebné k předání dat, která souvisí s událostí. Obvykle byste měli použít stejný vzor pojmenování jako rozhraní .NET `EventArgs`a ukončit název třídy dat události pomocí .  
  
Následující příklad ukazuje třídu `ThresholdReachedEventArgs`dat události s názvem . Obsahuje vlastnosti, které jsou specifické pro událost, která je vyvolána.  
  
[!code-csharp[EventsOverview#3](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
[!code-vb[EventsOverview#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Obslužné rutiny událostí

Chcete-li reagovat na událost, definujete metodu obslužné rutiny události v příjemci události. Tato metoda musí odpovídat podpisdelegáta pro událost, kterou zpracováváte. V obslužné rutině události provedete akce, které jsou požadovány při vyvolání události, jako je například shromažďování vstupu uživatele po kliknutí uživatele na tlačítko. Chcete-li přijímat oznámení, když dojde k události, musí se k odběru události přihlásit metoda obslužné rutiny události.  
  
Následující příklad ukazuje metodu `c_ThresholdReached` obslužné <xref:System.EventHandler> rutiny události s názvem, která odpovídá podpisu delegáta. Metoda se přihlásí `ThresholdReached` k odběru události.  
  
[!code-csharp[EventsOverview#2](~/samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
[!code-vb[EventsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Statické a dynamické obslužné rutiny událostí  

Rozhraní .NET umožňuje odběratelům zaregistrovat oznámení událostí staticky nebo dynamicky. Obslužné rutiny statických událostí jsou platné po celou dobu životnosti třídy, jejíž události zpracovávají. Obslužné rutiny dynamických událostí jsou explicitně aktivovány a deaktivovány během provádění programu, obvykle v reakci na některé logiky podmíněného programu. Například mohou být použity, pokud oznámení událostí jsou potřeba pouze za určitých podmínek nebo pokud aplikace poskytuje více obslužné rutiny událostí a podmínky běhu definovat odpovídající jeden použít. Příklad v předchozí části ukazuje, jak dynamicky přidat obslužnou rutinu události. Další informace naleznete v [tématu Události](../../visual-basic/programming-guide/language-features/events/index.md) (v jazyce Visual Basic) a [Události](../../csharp/programming-guide/events/index.md) (v jazyce C#).  
  
## <a name="raising-multiple-events"></a>Vyvolání více událostí  
 Pokud vaše třída vyvolá více událostí, kompilátor generuje jedno pole na instanci delegáta události. Pokud je počet událostí velký, nemusí být přijatelné náklady na úložiště jednoho pole na delegáta. Pro tyto situace .NET poskytuje vlastnosti událostí, které můžete použít s jinou datovou strukturou podle vašeho výběru k uložení delegátů událostí.  
  
 Vlastnosti události se skládají z deklarací událostí doprovázených přistupujícími objekty události. Přistupující objekty událostí jsou metody, které definujete pro přidání nebo odebrání instancí delegáta událostí ze struktury dat úložiště. Všimněte si, že vlastnosti události jsou pomalejší než pole událostí, protože každý delegát události musí být načten před tím, než může být vyvolán. Kompromis je mezi pamětí a rychlostí. Pokud vaše třída definuje mnoho událostí, které jsou zřídka vyvolány, budete chtít implementovat vlastnosti události. Další informace naleznete v [tématu How to: Handle multiple Events using Events Properties](how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Postupy: Vyvolávání a zpracovávání událostí](how-to-raise-and-consume-events.md)|Obsahuje příklady zvyšování a náročné události.|  
|[Postupy: Zpracování více událostí pomocí vlastností událostí](how-to-handle-multiple-events-using-event-properties.md)|Ukazuje, jak používat vlastnosti události ke zpracování více událostí.|  
|[Návrhový vzor Pozorovatel](observer-design-pattern.md)|Popisuje návrhový vzor, který umožňuje odběrateli zaregistrovat a přijímat oznámení od zprostředkovatele.|  
|[Postupy: Příjem událostí v aplikaci Web Forms](how-to-consume-events-in-a-web-forms-application.md)|Ukazuje, jak zpracovat událost, která je vyvolána ovládacím prvkem webových formulářů.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.EventHandler>
- <xref:System.EventHandler%601>
- <xref:System.EventArgs>
- <xref:System.Delegate>
- [Události (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)
- [Události (Průvodce programováním v C#)](../../csharp/programming-guide/events/index.md)
- [Přehled událostí a směrovaných událostí (aplikace UPW)](/windows/uwp/xaml-platform/events-and-routed-events-overview)
