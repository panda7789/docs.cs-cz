---
title: "Rozšíření klientů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: proxy extensions [WCF]
ms.assetid: 1328c61c-06e5-455f-9ebd-ceefb59d3867
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2444488418b7647111cf4b89db0c41a8e66470d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="extending-clients"></a>Rozšíření klientů
V volající aplikace je zodpovědná za překladu volání metod v kódu aplikace do odchozí zprávy, když zavedete je základní kanály, překladu výsledky zpět do návratové hodnoty a výstupní parametry v vrstva modelu služby kód aplikace a vrací výsledky zpět na volajícího. Rozšíření modelů služby upravit nebo jsou implementovány provádění nebo komunikace chování a funkce zahrnující klienta nebo dispečera funkce, vlastní chování, zprávu a parametr zachycení a další funkce rozšiřitelnost.  
  
 Toto téma popisuje postup použití <xref:System.ServiceModel.Dispatcher.ClientRuntime> a <xref:System.ServiceModel.Dispatcher.ClientOperation> třídy v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klientská aplikace změnit výchozí chování při spuštění systému [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta nebo k zachycení nebo upravit zprávy, parametry nebo návratové hodnoty před nebo Po odeslání nebo načítat vrstvy kanálu. Další informace o rozšíření modulu runtime service najdete v tématu [rozšíření dispečerů](../../../../docs/framework/wcf/extending/extending-dispatchers.md). Další informace o chování, které upravit a vložit přizpůsobení objektů do modulu runtime klienta najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="clients"></a>Klienti  
 V klientovi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objekt klienta nebo kanálem klienta převede volání metod zprávy odchozí a příchozí zprávy a pokuste se výsledky operace, které jsou vráceny do volající aplikace. (Další informace o typech klienta najdete v tématu [Architektura klienta WCF](../../../../docs/framework/wcf/feature-details/client-architecture.md).)  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]typů klientů mají runtime typy, které tuto funkci na úrovni koncového bodu a operace zpracování. Pokud aplikace zavolá operace, <xref:System.ServiceModel.Dispatcher.ClientOperation> překládá odchozí objekty do zprávy, zpracuje sběrače, potvrdí, že je v souladu se smlouvou cíl odchozí volání a předá odchozí zprávu, která se <xref:System.ServiceModel.Dispatcher.ClientRuntime>, což je zodpovědný za vytváření a správy odchozí kanály (a příchozí kanály v případě duplexní služby), zpracování velmi odchozí zprávy zpracování (například změna záhlaví), zpracování zpráv sběrače v obou směrech a směrování příchozí duplexní volání příslušné na straně klienta <xref:System.ServiceModel.Dispatcher.DispatchRuntime> objektu. Jak <xref:System.ServiceModel.Dispatcher.ClientOperation> a <xref:System.ServiceModel.Dispatcher.ClientRuntime> poskytují podobné služby, když jsou zprávy (včetně chyb) vrácen do klienta.  
  
 Tyto dvě třídy runtime jsou hlavní rozšíření přizpůsobit zpracování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objekty klienta a kanály. <xref:System.ServiceModel.Dispatcher.ClientRuntime> Třída umožňuje uživatelům zachytávat a rozšířit spuštění klienta mezi všechny zprávy ve smlouvě. <xref:System.ServiceModel.Dispatcher.ClientOperation> Třída umožňuje uživatelům zachytávat a rozšířit spuštění klienta pro všechny zprávy ve danou operaci.  
  
 Úprava vlastností nebo vkládání přizpůsobení provádí pomocí kontrakt, koncový bod a chování operaci. Další informace o tom, jak používat tyto typy chování vlastního nastavení klienta modulu runtime najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="scenarios"></a>Scénáře  
 Zde několik důvodů, proč rozšířit klientského systému, včetně:  
  
