---
title: Principy změn stavů
ms.date: 03/30/2017
ms.assetid: a79ed2aa-e49a-47a8-845a-c9f436ec9987
ms.openlocfilehash: 858da2a88c17920910c05966bb3b211d754fb278
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424768"
---
# <a name="understanding-state-changes"></a>Principy změn stavů
Toto téma popisuje stavy a přechody, které mají kanály, typy používané struktura kanálu stavům a způsobu jejich implementace.  
  
## <a name="state-machines-and-channels"></a>Stav počítače a kanály  
 Objekty, které pracují s komunikací, například soketů, obvykle k dispozici stavový počítač, jehož přechodů mezi stavy týkají přidělování prostředků sítě, přičemž nebo přijímá připojení, zavření připojení a komunikace se ukončuje. Stavový počítač kanál poskytuje jednotné model stavů objekt komunikace, který abstrahuje základní implementaci tohoto objektu. <xref:System.ServiceModel.ICommunicationObject> Rozhraní poskytuje sadu státy, metody přechod stavu a událostí změny stavu. Všechny kanály, objekty pro vytváření kanálů a moduly pro naslouchání kanálů můžete implementovat počítač stav kanálu.  
  
 Události uzavřeno, zavřete, Faulted, otevřeno a otevírání signál pozorovatel externí po přechod stavu.  
  
 Metody Abort, zavřít a otevřete (a jejich ekvivalenty asynchronní) způsobit, že přechodů mezi stavy.  
  
 Vlastnost state vrátí aktuální stav souladu s definicemi <xref:System.ServiceModel.CommunicationState>:  
  
## <a name="icommunicationobject-communicationobject-and-states-and-state-transition"></a>Objekt ICommunicationObject, v objektu CommunicationObject a stavy a přechod stavu  
 <xref:System.ServiceModel.ICommunicationObject> Spustí ve stavu vytvořen, kde lze nastavit jeho různé vlastnosti. Jednou ve stavu otevřen objekt je použitelná pro odesílání a příjem zpráv, ale její vlastnosti jsou považován za neměnitelný. Jakmile se ve stavu zavírání objektu můžete už zpracovat nové odeslání nebo přijímat požadavky, ale existujících žádostí mít příležitost dobře se až do dokončení je dosaženo zavřít časového limitu.  Pokud došlo k neopravitelné chybě, objekt přechází do chybovém stavu, ve kterém může být zkontrolovány informace o této chybě a nakonec uzavřen. Když v uzavřeném stavu objektu v podstatě dosáhla koncový stav stavového stroje. Jednou objektu přechodů z jednoho stavu do dalšího neprochází zpět do předchozího stavu.  
  
 Následující obrázek ukazuje, <xref:System.ServiceModel.ICommunicationObject> stavy a přechody stavu. Přechodů mezi stavy, může být způsobeno volání jedné ze tří metod: Přerušit, otevřít nebo zavřít. Může být také způsobeno voláním metod specifický pro implementaci. Přechod do stavu chyba může nastat v důsledku chyb při otevírání nebo po nutnosti otevřít objekt komunikace.  
  
 Každý <xref:System.ServiceModel.ICommunicationObject> spustí ve stavu vytvořen. V tomto stavu můžete aplikaci nakonfigurovat objektu nastavením jeho vlastností. Jakmile je objekt v jiném stavu než vytvořeno, je považován za neměnitelný.  
  
 ![Přechod stavu kanálu](../../../../docs/framework/wcf/extending/media/channelstatetranitionshighleveldiagram.gif "ChannelStateTranitionsHighLevelDiagram")  
Obrázek 1. Objekt ICommunicationObject stavového stroje.  
  
 Windows Communication Foundation (WCF) poskytuje abstraktní základní třídu s názvem <xref:System.ServiceModel.Channels.CommunicationObject> , který implementuje <xref:System.ServiceModel.ICommunicationObject> a stav stavového stroje kanálu. Na následujícím obrázku je upravený stav diagram, který je specifický pro <xref:System.ServiceModel.Channels.CommunicationObject>. Kromě <xref:System.ServiceModel.ICommunicationObject> stavový počítač zobrazuje den, kdy další <xref:System.ServiceModel.Channels.CommunicationObject> jsou metody vyvolány.  
  
 ![Stav změny](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure5statetransitionsdetailsc.gif "wcfc_WCFChannelsigure5StateTransitionsDetailsc")  
