---
title: Rozšíření klientů
ms.date: 03/30/2017
helpviewer_keywords:
- proxy extensions [WCF]
ms.assetid: 1328c61c-06e5-455f-9ebd-ceefb59d3867
ms.openlocfilehash: 48e6177e7098f8131d2a0fd62bda9c505fa8bcc9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662806"
---
# <a name="extending-clients"></a>Rozšíření klientů
Volající aplikace je zodpovědná za překládá volání metod v kódu aplikace do odchozích zpráv, jejich ukládání do základní kanálů, překlad výsledky zpátky na návratové hodnoty ani výstupní parametry v vrstva modelu služby kód aplikace a vrací výsledky zpět volajícímu. Rozšíření modelů služeb změnit nebo implementovat provádění nebo chování komunikace a funkce zahrnující funkce klienta nebo dispečer, vlastní chování, zprávy a parametr zachycení a další funkce rozšíření.  
  
 Toto téma popisuje způsob použití <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.ClientOperation> třídy v aplikaci klienta Windows Communication Foundation (WCF) Chcete-li změnit výchozí chování při spuštění klienta WCF a zachytit a změny zpráv, parametry nebo návratové hodnoty před nebo po odeslání nebo načítání z vrstvy kanálu. Další informace o rozšíření modulu runtime služby najdete v tématu [rozšíření dispečerů](../../../../docs/framework/wcf/extending/extending-dispatchers.md). Další informace o chování, které upravují a insert přizpůsobení objektů pro modul runtime klienta najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="clients"></a>Klienti  
 Kanál klienta nebo objektu klienta WCF na klientovi, převede volání metod na odchozí zprávy a příchozí zprávy pro výsledky operace, které jsou vráceny do volající aplikace. (Další informace o typech klienta najdete v tématu [Architektura klienta WCF](../../../../docs/framework/wcf/feature-details/client-architecture.md).)  
  
 Typ klienta WCF mít typy runtime, které zpracovávají tuto funkci úrovni koncového bodu a operace. Když aplikace volá operaci <xref:System.ServiceModel.Dispatcher.ClientOperation> přeloží odchozí objekty do zprávy, zpracuje sběrače, potvrdí, že odpovídá kontrakt cílů odchozí volání a předá výstupní zpráva, která má <xref:System.ServiceModel.Dispatcher.ClientRuntime>, což je zodpovědný za vytváření a správě odchozích kanálů (a příchozí kanály v případě duplexní služby), zpracování velmi odchozí zprávy (jako je například změna záhlaví) zpracování, zpracování zpráv sběrače v obou směrech a směrování příchozí duplexní volání odpovídající na straně klienta <xref:System.ServiceModel.Dispatcher.DispatchRuntime> objektu. Jak <xref:System.ServiceModel.Dispatcher.ClientOperation> a <xref:System.ServiceModel.Dispatcher.ClientRuntime> poskytují podobné služby, které při zpráv (chyb včetně) se vrátíte do klienta.  
  
 Tyto dvě třídy modulu runtime jsou hlavní rozšíření přizpůsobit zpracování objektů klienta WCF a kanály. <xref:System.ServiceModel.Dispatcher.ClientRuntime> Třída umožňuje uživatelům zachytit a spuštění klienta přesahují všechny zprávy v kontraktu. <xref:System.ServiceModel.Dispatcher.ClientOperation> Třída umožňuje uživatelům zachytit a rozšířit spuštění klienta pro všechny zprávy v danou operaci.  
  
 Úpravou vlastností nebo vkládání vlastní nastavení se provádí pomocí kontraktu koncového bodu a chování operace. Další informace o tom, jak používat tyto typy chování k vlastnímu modul runtime klienta najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="scenarios"></a>Scénáře  
 Tam několik důvodů, proč rozšíření systému klienta, včetně:  
  
