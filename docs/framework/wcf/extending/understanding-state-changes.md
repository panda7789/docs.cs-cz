---
title: Principy změn stavů
ms.date: 03/30/2017
ms.assetid: a79ed2aa-e49a-47a8-845a-c9f436ec9987
ms.openlocfilehash: f6ce9875a4ebecf11f1f8d08d681841773d9f841
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447513"
---
# <a name="understanding-state-changes"></a>Principy změn stavů
Toto téma popisuje stavy a přechody, které kanály obsahují, typy používané ke strukturování stavů kanálů a jejich implementaci.  
  
## <a name="state-machines-and-channels"></a>Stavové počítače a kanály  
 Objekty, které se zabývají komunikací, například sokety, obvykle prezentují Stavový počítač, jehož přechody stavu se vztahují k přidělování síťových prostředků, vytváření nebo přijímání připojení, zavírání připojení a ukončení komunikace. Stavový počítač kanálu poskytuje jednotný model stavů komunikačního objektu, který vyabstrakce základní implementaci tohoto objektu. Rozhraní <xref:System.ServiceModel.ICommunicationObject> poskytuje sadu stavů, metody přechodu stavu a události přechodu stavu. Všechny kanály, továrny kanálů a naslouchací procesy kanálu implementují Stavový počítač kanálu.  
  
 Po přechodu stavu dojde k zavření, zavření, chybě, otevření a otevření signálu externí pozorovatel.  
  
 Metody přeruší, zavřou a otevřou (a jejich asynchronní ekvivalenty) způsobují přechody stavu.  
  
 Vlastnost State vrátí aktuální stav definovaný pomocí <xref:System.ServiceModel.CommunicationState>:  
  
## <a name="icommunicationobject-communicationobject-and-states-and-state-transition"></a>Objekt ICommunicationObject, CommunicationObject a stavy a přechody stavu  
 <xref:System.ServiceModel.ICommunicationObject> se spustí ve stavu Created, ve kterém se dají nakonfigurovat jeho různé vlastnosti. Jednou v otevřeném stavu lze objekt použít pro odesílání a příjem zpráv, ale jeho vlastnosti jsou považovány za neměnné. V konečném stavu nemůže objekt nadále zpracovávat nové žádosti o odeslání nebo přijetí, ale existující požadavky mohou být dokončeny až do dosažení časového limitu ukončení.  Pokud dojde k neopravitelné chybě, objekt přejde do chybového stavu, kde je možné zkontrolovat informace o chybě a nakonec uzavřít. V případě, že je v zavřeném stavu, je objekt v zásadě dosaženo na konci stavového počítače. Jakmile se objekt přehraje z jednoho stavu na další, nevrátí se do předchozího stavu.  
  
 Následující diagram znázorňuje <xref:System.ServiceModel.ICommunicationObject> stavy a přechody stavu. Přechody stavu mohou být způsobeny voláním jedné ze tří metod: Abort, Open nebo Close. Mohou být také způsobeny voláním jiných metod specifických pro implementaci. Přechod na chybový stav může nastat v důsledku chyb při otevírání nebo po otevření objektu komunikace.  
  
 Každý <xref:System.ServiceModel.ICommunicationObject> začíná ve stavu Created (vytvořeno). V tomto stavu může aplikace nakonfigurovat objekt nastavením jeho vlastností. Jakmile je objekt v jiném než vytvořeném stavu, je považován za neproměnlivý.  
  
 ![Diagram toku dat přechodu stavu kanálu](./media/understanding-state-changes/channel-state-transitions.gif)  
Obrázek 1. Stavový počítač objekt ICommunicationObject.  
  
 Windows Communication Foundation (WCF) poskytuje abstraktní základní třídu s názvem <xref:System.ServiceModel.Channels.CommunicationObject>, která implementuje <xref:System.ServiceModel.ICommunicationObject> a Stavový počítač kanálu. Následující obrázek je upravený diagram stavu, který je specifický pro <xref:System.ServiceModel.Channels.CommunicationObject>. Kromě stavového počítače <xref:System.ServiceModel.ICommunicationObject> zobrazuje časování při vyvolání dalších metod <xref:System.ServiceModel.Channels.CommunicationObject>.  
  
 ![diagram toku dat pro změny stavu implementace CommunicationObject](./media/understanding-state-changes/communicationobject-implementation-state-machine.gif)
Obrázek 2. Implementace CommunicationObject stavového počítače objekt ICommunicationObject, včetně volání událostí a chráněných metod.  
  