Obrázek 2. V objektu CommunicationObject implementace stavového stroje objekt ICommunicationObject včetně volání na události a chráněné metody.  
  
### <a name="icommunicationobject-events"></a>Objekt ICommunicationObject události  
 <xref:System.ServiceModel.Channels.CommunicationObject> poskytuje pět události definované <xref:System.ServiceModel.ICommunicationObject>. Tyto události jsou navržené pro kód pomocí objektu komunikace upozornit přechodů mezi stavy. Jak je znázorněno na obrázku 2 výše, každý po aktivuje událost jednou stav objektu přechází do stavu s názvem události. Všechny události pět jsou `EventHandler` typ, který je definován jako:  
  
 `public delegate void EventHandler(object sender, EventArgs e);`  
  
 V <xref:System.ServiceModel.Channels.CommunicationObject> implementace, odesílatel je buď <xref:System.ServiceModel.Channels.CommunicationObject> samotné nebo cokoli, co byla předána jako odesílatele, aby <xref:System.ServiceModel.Channels.CommunicationObject> konstruktoru (Pokud byl použit tento přetížení konstruktoru). Parametr EventArgs `e`, je vždy `EventArgs.Empty`.  
  
### <a name="derived-object-callbacks"></a>Zpětná volání objektu  
 Kromě pěti události <xref:System.ServiceModel.Channels.CommunicationObject> deklaruje osm chráněné virtuální metody, které jsou navržené tak, objekt odvozené zpětné volání, před a po přechodu stavu.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> metody mají tři takové spojené s každou z nich zpětná volání. Například odpovídající <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> je <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, a <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>. Přidružené <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> jsou <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType>, a <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> metody.  
  
 Podobně platí <xref:System.ServiceModel.Channels.CommunicationObject.Abort%2A?displayProperty=nameWithType> metoda má odpovídající <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType>.  
  
 Zatímco <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, a <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType> nemají výchozí implementaci, další zpětná volání nemají výchozí implementace, která je nezbytná pro správnosti stavu počítače. Pokud je přepsat tyto metody nezapomeňte volat základní implementaci nebo správně nahradit.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.CommunicationObject.OnFaulted%2A?displayProperty=nameWithType> vyvolat odpovídající <xref:System.ServiceModel.Channels.CommunicationObject.Opening?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.Closing?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.CommunicationObject.Faulted?displayProperty=nameWithType> události. <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> nastavte stav objektu otevřen a uzavřené v uvedeném pořadí potom aktivuje odpovídající <xref:System.ServiceModel.Channels.CommunicationObject.Opened?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.CommunicationObject.Closed?displayProperty=nameWithType> události.  
  
### <a name="state-transition-methods"></a>Metody přechod stavu  
 <xref:System.ServiceModel.Channels.CommunicationObject> poskytuje implementace Abort, zavřete a otevřete. Také poskytuje metodu selhání, což způsobí, že stav přechod do stavu chyba. Obrázek 2 ukazuje <xref:System.ServiceModel.ICommunicationObject> stavového stroje s každý přechod označené metodu, která způsobí, že (bez popisku přechody stane uvnitř implementace metody, která způsobila poslední označených přechod).  
  
