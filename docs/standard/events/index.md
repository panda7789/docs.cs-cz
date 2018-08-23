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
ms.openlocfilehash: 623700161ae4587daeb2c7348055d413512f7c87
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752131"
---
# <a name="handling-and-raising-events"></a>Zpracování a generování událostí
Události v rozhraní .NET Framework jsou založené na modelu delegáta. Model delegáta následuje návrhový vzor pozorovatele, který umožňuje předplatiteli zaregistrovat se a dostávat upozornění od poskytovatele. Odesílatel události posune oznámení, že k události došlo, a příjemce události obdrží toto oznámení a definuje odpověď na ně. Tento článek popisuje hlavní součásti modelu delegáta, zacházení s událostmi v aplikacích a implementaci událostí ve vašem kódu.  
  
 Informace o zpracování událostí v aplikacích pro Windows 8.x Store najdete v tématu [událostí a směrovaných událostí přehled](https://docs.microsoft.com/previous-versions/windows/apps/hh758286(v=win.10)).  
  
## <a name="events"></a>Události  
 Událost je zpráva odeslaná objektem pro signalizaci výskytu akce. Akce může být způsobeno interakci s uživatelem, například kliknutí na tlačítko, nebo může být vyvolána nějakou jinou programovou logikou, jako je například změna hodnoty vlastnosti. Objekt, který vyvolá událost, se nazývá *odesílatele události*. Odesílatel událostí neví, který objekt nebo metoda obdrží (zpracuje) události, které vyvolá. Událost je obvykle člen odesílatele události; například <xref:System.Web.UI.WebControls.Button.Click> událostí je členem skupiny <xref:System.Web.UI.WebControls.Button> třídy a <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> událostí je členem třídy, která implementuje <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní.  
  
 Chcete-li definovat událost, použijte `event` (v jazyce C#) nebo `Event` (v jazyce Visual Basic) – klíčové slovo v podpisu událost třídy, a zadejte typ delegáta pro událost. Delegáti jsou popsáni v následující části.  
  
 Obvykle, chcete-li vyvolat událost, přidáte metodu, která je označena jako `protected` a `virtual` (v jazyce C#) nebo `Protected` a `Overridable` (v jazyce Visual Basic). Pojmenujte tuto metodu `On` *EventName*; například `OnDataReceived`. Metoda by měla přijímat jeden parametr, který určuje objekt dat události. Můžete zadat tato metoda umožňuje odvozeným třídám přepsat logiku pro vyvolání události. Odvozená třída musí vždy volat `On` *EventName* metody základní třídy, která se ujistěte, že registrovaní delegáti obdrží událost.  
  
 Následující příklad ukazuje, jak deklarovat událost s názvem `ThresholdReached`. Událost je přidružena s <xref:System.EventHandler> delegáta a vyvolána metoda s názvem `OnThresholdReached`.  
  
 [!code-csharp[EventsOverview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#1)]
 [!code-vb[EventsOverview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#1)]  
  
## <a name="delegates"></a>Delegáty  
 Delegát je typ, který obsahuje odkaz na metodu. Delegát je deklarován s podpisem, který zobrazuje návratový typ a parametry pro metody odkazuje a mohou obsahovat odkazy pouze na metody, které odpovídají jeho signatuře. Delegát je tedy ekvivalentní k ukazatele na funkci zajišťující bezpečnost typů nebo zpětného volání. Deklarace delegáta postačuje k definování třídy delegáta.  
  
 Delegáty mají celou řadu uplatnění v rozhraní .NET Framework. V kontextu událostí je delegát prostředník (nebo mechanismus podobný ukazateli) mezi zdrojem události a kód, který zpracovává událost. Přidružíte delegáta k události včetně typu delegáta v deklaraci události, jak je znázorněno v příkladu v předchozí části. Další informace o delegátech naleznete v tématu <xref:System.Delegate> třídy.  
  
 Rozhraní .NET Framework poskytuje <xref:System.EventHandler> a <xref:System.EventHandler%601> delegáty pro podporu většiny scénářů událostí. Použití <xref:System.EventHandler> delegování pro všechny události, které neobsahují data události. Použití <xref:System.EventHandler%601> delegáta události, které zahrnují data o události. Tyto delegáty nemají žádnou hodnotu návratového typu a přijímají dva parametry (objekt pro zdroj události) a objekt pro data události.  
  
 Delegáti jsou vícesměroví, což znamená, že mohou obsahovat odkazy na více než jednu metodu zpracování událostí. Podrobnosti najdete v tématu <xref:System.Delegate> referenční stránce. Delegáti poskytují pružnost a jemnou kontrolu ve zpracování událostí. Delegát funguje jako dispečer události pro třídu, která se vyvolá událost udržováním seznamu registrovaných obslužných rutin události pro událost.  
  
 Pro scénáře, ve kterém <xref:System.EventHandler> a <xref:System.EventHandler%601> delegáti nefungují, můžete definovat delegáta. Scénáře, které od vás vyžadují definování delegáta jsou velmi vzácné, jako je například, když musíte pracovat s kódem, který nerozpoznává obecné typy. Označíte delegáta klíčovým `delegate` v (C#) a `Delegate` (v jazyce Visual Basic) – klíčové slovo v deklaraci. Následující příklad ukazuje, jak deklarovat delegáta s názvem `ThresholdReachedEventHandler`.  
  
 [!code-csharp[EventsOverview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#4)]
 [!code-vb[EventsOverview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#4)]  
  
## <a name="event-data"></a>Data události  
 Data, která je přidružena k události mohou být poskytnuta prostřednictvím třídy dat události. Rozhraní .NET Framework poskytuje mnoho datových tříd událostí, které můžete použít ve svých aplikacích. Například <xref:System.IO.Ports.SerialDataReceivedEventArgs> třídy je třída dat události pro <xref:System.IO.Ports.SerialPort.DataReceived?displayProperty=nameWithType> událostí. Rozhraní .NET Framework následuje vzor pojmenování spočívající v ukončení všechny datových tříd událostí `EventArgs`. Můžete určit, která třída dat události je přidružena událost pohledem na delegáta pro událost. Například <xref:System.IO.Ports.SerialDataReceivedEventHandler> zahrnuje delegáta <xref:System.IO.Ports.SerialDataReceivedEventArgs> třídy jako jeden ze svých parametrů.  
  
 <xref:System.EventArgs> Třída je základní typ pro všechny datové třídy událostí. <xref:System.EventArgs> je také třída, kterou použijete při události nemá všechna data související s ním. Při vytváření událost, která je určená jenom upozornit ostatní třídy, které se něco stalo a není třeba předávat žádná data, patří <xref:System.EventArgs> třídu jako druhý parametr do delegáta. Můžete předat <xref:System.EventArgs.Empty?displayProperty=nameWithType> hodnotu, pokud nejsou k dispozici žádná data. <xref:System.EventHandler> Zahrnuje delegáta <xref:System.EventArgs> jako parametr předávat třídu.  
  
 Pokud chcete vytvořit vlastní třídu dat události, vytvořit třídu, která je odvozena z <xref:System.EventArgs>a potom zadejte všechny členy potřebné pro předání dat, která má vztah k události. Obvykle by měl používat stejný vzor pro pojmenování jako rozhraní .NET Framework a ukončit váš název datové třídy události s `EventArgs`.  
  
 Následující příklad ukazuje třídu dat události s názvem `ThresholdReachedEventArgs`. Obsahuje vlastnosti, které jsou specifické pro vyvolanou událost.  
  
 [!code-csharp[EventsOverview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#3)]
 [!code-vb[EventsOverview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#3)]  
  
## <a name="event-handlers"></a>Obslužné rutiny událostí  
 Reakce na události, definujete metodu obslužné rutiny události v příjemci události. Tato metoda musí odpovídat signatuře delegáta události, kterou obsluhujete. V případě obslužné rutině provedete akce, které jsou potřebné k vyvolání události, jako je například shromažďování vstupu uživatele, jakmile uživatel klikne na tlačítko. Pokud chcete dostávat oznámení při výskytu události, musí vaše metoda obslužné rutiny událostí k události registrovat.  
  
 Následující příklad ukazuje metodu obslužné rutiny události s názvem `c_ThresholdReached` , která odpovídá podpisu pro <xref:System.EventHandler> delegovat. Metoda se hlásí k `ThresholdReached` událostí.  
  
 [!code-csharp[EventsOverview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programtruncated.cs#2)]
 [!code-vb[EventsOverview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1truncated.vb#2)]  
  
## <a name="static-and-dynamic-event-handlers"></a>Statické a dynamické obslužné rutiny událostí  
 Rozhraní .NET umožňuje odběratelům registraci k oznamování události staticky nebo dynamicky. Statické obslužné rutiny jsou platné po celou dobu životnosti třídy, jejíž události zpracovávají. Dynamické obslužné rutiny událostí jsou explicitně aktivovat a deaktivovat během provádění programu, obvykle v reakci na podmíněnou logiku programu. Například můžete používají Pokud jsou oznámení událostí potřebná pouze za určitých podmínek nebo pokud aplikace poskytuje více obslužných rutin událostí a podmínky za běhu určí vhodnou rutinu, chcete-li použít. Příklad v předchozím oddílu ukazuje, jak dynamicky přidat obslužnou rutinu události. Další informace najdete v tématu [události](../../visual-basic/programming-guide/language-features/events/index.md) a [události](../../csharp/programming-guide/events/index.md).  
  
## <a name="raising-multiple-events"></a>Vyvolání více událostí  
 Pokud vaše třída vyvolá více událostí, kompilátor vygeneruje jedno pole pro každou instanci delegáta události. Pokud je počet událostí velký, nemusí být přijatelné náklady na uložení jednoho pole pro každého delegáta. Pro tyto situace rozhraní .NET Framework poskytuje vlastnosti událostí, můžete použít s jinou datovou strukturou vašeho výběru k ukládání delegátů událostí.  
  
 Vlastnosti událostí se skládají z deklarace události společně s přístupovými objekty události. Přístupové objekty událostí jsou metody, které definujete přidat nebo odebrat instance delegátů událostí z datové struktury úložiště. Všimněte si, že vlastnosti událostí jsou pomalejší než pole události, protože každý delegát události musí být načten dříve, než může být vyvolána. Nutný kompromis je mezi pamětí a rychlostí. Pokud vaše třída definuje mnoho událostí, které jsou vyvolávány, můžete implementovat vlastnosti událostí. Další informace najdete v tématu [postupy: zpracování více událostí pomocí vlastností události](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Vyvolávání a zpracovávání událostí](../../../docs/standard/events/how-to-raise-and-consume-events.md)|Obsahuje příklady vyvolávajících a spotřebovávajících událostí.|  
|[Postupy: Zpracování více událostí pomocí vlastností událostí](../../../docs/standard/events/how-to-handle-multiple-events-using-event-properties.md)|Ukazuje, jak použít vlastnosti událostí pro zpracování více událostí.|  
|[Návrhový vzor Pozorovatel](../../../docs/standard/events/observer-design-pattern.md)|Popisuje vzor návrhu, který umožňuje předplatiteli zaregistrovat se a dostávat upozornění od poskytovatele.|  
|[Postupy: Zpracování událostí v aplikaci Web Forms](../../../docs/standard/events/how-to-consume-events-in-a-web-forms-application.md)|Ukazuje, jak zpracovat událost vyvolanou ovládacím prvkem webových formulářů.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.EventHandler>  
 <xref:System.EventHandler%601>  
 <xref:System.EventArgs>  
 <xref:System.Delegate>  
 [Přehled směrovaných událostí (aplikace pro UPW) a události](/windows/uwp/xaml-platform/events-and-routed-events-overview)  
 [Události (Visual Basic)](../../visual-basic/programming-guide/language-features/events/index.md)  
 [Události (C# Programming Guide)](../../csharp/programming-guide/events/index.md)