### <a name="icommunicationobject-events"></a>Události objekt ICommunicationObject  
 <xref:System.ServiceModel.Channels.CommunicationObject> zveřejňuje pět událostí definovaných pomocí <xref:System.ServiceModel.ICommunicationObject>. Tyto události jsou navržené pro kód pomocí objektu komunikace, který bude upozorněn na přechody stavu. Jak je znázorněno na obrázku 2 výše, každá událost je aktivována jednou po přechodu stavu objektu do stavu s názvem událost. Všechna pět událostí jsou `EventHandler`ho typu, který je definován jako:  
  
 `public delegate void EventHandler(object sender, EventArgs e);`  
  
 V <xref:System.ServiceModel.Channels.CommunicationObject> implementace je odesílatel buď <xref:System.ServiceModel.Channels.CommunicationObject> sám sebe, nebo cokoli, co bylo předáno jako odesilatel do konstruktoru <xref:System.ServiceModel.Channels.CommunicationObject> (pokud bylo použito přetížení konstruktoru). Parametr EventArgs, `e`, je vždy `EventArgs.Empty`.  
  
### <a name="derived-object-callbacks"></a>Odvozená zpětná volání objektů  
 Kromě pěti událostí <xref:System.ServiceModel.Channels.CommunicationObject> deklaruje osm chráněných virtuálních metod navržených tak, aby odvozený objekt mohl být volán zpět před a po probíhají přechody stavu.  
  
 Metody <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> mají tři tato zpětná volání přidružená ke každému z nich. Například odpovídá <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>a <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType>. Přidružená k <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> jsou metody <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType>a <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType>.  
  
 Podobně, <xref:System.ServiceModel.Channels.CommunicationObject.Abort%2A?displayProperty=nameWithType> metoda má odpovídající <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType>.  
  
 I když <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=nameWithType>a <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=nameWithType> nemají žádnou výchozí implementaci, ostatní zpětná volání mají výchozí implementaci, která je nezbytná pro správnost stavového počítače. Pokud přepíšete tyto metody, ujistěte se, že jste volali základní implementaci nebo ji správně nahradili.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.CommunicationObject.OnFaulted%2A?displayProperty=nameWithType> vyvolávat odpovídající události <xref:System.ServiceModel.Channels.CommunicationObject.Opening?displayProperty=nameWithType>, <xref:System.ServiceModel.Channels.CommunicationObject.Closing?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.CommunicationObject.Faulted?displayProperty=nameWithType>. <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=nameWithType> nastaví stav objektu na otevřeno a uzavřeno, potom aktivuje odpovídající <xref:System.ServiceModel.Channels.CommunicationObject.Opened?displayProperty=nameWithType> a události <xref:System.ServiceModel.Channels.CommunicationObject.Closed?displayProperty=nameWithType>.  
  
### <a name="state-transition-methods"></a>Metody přechodu stavu  
 <xref:System.ServiceModel.Channels.CommunicationObject> poskytuje implementace přerušení, zavřít a otevřít. Poskytuje také metodu selhání, která způsobuje přechod stavu do chybového stavu. Obrázek 2 ukazuje <xref:System.ServiceModel.ICommunicationObject> stavového počítače s každým přechodem, který je označený metodou, která to způsobuje (v rámci implementace metody, která způsobila poslední přechod na návěští).  
  
