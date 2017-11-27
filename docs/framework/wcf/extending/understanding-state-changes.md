---
title: "Principy změn stavů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a79ed2aa-e49a-47a8-845a-c9f436ec9987
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 972b7e0ed9ffbc9f9ddecb2ab7afdd08626fde19
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="understanding-state-changes"></a>Principy změn stavů
Toto téma popisuje stavy a přechody, které mají kanály, typy používané struktura kanál stavy a jejich implementaci.  
  
## <a name="state-machines-and-channels"></a>Stav počítače a kanály  
 Objekty, které pracují s komunikace, například soketů, obvykle prezentovat stavu počítače, jejichž přechodů mezi stavy se týkají přidělování prostředků sítě, která nebo přijímá připojení, ukončením připojení a komunikaci se ukončuje. Stav stavového stroje kanál poskytuje jednotný model stavy komunikace objektu, který abstrahuje základní implementaci tohoto objektu. <xref:System.ServiceModel.ICommunicationObject> Rozhraní představuje sadu stavy, metody přechod stavu a události přechod stavu. Všechny kanály, objekty factory kanálu a naslouchací procesy kanál implementovat kanál stav stavového stroje.  
  
 Události uzavřeno, zavřete, Faulted, otevřeno a otevírání signalizují pozorovatele externí potom, co dojde přechod stavu.  
  
 Metody přerušení, zavřít a otevřít (a jejich ekvivalenty u asynchronní) způsobit, že přechodů mezi stavy.  
  
 Vlastnost state vrátí aktuální stav podle definice <xref:System.ServiceModel.CommunicationState>:  
  
## <a name="icommunicationobject-communicationobject-and-states-and-state-transition"></a>ICommunicationObject, objektu CommunicationObject a stavy a přechod stavu  
 <xref:System.ServiceModel.ICommunicationObject> Spustí odhlašování ve stavu vytvořen, kde se dají konfigurovat jeho různé vlastnosti. Jednou ve stavu otevřeno, objekt je použitelné pro odesílání a přijímání zpráv, ale jeho vlastnosti jsou považovány za neměnitelný. Jakmile ve stavu ukončovací objekt můžete už zpracovat nové odesílat nebo přijímat žádosti o, ale stávající požadavky mít možnost dokončit, dokud je dosaženo zavřít časový limit.  Pokud dojde k neodstranitelné chybě, objekt přechází do stavu chybný, kde může být prověřovány na informace o chybě a nakonec uzavřen. Když v uzavřeném stavu objektu v podstatě dosáhne konce stav stavového stroje. Jednou k objektu přechody mezi jednotlivými stavy na další ho nepřekračuje zpět do předchozího stavu.  
  
 Následující obrázek ukazuje <xref:System.ServiceModel.ICommunicationObject> stavy a přechody stavu. Přechody stavu může být způsobeno volání jedné ze tří metod: zrušení, otevřete, nebo zavřete. Může být také způsobeno voláním jiné metody konkrétní implementace. Přechod do stavu Faulted mohlo dojít v důsledku chyb při otevírání nebo po nutnosti otevřít objekt komunikace.  
  
 Každý <xref:System.ServiceModel.ICommunicationObject> spustí odhlašování ve stavu vytvořen. V tomto stavu můžete aplikaci nakonfigurovat objekt nastavení jeho vlastnosti. Jakmile objekt je ve stavu, než vytvořen, je považován za neměnitelný.  
  
 ![Kanálu stavu transitition](../../../../docs/framework/wcf/extending/media/channelstatetranitionshighleveldiagram.gif "ChannelStateTranitionsHighLevelDiagram")  
Obrázek 1. ICommunicationObject stav počítače.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Poskytuje abstraktní základní třídu s názvem <xref:System.ServiceModel.Channels.CommunicationObject> , která implementuje <xref:System.ServiceModel.ICommunicationObject> a stav stavového stroje kanálu. Na následujícím obrázku je upravený stav diagram, který je specifický pro <xref:System.ServiceModel.Channels.CommunicationObject>. Kromě <xref:System.ServiceModel.ICommunicationObject> stavu počítače, se zobrazí den, kdy další <xref:System.ServiceModel.Channels.CommunicationObject> jsou vyvolány metody.  
  
 ![Změny stavu](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure5statetransitionsdetailsc.gif "wcfc_WCFChannelsigure5StateTransitionsDetailsc")  