> [!NOTE]
>  Všechny <xref:System.ServiceModel.Channels.CommunicationObject> implementace komunikace stavu, získá nebo nastaví jsou synchronizovány vlákna.  
  
 Konstruktor  
  
 <xref:System.ServiceModel.Channels.CommunicationObject> poskytuje tři konstruktory, které ponechte objekt ve stavu vytvořen. Konstruktory jsou definovány jako:  
  
 První konstruktor je výchozí konstruktor, který se delegoval přetížení konstruktoru, který přebírá objekt:  
  
 `protected CommunicationObject() : this(new object()) { … }`  
  
 Konstruktor, který přijímá objekt tento parametr používá jako objekt uzamčení při synchronizaci přístup ke stavu objektu komunikace:  
  
 `protected CommunicationObject(object mutex) { … }`  
  
 A konečně, třetí konstruktor přijímá další parametr, který se používá jako argument odesílatele při <xref:System.ServiceModel.ICommunicationObject> jsou vyvolávány události.  
  
 `protected CommunicationObject(object mutex, object eventSender) { … }`  
  
 Předchozí dva konstruktory nastavte odesílatel na to.  
  
 Open – metoda  
  
 Předběžné podmínky: Stav se vytvoří.  
  
 Podmínka po: Stav je otevřen nebo Faulted. Může vyvolat výjimku.  
  
 Metoda Open() se pokusí otevřít objekt komunikace a nastavit stav na otevřen. Pokud dojde k chybě, nastaví na chybovém stavu.  
  
 Metoda nejprve zkontroluje, že se vytvořil aktuální stav. Pokud je aktuální stav otevírání nebo otevření vyvolá <xref:System.InvalidOperationException>. Pokud jeho aktuální stav je uzavírací nebo Uzavřeno, vyvolá výjimku <xref:System.ServiceModel.CommunicationObjectAbortedException> Pokud byl ukončen objekt a <xref:System.ObjectDisposedException> jinak. Pokud došlo k chybě v aktuální stav, vyvolá výjimku <xref:System.ServiceModel.CommunicationObjectFaultedException>.  
  
 Potom nastaví stav otevírací a volá OnOpening() (která vyvolává událost otevření), OnOpen() a OnOpened() v uvedeném pořadí. OnOpened() nastaví stav otevřen a vyvolává událost otevřen. Pokud některý z těchto vyvolá výjimku (Otevřít) volá Fault() a umožní bublinu výjimka. Následující diagram znázorňuje otevřeného procesu podrobněji.  
  
 ![Stav změny](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigurecoopenflowchartf.gif "wcfc_WCFChannelsigureCOOpenFlowChartf")  
Přepište metodu při otevření a implementovat vlastní otevřít logiku, jako je otevření objektu vnitřní komunikace.  
  
 Close – metoda  
  
 Předběžné podmínky: Žádné  
  
 Podmínka po: Stav je zavřený. Může vyvolat výjimku.  
  
 Metoda Close() lze volat vždycky. Pokusí se obvykle zavření objektu. Pokud dojde k chybě, ukončí na objekt. Metoda provede, když se zavírá aktuální stav nebo Uzavřeno. Jinak nastaví stav zavření. Pokud se původní stav byl vytvořen, otevření nebo Faulted, zavolá Abort() (viz následující diagram). Pokud byl otevřen původního stavu, volá OnClosing() (která vyvolává událost pravou), OnClose() a OnClosed() v uvedeném pořadí. Pokud některý z těchto vyvolá výjimku (Zavřít) volá Abort() a umožňuje bublinu výjimka. OnClosed() nastaví stavu na Uzavřeno a vyvolá zavřeném ovladači události. Následující diagram znázorňuje uzavření zpracovat podrobněji.  
  
 ![Stav změny](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsguire7ico-closeflowchartc.gif "wcfc_WCFChannelsguire7ICO CloseFlowChartc")  
Potlačí metodu při zavření k implementaci vlastní logiky zavřít, například zavření objektu vnitřní komunikace. Všechny řádné zavření logiku, která může blokovat pro dlouhou dobu (například čekání na druhé straně reagovat) by měla být implementována v OnClose(), protože má parametr časového limitu, a proto není volána jako součást Abort().  
  
 Přerušení  
  
 Předběžné podmínky: Žádné  
Podmínka po: Stav je zavřený. Může vyvolat výjimku.  
  
 Metoda Abort() nemá žádný účinek, pokud jeho aktuální stav je uzavřený nebo pokud objekt byl ukončen před (například může být tím, že Abort() provádění na jiné vlákno). Jinak nastaví stav uzavírací a volá OnClosing() (která vyvolává událost pravou), OnAbort() a OnClosed() v tomto pořadí (nevolá onclose – vzhledem k tomu, že objekt se ukončuje, není ukončen). OnClosed() nastaví stavu na Uzavřeno a vyvolá zavřeném ovladači události. Pokud některý z těchto vyvolat výjimku, je znovu vyvolána volajícímu přerušení. Implementace OnClosing(), OnClosed() a OnAbort() by neměla blokovat (třeba na vstup/výstup). Následující diagram znázorňuje proces zrušení podrobněji.  
  
 ![Stav změny](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure8ico-abortflowchartc.gif "wcfc_WCFChannelsigure8ICO AbortFlowChartc")  