> [!NOTE]
> Všechny <xref:System.ServiceModel.Channels.CommunicationObject> implementace stavu komunikace, které získá nebo nastaví, jsou synchronizované z více vláken.  
  
 Konstruktor  
  
 <xref:System.ServiceModel.Channels.CommunicationObject> poskytuje tři konstruktory, z nichž všechny opustí objekt ve stavu Created. Konstruktory jsou definovány takto:  
  
 První konstruktor je konstruktor bez parametrů, který deleguje přetížení konstruktoru, který přebírá objekt:  
  
 `protected CommunicationObject() : this(new object()) { … }`  
  
 Konstruktor, který přebírá objekt, používá tento parametr jako objekt, který se má uzamknout při synchronizaci přístupu ke stavu objektu komunikace:  
  
 `protected CommunicationObject(object mutex) { … }`  
  
 Nakonec třetí konstruktor přebírá další parametr, který se používá jako argument Sender při vyvolání události <xref:System.ServiceModel.ICommunicationObject>.  
  
 `protected CommunicationObject(object mutex, object eventSender) { … }`  
  
 Předchozí dva konstruktory nastavili odesílatele na this.  
  
 Open – metoda  
  
 Předběžná podmínka: stav je vytvořen.  
  
 Po stavu: stav je otevřeno nebo chyba. Může vyvolat výjimku.  
  
 Metoda Open () se pokusí otevřít objekt komunikace a nastavit stav na otevřeno. Pokud dojde k chybě, nastaví se stav na chyba.  
  
 Metoda nejprve zkontroluje, zda je aktuální stav vytvořen. Pokud je aktuální stav otevřený nebo otevřený, vyvolá <xref:System.InvalidOperationException>. Pokud je aktuální stav uzavřen nebo zavřen, vyvolá <xref:System.ServiceModel.CommunicationObjectAbortedException>, pokud byl objekt ukončen a <xref:System.ObjectDisposedException> jinak. Pokud dojde k chybě aktuálního stavu, vyvolá <xref:System.ServiceModel.CommunicationObjectFaultedException>.  
  
 Poté nastaví stav na otevírání a volání při otevření () (což vyvolává událost otevření), událost otevření () a otevřené () v tomto pořadí. Open () nastaví stav na otevřeno a vyvolá otevřenou událost. Pokud některý z těchto vyvolání vyvolá výjimku, příkaz Open () volá chybu () a umožňuje bublinu výjimky. Následující diagram znázorňuje otevření procesu podrobněji.  
  
 ![Diagram toku dat objekt ICommunicationObject. otevřít změny stavu](./media/understanding-state-changes/ico-open-process-override-onopen.gif)  
Přepište metodu Open pro implementaci vlastní otevřené logiky, jako je například otevření objektu vnitřní komunikace.  
  
 Close – metoda  
  
 Předběžná podmínka: žádné.  
  
 Po stavu: stav je uzavřeno. Může vyvolat výjimku.  
  
 Metodu Close () lze volat v jakémkoli stavu. Pokusí se objekt zavřít normálně. Pokud dojde k chybě, dojde k ukončení objektu. Metoda neprovede nic, pokud je aktuální stav uzavřený nebo zavřený. V opačném případě nastaví stav na Zavřít. Pokud byl původní stav vytvořen, otevírání nebo chyba, volá funkci Abort () (viz následující diagram). Pokud byl původní stav otevřen, volání příkazu "Close ()" (což vyvolává událost ukončení), "Close" () a "Closed" () v tomto pořadí. Pokud některý z těchto vyvolá výjimku, volání Close () volá Abort () a umožňuje bublinu výjimky nahoru. -Closeed () nastaví stav na uzavřeno a vyvolá uzavřenou událost. Následující diagram znázorňuje proces zavření podrobněji.  
  
 ![Diagram toku dat pro objekt ICommunicationObject. Zavřete změny stavu.](./media/understanding-state-changes/ico-close-process-override-onclose.gif)  
Přepište metodu Close pro implementaci vlastní logiky ukončení, jako je například zavření objektu vnitřní komunikace. Veškerá plynulá uzavírací logika, která může být zablokovaná dlouhou dobu (například čekání na druhou stranu reakce), by měla být implementována v operaci Close (), protože má parametr timeout a protože není volána jako součást přerušení ().  
  
 Přerušení  
  
 Předběžná podmínka: žádné.  
Po stavu: stav je uzavřeno. Může vyvolat výjimku.  
  
 Metoda Abort () nedělá nic, pokud je aktuální stav uzavřen nebo pokud byl objekt ukončen dříve (například může mít přerušení () prováděné v jiném vlákně). V opačném případě nastaví stav na zavírání a volání metody "Close" () (která vyvolává uzavírací událost), operace "Abort () a" uzavřeno "() v tomto pořadí () v tomto pořadí (nevolá funkci Close, protože objekt je právě ukončován, nikoli uzavřený). -Closeed () nastaví stav na uzavřeno a vyvolá uzavřenou událost. Pokud některý z těchto výjimek vyvolá výjimku, je znovu vyvolána volajícímu přerušení. Implementace příkazového začátku (), Closeed () a Abort () by neměly blokovat (například při vstupu/výstupu). Následující diagram znázorňuje proces přerušení podrobněji.  
  
 ![Diagram toku dat objekt ICommunicationObject. Abort změny stavu.](./media/understanding-state-changes/ico-abort-process-override-onabort.gif)  