Obrázek 2. Implementace objektu CommunicationObject stav stavového stroje ICommunicationObject včetně volání události a chráněné metody.  
  
### <a name="icommunicationobject-events"></a>ICommunicationObject události  
 <xref:System.ServiceModel.Channels.CommunicationObject>zpřístupní pět události definované <xref:System.ServiceModel.ICommunicationObject>. Tyto události jsou navrženy pro kódu pomocí objekt komunikace upozornit přechodů mezi stavy. Jak je znázorněno na obrázku 2 výše, každá událost je aktivována jednou, po stav objektu přechází do stavu s názvem událost. Všechny události pět jsou `EventHandler` typ, který je definován jako:  
  
 `public delegate void EventHandler(object sender, EventArgs e);`  
  
 V <xref:System.ServiceModel.Channels.CommunicationObject> implementace, odesílatel je buď <xref:System.ServiceModel.Channels.CommunicationObject> sám sebe nebo ať byla předána jako odesílatele, aby <xref:System.ServiceModel.Channels.CommunicationObject> – konstruktor (Pokud byl použit tento konstruktor přetížení). Parametr EventArgs `e`, je vždy `EventArgs.Empty`.  
  
### <a name="derived-object-callbacks"></a>Zpětná volání odvozené objektu  
 Kromě pěti události <xref:System.ServiceModel.Channels.CommunicationObject> deklaruje osm chráněné virtuální metody navržena k umožnění objekt odvozené zpětné volání před a po přechodu stavu.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> metody mají tři takové spojené s každou z nich zpětných volání. Například odpovídající <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> je <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, a <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>. Přidružené <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> jsou <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType>, a <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> metody.  
  
 Podobně <xref:System.ServiceModel.Channels.CommunicationObject.Abort%2A?displayProperty=nameWithType> metoda má odpovídající <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType>.  
  
 Při <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, a <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType> mít žádné výchozí implementace, ostatní zpětná volání mají výchozí implementace, který je potřebný pro správnost stav počítače. Pokud je přepsat tyto metody nezapomeňte volat základní implementaci nebo správně jej nahradit.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.CommunicationObject.OnFaulted%2A?displayProperty=nameWithType> fire odpovídající <xref:System.ServiceModel.Channels.CommunicationObject.Opening?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.Closing?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.CommunicationObject.Faulted?displayProperty=nameWithType> události. <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>a <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> nastavit stav objektu otevřeno a uzavřené v uvedeném pořadí a provést odpovídající <xref:System.ServiceModel.Channels.CommunicationObject.Opened?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.CommunicationObject.Closed?displayProperty=nameWithType> události.  
  
### <a name="state-transition-methods"></a>Metody přechod stavu  
 <xref:System.ServiceModel.Channels.CommunicationObject>poskytuje implementaci přerušení, zavřete a otevřete. Nabízí taky metoda selhání, což způsobí, že přechod stavu chybném stavu. Obrázek 2 ukazuje <xref:System.ServiceModel.ICommunicationObject> stavový stroj při každém přechodu označené metodu, která způsobí, že ho (bez popisku přechody dojít uvnitř provádění metodu, která způsobila, že poslední s popiskem přechodu).  
  