-   Vlastní zprávy ověření. Uživatel může chtít vynutit, že je platný pro určité schéma zprávu. To lze provést implementací <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> rozhraní a přiřazení k implementaci <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A> vlastnost. Příklady najdete v tématu [postup: zkontrolovat nebo upravit zprávy v klientovi](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md) a [postup: zkontrolovat nebo upravit zprávy v klientovi](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
-   Vlastní zprávu při protokolování. Uživatel může chtít kontrolovat a protokolu některé sadu zpráv aplikace, které procházet skrz koncový bod. To můžete provést také s rozhraními interceptoru zprávy.  
  
-   Vlastní zprávu transformace. Místo změny kódu aplikace, uživatel může chtít použít určité transformace na zprávu v modulu runtime (například pro správu verzí). Můžete to provést, znovu s rozhraními interceptoru zprávy.  
  
-   Vlastní datový Model. Uživatel může chtít, aby data nebo serializace modelu nejsou podporovány ve výchozím nastavení v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (konkrétně, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>, a <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> objektů). Tento krok můžete provést implementací rozhraní formátování zprávy. Další informace najdete v tématu <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType> a <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A?displayProperty=nameWithType> vlastnost.  
  
-   Vlastní parametr ověření. Uživatel může chtít vynutit, aby typové parametry jsou platné (na rozdíl od XML). To lze provést pomocí rozhraní inspector parametr. Příklad, naleznete v části [postupy: Kontrola nebo úprava parametrů](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md) nebo [ověření klienta](../../../../docs/framework/wcf/samples/client-validation.md).  
  
### <a name="using-the-clientruntime-class"></a>Používání třídy ClientRuntime  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime> Třída je bod rozšiřitelnosti na které můžete přidat objekty rozšíření, které zachytí zprávy a rozšířit chování klienta. Zachycení můžete zpracovávat všechny zprávy ve kontraktu konkrétní zpracovat pouze zprávy pro konkrétní operace, provést inicializaci vlastní kanál, objektů a implementovat jiné chování vlastní klientské aplikace.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> Vlastnost vrací objekt run-time odesílání pro klienty služby spouštěná zpětného volání.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.OperationSelector%2A> Tato vlastnost přijímá parametry objekt selektor vlastní operace.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ChannelInitializers%2A> Vlastnost umožňuje přidání inicializátoru kanál, který můžete zkontrolovat nebo upravit kanálem klienta.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> Vlastnost získá kolekci <xref:System.ServiceModel.Dispatcher.ClientOperation> objekty, na které můžete přidat vlastní zprávu sběrače, které poskytují funkce specifické pro zprávy této operace.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ManualAddressing%2A> Vlastnost umožňuje vypnout některé automatické adresování hlavičky přímo řídit adresování aplikaci.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.Via%2A> Vlastnost nastaví hodnotu cíl zprávy na úrovni přenosu pro podporu prostředníci a jiné scénáře.  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> Vlastnost získá kolekci <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> objekty, na které můžete přidat vlastní zprávu sběrače pro všechny zprávy cestě prostřednictvím [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta.  
  
 Kromě toho existuje několik dalších vlastností, které načíst informace o smlouvě:  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractName%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractNamespace%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractClientType%2A>  
  
 Pokud [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] duplexní režim je klient [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta tyto vlastnosti také načíst zpětné volání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] informace o klientech:  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackClientType%2A>  
  
-   <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>  
  
 Rozšíření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spuštění klienta napříč celou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, zkontrolujte vlastnosti, které jsou dostupné na <xref:System.ServiceModel.Dispatcher.ClientRuntime> třída zobrazíte zda úpravu vlastnosti nebo implementace rozhraní a její přidání do vlastnost vytvoří funkci hledáte. Jakmile jste vybrali konkrétní rozšíření k vytvoření, vložit rozšíření do příslušné <xref:System.ServiceModel.Dispatcher.ClientRuntime> vlastnost implementací chování klienta, který poskytuje přístup k <xref:System.ServiceModel.Dispatcher.ClientRuntime> třídy při vyvolání.  
  
 Vlastní rozšíření objektů můžete vložit do kolekce pomocí operaci chování (objekt, který implementuje <xref:System.ServiceModel.Description.IOperationBehavior>), kontrakt chování (objekt, který implementuje <xref:System.ServiceModel.Description.IContractBehavior>), nebo chování koncového bodu (objekt, který implementuje <xref:System.ServiceModel.Description.IEndpointBehavior> ). Objekt instalaci chování je přidán do příslušné kolekce chování prostřednictvím kódu programu, deklarativně (implementace vlastních atributů), nebo implementací vlastní <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> objekt, který chcete povolit chování má být vložen pomocí konfigurační soubor aplikace. Podrobnosti najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Příklady, které ukazují zachycení napříč [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, najdete v části [postup: zkontrolovat nebo upravit zprávy v klientovi](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md).  
  
### <a name="using-the-clientoperation-class"></a>Používání třídy ClientOperation  
 <xref:System.ServiceModel.Dispatcher.ClientOperation> Třída je umístění pro úpravy spuštění klienta a vložení bodu pro vlastní rozšíření, která jsou omezená na operaci pouze jedna služba. (Chcete-li upravit běhového chování klienta pro všechny zprávy ve smlouvě, použijte <xref:System.ServiceModel.Dispatcher.ClientRuntime> třídy.)  
  
 Použití <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> vlastnost najít <xref:System.ServiceModel.Dispatcher.ClientOperation> objekt, který reprezentuje operaci konkrétní služby. Tyto vlastnosti umožňují vložit vlastní objekty do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] systému klienta:  
  
-   Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> vlastnost vložit vlastní <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementaci pro operace nebo změnit aktuální formátování.  
  
-   Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A> vlastnost vložit vlastní <xref:System.ServiceModel.Dispatcher.IParameterInspector> implementace nebo změnit aktuální.  
  
 Tyto vlastnosti umožňují upravit systému v interakci s formátovacího modulu a vlastní parametr kontroly:  
  
-   Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.SerializeRequest%2A> vlastnost k řízení serializace odchozí zprávy.  
  
-   Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.DeserializeReply%2A> vlastnost k řízení deserializace příchozí zprávy.  
  
-   Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.Action%2A> vlastnost řídit akce WS-Addressing zprávy požadavku.  
  
-   Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.BeginMethod%2A> a <xref:System.ServiceModel.Dispatcher.ClientOperation.EndMethod%2A> k určete, které [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metody klienta jsou přidruženy asynchronní operace.  
  
-   Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.FaultContractInfos%2A> vlastnost k získání kolekce, která obsahuje typy, které se mohou objevit v protokolu SOAP chyb jako typ podrobností.  
  
-   Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.IsInitiating%2A> a <xref:System.ServiceModel.Dispatcher.ClientOperation.IsTerminating%2A> vlastnosti k řízení, zda je relace je zahájeno nebo odpojí dolů při volání operace.  
  
-   Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.IsOneWay%2A> vlastnost řídit, jestli tuto operaci je jednosměrná operace.  
  
-   Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.Parent%2A> vlastnost k získání obsahující <xref:System.ServiceModel.Dispatcher.ClientRuntime> objektu.  
  
-   Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.Name%2A> vlastnost k získání názvu operace.  
  
-   Použití <xref:System.ServiceModel.Dispatcher.ClientOperation.SyncMethod%2A> vlastnost řídit, která metoda je namapována na operaci.  
  
 Rozšíření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spuštění klienta napříč pouze jedna služba operace, zkontrolujte vlastnosti, které jsou dostupné na <xref:System.ServiceModel.Dispatcher.ClientOperation> třída zobrazíte zda úpravu vlastnosti nebo implementace rozhraní a její přidání do vlastnost vytvoří funkci jste vyhledávání. Jakmile jste vybrali konkrétní rozšíření k vytvoření, vložit rozšíření do příslušné <xref:System.ServiceModel.Dispatcher.ClientOperation> vlastnost implementací chování klienta, který poskytuje přístup k <xref:System.ServiceModel.Dispatcher.ClientOperation> třídy při vyvolání. Uvnitř tohoto chování poté můžete upravit <xref:System.ServiceModel.Dispatcher.ClientRuntime> vlastnost podle svých požadavků.  
  
 Obvykle implementace operaci chování (objekt, který implementuje <xref:System.ServiceModel.Description.IOperationBehavior> rozhraní) přípony, ale můžete také použít chování koncový bod a smlouvy chování na totéž provést tím, že <xref:System.ServiceModel.Description.OperationDescription> pro konkrétní operace a připojení chování existuje. Podrobnosti najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Abyste mohli používat vaše vlastní chování z konfigurace, nainstalujte chování vaší pomocí obslužnou rutinu oddílu konfigurace vlastního chování. Můžete také nainstalovat chování vaší tak, že vytvoříte vlastní atribut.  
  
 Příklady, které ukazují zachycení napříč [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, najdete v části [postupy: Kontrola nebo upravte parametry](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime>  
 <xref:System.ServiceModel.Dispatcher.ClientOperation>  
 [Postupy: Kontrola a změny zpráv v klientovi](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md)  
 [Postupy: Kontrola nebo úprava parametrů](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