Přepište metodu-Abort pro implementaci vlastní logiky ukončení, jako je například ukončení objektu vnitřní komunikace.  
  
 Indikován  
  
 Metoda Fault je specifická pro <xref:System.ServiceModel.Channels.CommunicationObject> a není součástí rozhraní <xref:System.ServiceModel.ICommunicationObject>. Je zde obsažena pro úplnost.  
  
 Předběžná podmínka: žádné.  
  
 Post-Condition: stav je chybný. Může vyvolat výjimku.  
  
 Metoda Fault () nedělá nic, pokud je aktuální stav chybný nebo uzavřený. V opačném případě nastaví stav na chyba a volání došlo k chybě (), což vyvolá událost s chybou. Pokud došlo k chybě, vyvolá výjimku, která je znovu vyvolána.  
  
### <a name="throwifxxx-methods"></a>Metody ThrowIfXxx  
 CommunicationObject má tři chráněné metody, které lze použít k vyvolání výjimek, je-li objekt v určitém stavu.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposed%2A> vyvolá výjimku, pokud je stav ukončován, uzavřený nebo chyba.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrImmutable%2A> vyvolá výjimku, pokud stav není vytvořen.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrNotOpen%2A> vyvolá výjimku, pokud stav není otevřen.  
  
 Vyvolané výjimky závisí na stavu. V následující tabulce jsou uvedeny různé stavy a odpovídající typ výjimky vyvolaný voláním ThrowIfXxx, který tento stav vyvolá.  
  
|Stát|Volala se přerušení?|Výjimka|  
|-----------|----------------------------|---------------|  
|Datum vytvoření|NEUŽÍVÁ SE.|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Zahájil|NEUŽÍVÁ SE.|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|Otevřít|NEUŽÍVÁ SE.|<xref:System.InvalidOperationException?displayProperty=nameWithType>|  
|zavírání|Ano|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|zavírání|Ne|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Uzavřeno|Ano|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType> v případě, že objekt byl zavřen předchozím a explicitním voláním metody Abort. Pokud zavoláte zavřít u objektu, je vyvolána <xref:System.ObjectDisposedException?displayProperty=nameWithType>.|  
|Uzavřeno|Ne|<xref:System.ObjectDisposedException?displayProperty=nameWithType>|  
|Došlo chybě|NEUŽÍVÁ SE.|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
  
### <a name="timeouts"></a>Vypršení časových limitů  
 Některé z metod, které jsme provzali, přijímá parametry časového limitu. Jedná se o zavřít, otevřít (určitá přetížení a asynchronní verze), uzavřít a otevřít. Tyto metody jsou navržené tak, aby umožňovaly zdlouhavé operace (například blokování vstupu/výstupu při řádném ukončení připojení), takže parametr timeout označuje, jak dlouho můžou tyto operace trvat, než se přeruší. Implementace kterékoli z těchto metod by měly použít poskytnutou hodnotu časového limitu, aby se zajistilo, že se vrátí volajícímu v daném časovém limitu. Implementace jiných metod, které nevezmou časový limit, nejsou navrženy pro zdlouhavé operace a neměly by být zablokované na vstupu a výstupu.  
  
 Výjimkou jsou přetížení Open () a Close (), které nevyžadují časový limit. Používají výchozí hodnotu časového limitu poskytnutou odvozenou třídou. <xref:System.ServiceModel.Channels.CommunicationObject> zpřístupňuje dvě chráněné abstraktní vlastnosti s názvem <xref:System.ServiceModel.Channels.CommunicationObject.DefaultCloseTimeout%2A> a <xref:System.ServiceModel.Channels.CommunicationObject.DefaultOpenTimeout%2A> definovány jako:  
  
 `protected abstract TimeSpan DefaultCloseTimeout { get; }`  
  
 `protected abstract TimeSpan DefaultOpenTimeout { get; }`  
  
 Odvozená třída implementuje tyto vlastnosti, aby poskytovala výchozí časový limit pro přetížení Open () a Close (), která nevyužívají hodnotu časového limitu. Implementací () a Close () implementací přenese delegáta, který má časový limit k předání hodnoty výchozí časový limit, například:  
  
 `public void Open()`  
  
 `{`  
  
 `this.Open(this.DefaultOpenTimeout);`  
  
 `}`  
  
#### <a name="idefaultcommunicationtimeouts"></a>IDefaultCommunicationTimeouts  
 Toto rozhraní obsahuje čtyři vlastnosti jen pro čtení pro poskytování výchozích hodnot časového limitu pro možnosti otevřít, odeslat, přijmout a zavřít. Každá implementace zodpovídá za získání výchozích hodnot jakýmkoli způsobem. Jako pohodlí <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase> výchozí hodnoty 1 minuty.