> [!NOTE]
>  Všechny <xref:System.ServiceModel.Channels.CommunicationObject> implementace komunikace stavu, získá nebo nastaví jsou synchronizovány přístup z více vláken.  
  
 Konstruktor  
  
 <xref:System.ServiceModel.Channels.CommunicationObject>poskytuje tři konstruktory, z nichž všechny nechte objekt ve stavu vytvořen. Konstruktory jsou definovány jako:  
  
 První konstruktor je výchozí konstruktor, který deleguje konstruktor přetížení, která přebírá objekt:  
  
 `protected CommunicationObject() : this(new object()) { … }`  
  
 Konstruktor, který přebírá objekt používá tento parametr jako objekt se uzamkne při synchronizaci přístup k stav objektu komunikace:  
  
 `protected CommunicationObject(object mutex) { … }`  
  
 Nakonec třetí konstruktor přebírá další parametr, který se používá jako argument odesílatele při <xref:System.ServiceModel.ICommunicationObject> při vyvolání událostí.  
  
 `protected CommunicationObject(object mutex, object eventSender) { … }`  
  
 Předchozí dva konstruktory nastavit odesílatel to.  
  
 Open – metoda  
  
 Předběžnou: Stav je vytvořen.  
  
 Po podmínka: Stav je otevřeno nebo Faulted. Může vyvolat výjimku.  
  
 Metoda Open() se pokusí otevřít objekt komunikace a nastavit stav na otevřeno. Pokud dojde k chybě, nastaví pro chybný stav.  
  
 Metoda nejdřív zkontroluje vytvořený aktuální stav. Pokud je aktuální stav otevírání nebo otevřít, se vrátí <xref:System.InvalidOperationException>. Pokud aktuální stav je ukončovací nebo Uzavřeno, vyvolá výjimku <xref:System.ServiceModel.CommunicationObjectAbortedException> Pokud byla ukončena objekt a <xref:System.ObjectDisposedException> jinak. Pokud došlo k chybě v aktuálním stavu, vyvolá výjimku <xref:System.ServiceModel.CommunicationObjectFaultedException>.  
  
 Potom nastaví stav k otevírání a volá OnOpening() (který vyvolá událost otevření), OnOpen() a OnOpened() v tomto pořadí. OnOpened() nastaví stav otevřeno a vyvolá událost otevřeno. Pokud platí jedna z těchto vyvolá výjimku, (Otevřít) volá Fault() a umožňuje bublin výjimka. Následující diagram znázorňuje proces otevřete podrobněji.  
  
 ![Změny stavu](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigurecoopenflowchartf.gif "wcfc_WCFChannelsigureCOOpenFlowChartf")  
Potlačení při otevření metody k implementaci vlastní logiky otevřete například otevírání objekt vnitřní komunikace.  
  
 Close – metoda  
  
 Předběžné podmínky: žádné.  
  
 Po podmínku: Stav je uzavřený. Může vyvolat výjimku.  
  
 Ve všech stavu nelze volat metodu Close(). Pokusí se obvykle zavřete objekt. Pokud dojde k chybě, ukončí objekt. Metoda nemá nic, pokud aktuální stav ukončuje nebo Uzavřeno. Jinak nastaví stav na Zavřít. Pokud původní stav byl vytvořen, otevření nebo Faulted, zavolá Abort() (viz následující obrázek). Pokud byl otevřen původního stavu, zavolá OnClosing() (která vyvolává událost uzavírací), OnClose() a OnClosed() v tomto pořadí. Pokud platí jedna z těchto vyvolá výjimku, (Zavřít) volá Abort() a umožňuje bublin výjimka. OnClosed() nastaví stav na uzavřený a vyvolá událost, uzavřené. Následující diagram ukazuje ukončení procesu podrobněji.  
  
 ![Změny stavu](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsguire7ico-closeflowchartc.gif "wcfc_WCFChannelsguire7ICO CloseFlowChartc")  
Potlačí metodu při zavření k implementaci vlastní logiky zavřít, například zavření objektu vnitřní komunikace. Všechny řádné zavření logiky, která může blokovat pro dlouhou dobu (například čekání na druhé straně reagovat) by měla být implementována v OnClose(), protože má parametr časového limitu a z toho důvodu není volána v rámci Abort().  
  
 Přerušení  
  
 Předběžné podmínky: žádné.  
Po podmínku: Stav je uzavřený. Může vyvolat výjimku.  
  
 Metoda Abort() neprovede žádnou akci, pokud aktuální stav je zavřené nebo pokud objekt byl ukončen před (například pravděpodobně tak, že Abort() provádění na jiné vlákno). Jinak nastaví stav uzavírací a volá OnClosing() (která vyvolává událost uzavírací), OnAbort() a OnClosed() v tomto pořadí (nevyvolá při zavření vzhledem k tomu, že objekt je ukončovány, neuzavřené). OnClosed() nastaví stav na uzavřený a vyvolá událost, uzavřené. Pokud některý z těchto způsobí výjimku, je znovu vyvolána volajícímu přerušení. Implementace OnClosing(), OnClosed() a OnAbort() by neměly blokovat (například na vstup/výstup). Následující diagram znázorňuje proces přerušení podrobněji.  
  
 ![Změny stavu](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure8ico-abortflowchartc.gif "wcfc_WCFChannelsigure8ICO AbortFlowChartc")  