- Ověření vlastní zprávu. Uživatel může být vhodné vynutit platnost zprávy pro určité schéma. To můžete udělat pomocí implementace <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> rozhraní a přiřazování implementaci <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A> vlastnost. Příklady najdete v tématu [jak: Kontrola a změny zpráv na straně klienta](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md) a [jak: Kontrola a změny zpráv na straně klienta](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
- Protokolování vlastních zpráv. Uživatel může být vhodné ke kontrole a některé sadu zpráv aplikace, které probíhá přes koncový bod protokolu. To můžete provést také pomocí rozhraní zachycování zpráv.  
  
- Vlastní zpráva transformace. Spíše než změnit kód aplikace, uživatel může chtít použití některých transformací na zpráv v modulu runtime (například Správa verzí). Toho můžete docílit, znovu s rozhraním zachycování zpráv.  
  
- Vlastní datový Model. Uživatel může chtít modelu dat nebo serializace než ty, které nepodporuje ve výchozím nastavení ve službě WCF (konkrétně <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>, a <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> objekty). To můžete udělat pomocí implementace rozhraní formátovací modul zpráv. Další informace najdete v tématu <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType> a <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A?displayProperty=nameWithType> vlastnost.  
  
- Ověření vlastního parametru. Uživatel může chtít zajistit, že zadané parametry jsou platné (na rozdíl od XML). To lze provést pomocí rozhraní inspektoru parametru. Příklad najdete v tématu [jak: Kontrola nebo úprava parametrů](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md) nebo [ověřování na straně klienta](../../../../docs/framework/wcf/samples/client-validation.md).  
  
### <a name="using-the-clientruntime-class"></a>Pomocí třídy ClientRuntime  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime> Třída je bod rozšiřitelnosti pro které můžete přidat objekty rozšíření, které zachytit zprávy a rozšíření chování klienta. Zachycení objektů můžete zpracovávat všechny zprávy v konkrétní smlouvy, zpracovat pouze zprávy pro konkrétní operace, provedení inicializace vlastního kanálu a implementovat další chování vlastní klientské aplikace.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> Vrátí vlastnost run-time objekt odeslání pro klienty spouštěných službou zpětného volání.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.OperationSelector%2A> Tato vlastnost přijímá parametry objektu výběr vlastní operace.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ChannelInitializers%2A> Vlastnost umožňuje přidání inicializátoru kanál, který může kontrola nebo úprava kanálu klienta.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> Vlastnost získá kolekci <xref:System.ServiceModel.Dispatcher.ClientOperation> objekty, na které můžete přidat vlastní zprávu sběrače, které poskytují funkce, které jsou specifické pro zprávy této operace.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ManualAddressing%2A> Vlastnost umožní aplikaci chcete-li vypnout automatické adresování záhlaví přímo řídit adresování.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.Via%2A> Vlastnost nastaví hodnotu cíl zprávy na úrovni přenosu pro podporu zprostředkovatele a další scénáře.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> Vlastnost získá kolekci <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> objekty, na které můžete přidat vlastní zprávu sběrače pro všechny zprávy procházející klienta WCF.  
  
 Kromě toho existuje několik dalších vlastností, které načítají informace o smlouvě:  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractName%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractNamespace%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractClientType%2A>  
  
 Pokud je klient WCF duplexní klienta WCF, následující vlastnosti také načíst zpětného volání klienta informace WCF:  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackClientType%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>  
  
 Spuštění klienta WCF rozšířit napříč celou klienta WCF, zkontrolujte vlastnosti k dispozici na <xref:System.ServiceModel.Dispatcher.ClientRuntime> třídy naleznete v tématu, zda úpravu vlastnosti nebo implementace rozhraní a jejich přidání do vlastnosti vytvoří funkci, která požadujete. Po výběru konkrétního rozšíření k sestavení, vložení rozšíření do příslušné <xref:System.ServiceModel.Dispatcher.ClientRuntime> vlastnost implementací chování klienta, který poskytuje přístup k <xref:System.ServiceModel.Dispatcher.ClientRuntime> třídy při vyvolání.  
  
 Rozšíření vlastních objektů můžete vložit do kolekce pomocí na chování operace (objekt, který implementuje <xref:System.ServiceModel.Description.IOperationBehavior>), smlouva chování (objekt, který implementuje <xref:System.ServiceModel.Description.IContractBehavior>), nebo chování koncového bodu (objekt, který implementuje <xref:System.ServiceModel.Description.IEndpointBehavior> ). Instalace chování objektu se přidá do příslušné kolekce chování prostřednictvím kódu programu, deklarativně (prostřednictvím implementace vlastního atributu), nebo prostřednictvím implementace vlastního <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> objekt, má-li povolit chování, které má být vložen pomocí konfigurační soubor aplikace. Podrobnosti najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Příklady, které ukazují zachycení napříč klienta WCF najdete v tématu [jak: Kontrola a změny zpráv na straně klienta](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
### <a name="using-the-clientoperation-class"></a>Pomocí třídy ClientOperation  
 <xref:System.ServiceModel.Dispatcher.ClientOperation> Třídy je umístění pro klienta za běhu úpravy a vložení bod pro vlastní rozšíření, která jsou omezená jen jedna operace. (Chcete-li upravit chování klienta za běhu pro všechny zprávy ve smlouvě, použijte <xref:System.ServiceModel.Dispatcher.ClientRuntime> třídy.)  
  
 Použití <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> vlastnost najít <xref:System.ServiceModel.Dispatcher.ClientOperation> objekt, který reprezentuje operaci konkrétní službu. Následující vlastnosti umožňují vkládání vlastní objekty do systému klienta WCF:  
  
- Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> vlastnost vložit vlastní <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementaci pro operace nebo upravit aktuální formátovacího modulu.  
  
- Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A> vlastnost vložit vlastní <xref:System.ServiceModel.Dispatcher.IParameterInspector> implementace nebo upravovat stávající.  
  
 Tyto vlastnosti umožňují změnit systému v interakci s formátovacího modulu a vlastní parametr kontroly:  
  
- Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.SerializeRequest%2A> vlastnost k řízení serializace odchozí zprávy.  
  
- Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.DeserializeReply%2A> vlastnost k řízení serializace příchozí zprávy.  
  
- Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.Action%2A> vlastnost řídit akce WS-Adressing zprávy s požadavkem.  
  
- Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.BeginMethod%2A> a <xref:System.ServiceModel.Dispatcher.ClientOperation.EndMethod%2A> k určení, které metody klienta WCF, které jsou přidružené asynchronní operace.  
  
- Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.FaultContractInfos%2A> jako typ podrobností chyb stránkování k získání kolekce, která obsahuje typy, které se mohou objevit v protokolu SOAP.  
  
- Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.IsInitiating%2A> a <xref:System.ServiceModel.Dispatcher.ClientOperation.IsTerminating%2A> vlastností do ovládacího prvku, zda je relace je zahájeno nebo odpojí dolů se při volání operace.  
  
- Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.IsOneWay%2A> vlastnost řídit, zda operace je jednosměrná operace.  
  
- Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.Parent%2A> vlastnost k získání obsahující <xref:System.ServiceModel.Dispatcher.ClientRuntime> objektu.  
  
- Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.Name%2A> vlastnost a získat tak název operace.  
  
- Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.SyncMethod%2A> vlastnost řídit, která metoda se mapuje na operaci.  
  
 Spuštění klienta WCF přesahují jen jedna operace, najdete v tématu vlastnosti, které jsou k dispozici na <xref:System.ServiceModel.Dispatcher.ClientOperation> třídy naleznete v tématu, zda úpravu vlastnosti nebo implementace rozhraní a jejich přidání do vlastnosti vytvoří funkci, která požadujete. Po výběru konkrétního rozšíření k sestavení, vložení rozšíření do příslušné <xref:System.ServiceModel.Dispatcher.ClientOperation> vlastnost implementací chování klienta, který poskytuje přístup k <xref:System.ServiceModel.Dispatcher.ClientOperation> třídy při vyvolání. Uvnitř tohoto chování poté můžete upravit <xref:System.ServiceModel.Dispatcher.ClientRuntime> vlastnosti podle svých požadavků.  
  
 Obvykle implementace na chování operace (objekt, který implementuje <xref:System.ServiceModel.Description.IOperationBehavior> rozhraní) přípony, ale můžete také použít chování koncového bodu a smlouvy chování dosahuje se toho tím provést totéž <xref:System.ServiceModel.Description.OperationDescription> pro konkrétní operace a připojení chování existuje. Podrobnosti najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Pokud chcete používat vaše vlastní chování z konfigurace, nainstalujte chování pomocí obslužné rutiny konfiguračního oddílu vlastní chování. Chování můžete také nainstalovat tak, že vytvoříte vlastní atribut.  
  
 Příklady, které ukazují zachycení napříč klienta WCF najdete v tématu [jak: Kontrola nebo úprava parametrů](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Dispatcher.ClientRuntime>
- <xref:System.ServiceModel.Dispatcher.ClientOperation>
- [Postupy: Kontrola a změny zpráv na straně klienta](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md)
- [Postupy: Kontrola nebo úprava parametrů](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