Přepsání metody OnAbort implementovat vlastní ukončit logiku, jako je objekt vnitřní komunikace se ukončuje.  
  
 Selhání  
  
 Metoda selhání je specifické pro <xref:System.ServiceModel.Channels.CommunicationObject> a nejsou součástí <xref:System.ServiceModel.ICommunicationObject> rozhraní. Je tu zahrnuté pro úplnost.  
  
 Předběžné podmínky: Žádné  
  
 Podmínka po: Stav je došlo k chybě. Může vyvolat výjimku.  
  
 Metoda Fault() nemá žádný účinek, pokud jeho aktuální stav je chybný nebo Uzavřeno. Jinak nastaví stav Faulted a volání OnFaulted(), která vyvolává událost Faulted. Pokud dojde k výjimce OnFaulted je znovu vyvolána.  
  
### <a name="throwifxxx-methods"></a>ThrowIfXxx metody  
 V objektu CommunicationObject má tři chráněné metody, které lze použít k vyvolání výjimky, pokud je objekt v určitém stavu.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposed%2A> vyvolá výjimku, pokud stav není uzavírací, Uzavřeno nebo Faulted.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrImmutable%2A> vyvolá výjimku, pokud stav není vytvořena.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrNotOpen%2A> vyvolá výjimku, pokud stav není otevřený.  
  
 Výjimky vyvolané závisí na stavu. V následující tabulce jsou uvedeny různé stavy a odpovídající typ výjimky vyvolané volání ThrowIfXxx, vyvolá se v tomto stavu.  
  
|Stav|Byla volána přerušit?|Výjimka|  
|-----------|----------------------------|---------------|  
|Vytvořeno|Není k dispozici|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Otevření|Není k dispozici|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Otevřít|Není k dispozici|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|zavírání|Ano|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|zavírání|Ne|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Zavřeno|Ano|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType> v případě, že objekt zavřel předchozí a explicitní volání přerušení. Zavřít při volání objektu a <xref:System.ObjectDisposedException?displayProperty=nameWithType> je vyvolána výjimka.|  
|Zavřeno|Ne|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Došlo k chybě|Není k dispozici|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
  
### <a name="timeouts"></a>Vypršení časových limitů  
 Několik metod, které jsme probírali přijímají parametry časového limitu. Toto jsou zavřít, Open (některých přetížení a asynchronní verze), při zavření a při otevření. Tyto metody umožňují delších operací (například blokuje na vstupu/výstupu při uzavřením dolů připojení), parametr časového limitu označuje, jak dlouho tyto operace může trvat před přerušení. Implementace některého z těchto metod používejte zadaný časový limit pro Ujistěte se, že se vrátí volajícímu v tomto časovém limitu. Implementace dalších metodách, které nepřebírají vypršení časového limitu nejsou určená pro zdlouhavé operace a by neměla blokovat na vstupu a výstupu.  
  
 Výjimky jsou Open() a Close() přetížení, které nepřebírají vypršení časového limitu. Toto použijte výchozí hodnotu časového limitu poskytnutých odvozené třídy. <xref:System.ServiceModel.Channels.CommunicationObject> zpřístupňuje dvě chráněné abstraktních a vlastností s názvem <xref:System.ServiceModel.Channels.CommunicationObject.DefaultCloseTimeout%2A> a <xref:System.ServiceModel.Channels.CommunicationObject.DefaultOpenTimeout%2A> definován jako:  
  
 `protected abstract TimeSpan DefaultCloseTimeout { get; }`  
  
 `protected abstract TimeSpan DefaultOpenTimeout { get; }`  
  
 Odvozená třída implementuje tyto vlastnosti k poskytnutí výchozí časový limit pro Open() a Close() přetížení, které se nedají zadat hodnotu časového limitu. Potom implementace Open() a Close() delegovat na přetížení přijímající vypršení časového limitu předáním výchozí hodnotu časového limitu, například:  
  
 `public void Open()`  
  
 `{`  
  
 `this.Open(this.DefaultOpenTimeout);`  
  
 `}`  
  
#### <a name="idefaultcommunicationtimeouts"></a>IDefaultCommunicationTimeouts  
 Toto rozhraní má čtyři vlastnosti jen pro čtení pro poskytnutí výchozí hodnoty časového limitu pro otevření, odesílání, příjem a zavřete. Každá implementace je odpovědný za získání výchozí hodnoty v příslušné jakýmkoli způsobem. Pro zjednodušení <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase> výchozí tyto hodnoty na 1 minutu.