Přepsání metody OnAbort implementovat vlastní ukončit logiku, jako je objekt vnitřní komunikace se ukončuje.  
  
 Selhání  
  
 Metoda selhání je specifická pro <xref:System.ServiceModel.Channels.CommunicationObject> a nejsou součástí <xref:System.ServiceModel.ICommunicationObject> rozhraní. Je zde uveden pro úplnost.  
  
 Předběžné podmínky: žádné.  
  
 Po podmínku: Stavu došlo k chybě. Může vyvolat výjimku.  
  
 Metoda Fault() neprovede žádnou akci, pokud aktuální stav je chybný nebo Uzavřeno. Jinak nastaví stav a OnFaulted(), která vyvolává událost Faulted volání chybném. Pokud OnFaulted vyvolá výjimku je znovu.  
  
### <a name="throwifxxx-methods"></a>ThrowIfXxx metody  
 V objektu CommunicationObject má tři chráněné metody, které lze použít k vyvolání výjimky, pokud je objekt v určitém stavu.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposed%2A>Pokud stav není pravé, Uzavřeno nebo Faulted, vyvolá výjimku.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrImmutable%2A>vyvolá výjimku, pokud stav není vytvořena.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrNotOpen%2A>vyvolá výjimku, pokud stav není otevřený.  
  
 Výjimky vydané závisí na stavu. Následující tabulka uvádí různé stavy a odpovídající typ výjimky vyvolané volání ThrowIfXxx, který vyvolá v tomto stavu.  
  
|Stav|Bylo voláno zrušení?|Výjimka|  
|-----------|----------------------------|---------------|  
|Vytvořit|Není k dispozici|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Otevírání|Není k dispozici|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Otevřít|Není k dispozici|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|zavírání|Ano|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|zavírání|Ne|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Zavřeno|Ano|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>v případě, že objekt bylo ukončeno předchozí a explicitní volání přerušení. Když zavoláte zavřít na objekt pak <xref:System.ObjectDisposedException?displayProperty=nameWithType> je vyvolána výjimka.|  
|Zavřeno|Ne|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Došlo k chybě|Není k dispozici|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
  
### <a name="timeouts"></a>Časové limity  
 Několik metod, které jsme probrali trvat parametry časového limitu. Jsou to zavře, otevřete (určité přetížení a asynchronní verze), při zavření a při otevření. Tyto metody jsou navrženy tak, aby bylo možné náročná operace (například blokování na vstupu a výstupu při zavírání řádně dolů připojení), vypršení časového limitu parametr určuje, jak dlouho tyto operace může trvat před se přerušena. Implementace některé z těchto metod použití hodnota časového limitu zadaný zajistit, že vrátí volajícího v tomto časovém limitu. Implementace dalších metodách, které nepřebírají vypršení časového limitu nejsou navrženy pro náročná operace a by neměly blokovat na vstupu a výstupu.  
  
 Výjimkou jsou Open() a Close() přetížení, které nepřebírají vypršení časového limitu. Tyto použijte výchozí hodnotu časového limitu poskytl odvozené třídy. <xref:System.ServiceModel.Channels.CommunicationObject>zpřístupňuje dva chráněné abstraktních a vlastností s názvem <xref:System.ServiceModel.Channels.CommunicationObject.DefaultCloseTimeout%2A> a <xref:System.ServiceModel.Channels.CommunicationObject.DefaultOpenTimeout%2A> definován jako:  
  
 `protected abstract TimeSpan DefaultCloseTimeout { get; }`  
  
 `protected abstract TimeSpan DefaultOpenTimeout { get; }`  
  
 Odvozená třída implementuje tyto vlastnosti zajistit výchozí časový limit pro Open() a Close() přetížení, které nepřebírají hodnotu časového limitu. Potom implementace Open() a Close() delegovat na přetížení, které přijímá vypršení časového limitu předání výchozí hodnotu časového limitu, například:  
  
 `public void Open()`  
  
 `{`  
  
 `this.Open(this.DefaultOpenTimeout);`  
  
 `}`  
  
#### <a name="idefaultcommunicationtimeouts"></a>IDefaultCommunicationTimeouts  
 Toto rozhraní má čtyři jen pro čtení vlastnosti pro poskytnutí výchozí hodnoty časového limitu pro otevřete, odesílání, příjem a zavřete. Každá implementace je zodpovědná za získání výchozí hodnoty v příslušné jakýmkoli způsobem. Pro potřeby <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase> výchozí tyto hodnoty na 1 minutu.
