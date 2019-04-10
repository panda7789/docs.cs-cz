---
title: Přístup ke službám pomocí klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
ms.openlocfilehash: a94864563491b5bd2d50a6df59858f4b7235fd75
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314877"
---
# <a name="accessing-services-using-a-client"></a>Přístup ke službám pomocí klienta
Klientské aplikace musíte vytvořit, konfigurovat a komunikace se službami pomocí WCF klienta nebo kanál objektů. [Přehled klientů WCF](../../../../docs/framework/wcf/wcf-client-overview.md) téma obsahuje přehled objektů a kroky při vytváření základních klienta a kanál objektů a jejich používání.  
  
 Toto téma obsahuje podrobné informace o některých problémů s klientem aplikace a klienta a kanál objekty, které mohou být užitečné, v závislosti na vašem scénáři.  
  
## <a name="overview"></a>Přehled  
 Toto téma popisuje chování a problémů souvisejících se službou:  
  
-   Kanál a relace životnosti.  
  
-   Zpracování výjimek.  
  
-   Principy blokující problémy.  
  
-   Inicializace kanály interaktivně.  
  
### <a name="channel-and-session-lifetimes"></a>Kanál a doby trvání relace  
 Aplikace Windows Communication Foundation (WCF) obsahuje dvě kategorie kanály datagramu, který neobsahuje relace.  
  
 A *datagram* kanálu je kanál, ve kterém jsou bez korelace nejsou všechny zprávy. Pomocí kanálu datagramu, pokud vstupní nebo výstupní operace se nezdaří, další operaci je obvykle to neovlivní a jeden kanál je možné využít znovu. Z tohoto důvodu datagram kanály obvykle není chyb.  
  
 *Který neobsahuje relace* kanály, ale jsou kanály s připojením k jiný koncový bod. Zprávy v relaci na jedné straně se vždy korelují s stejné relace na druhé straně. Kromě toho obou účastníků v relaci musí souhlasit, že byly splněny požadavky jejich konverzace pro danou relaci do považovat za úspěšné. Pokud nelze souhlasí, kanál s relacemi dojít k chybě.  
  
 Otevření klienti explicitně nebo implicitně voláním první operace.  
  
> [!NOTE]
>  Pokusu explicitně zjišťovat chybnou duplexních kanálů s relacemi není obvykle vhodné, protože když se zobrazí oznámení, závisí na implementaci relace. Například protože <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> (s ve stabilní relaci zakázané) poskytuje relace připojení TCP, pokud budete naslouchat <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=nameWithType> událostí na službu nebo klienta, budete pravděpodobně být rychle informovat v případě selhání sítě. Ale spolehlivé relace (stanovené vazby, ve kterém <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> je povoleno) jsou určeny k izolovat služby z malých síťových chyb. Pokud relace můžete je znovu vytvořit v rozumné časovém období, stejnou vazbu – nakonfigurovaný pro spolehlivé relace – nemusí selhání, dokud přerušení pokračuje po delší dobu.  
  
 Většina vazeb poskytovaných systémem, (které zpřístupňují kanály pro aplikační vrstvu) používá relace ve výchozím nastavení, ale <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> tak není. Další informace najdete v tématu [s využitím relací](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="the-proper-use-of-sessions"></a>Správné použití relací  
 Relací zadejte způsob, jak zjistit, pokud celé zprávy exchange je dokončena a obě strany považovat za úspěšné. Je doporučeno volající aplikace otevřít kanál, používat a zavřete kanál uvnitř bloku jeden pokus. Pokud kanál relace je otevřený a <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> metoda se volá jednou a toto volání vrátí úspěšně, a relace byla úspěšná. Úspěšné v tomto případě znamená, že všechny doručování zaručuje Zadaná vazba nebyly splněny a druhá strana nezavolalo <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=nameWithType> na kanálu před voláním <xref:System.ServiceModel.ICommunicationObject.Close%2A>.  
  
 Následující část poskytuje příklad tohoto přístupu klienta.  
  
### <a name="handling-exceptions"></a>Zpracování výjimek  
 Zpracování výjimek v klientských aplikacích je jednoduché. Pokud kanál se otevřel, používat a uzavřel uvnitř bloku try, pak konverzace proběhla úspěšně, pokud je vyvolána výjimka. Obvykle Pokud je vyvolána výjimka konverzace byl přerušen.  
  
> [!NOTE]
>  Použití `using` – příkaz (`Using` v jazyce Visual Basic) se nedoporučuje. Důvodem je, že na konec `using` příkaz může způsobit výjimky, které může zastínit ostatní výjimky, budete muset znát. Další informace najdete v tématu [použití zavřít a Abort k uvolnění prostředků klienta WCF](../../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 Následující příklad kódu ukazuje doporučený klient modelu s použitím bloku try/catch, ne `using` příkazu.  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
>  Kontrolou hodnoty <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=nameWithType> vlastnost je časování a nedoporučuje se používat k určení, jestli se má opakovaně používat nebo zavření kanálu.  
  
 Kanály datagram nikdy selhání i v případě, že výjimkám dochází, když jsou uzavřeny. Kromě toho vyvolat neduplexní klienty, kteří neumožňuje ověřovat, obvykle pomocí zabezpečené konverzace <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>. Ale pokud se ověření nezdaří duplexní klienta pomocí zabezpečené konverzace, klient přijme <xref:System.TimeoutException?displayProperty=nameWithType> místo.  
  
 Podrobnější informace o práci s informacemi o chybě na úrovni aplikace, najdete v části [zadání a zpracování chyb v kontraktech a službách](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). [Očekávané výjimky](../../../../docs/framework/wcf/samples/expected-exceptions.md) popisuje očekávané výjimky a ukazuje způsob jejich zpracování. Další informace o tom, jak řešit chyby při vývoj kanálů najdete v tématu [zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
### <a name="client-blocking-and-performance"></a>Blokování klienta a výkonu  
 Když aplikaci synchronně volá operace požadavek odpověď, bloky klienta, dokud neobdrží návratovou hodnotu nebo výjimku (například <xref:System.TimeoutException?displayProperty=nameWithType>) je vyvolána výjimka. Toto chování je podobné místní chování. Když aplikaci synchronně vyvolá operaci objektu klienta WCF nebo kanálu, klient nevrací dokud vrstvy kanálu můžete zapisovat data do sítě nebo dokud je vyvolána výjimka. A při vzoru výměny zpráv jednosměrné (Zadaná operace s označením <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> nastavena na `true`) může být někteří klienti odezvu, jednosměrné operace, můžete taky zablokovat, v závislosti na vazby a co zprávy již byly odeslání. Jednosměrná operace jsou jen o výměně zpráv, častěji a méně. Další informace najdete v tématu [One-Way služby](../../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
 Bloky dat velkých objemů dat může zpomalit zpracování bez ohledu na to, co vzorce výměny zpráv na straně klienta. Pokud chcete pochopit, jak zpracovat tyto problémy, přečtěte si téma [velkých objemů dat a datových proudů](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Pokud vaše aplikace musí provést další práce při dokončení operace, měli byste vytvořit páru asynchronní metody na rozhraní servisní smlouvy, která implementuje klienta WCF. Nejjednodušší způsob je použít `/async` zapnout [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Příklad najdete v tématu [jak: Asynchronní volání operací služby](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Další informace o zvyšování výkonu klienta najdete v tématu [klientské aplikace střední vrstvy](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).  
  
### <a name="enabling-the-user-to-select-credentials-dynamically"></a>Umožňuje uživateli vybrat dynamicky přihlašovacích údajů  
 <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> Rozhraní umožňuje aplikacím zobrazují uživatelské rozhraní, která umožňuje uživateli zvolit přihlašovací údaje, se kterými se vytvoří kanál před zahájením časovače časový limit.  
  
 Vývojáři aplikací mohli používat z vložené <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> dvěma způsoby. Klientská aplikace může volat <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (nebo asynchronní verze) před otevření kanálu ( *explicitní* přístup) nebo volání první operace ( *implicitní*přístup).  
  
 Pokud používáte implicitní přístup, aplikace musí volat první operace na <xref:System.ServiceModel.ClientBase%601> nebo <xref:System.ServiceModel.IClientChannel> rozšíření. Volá-li to nic jiného než první operace, je vyvolána výjimka.  
  
 Při použití explicitní přístup, musí aplikace provádět následující kroky v pořadí:  
  
1. Volání na buď <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (nebo asynchronní verze).  
  
2. Když inicializátorech vrátily, zavolejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu na <xref:System.ServiceModel.IClientChannel> objekt nebo na <xref:System.ServiceModel.IClientChannel> objekt vrácený z <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=nameWithType> vlastnost.  
  
3. Volání operací.  
  
 Doporučuje se, že aplikace produkční kvality řízení procesu uživatelského rozhraní přijetím explicitní přístup.  
  
 Aplikace, které používají implicitní přístup vyvolat inicializátory uživatelského rozhraní, ale pokud uživatel aplikace přestane reagovat v časovém limitu odesílání vazby, dojde k výjimce při návratu uživatelského rozhraní.  
  
## <a name="see-also"></a>Viz také:

- [Duplexní služby](../../../../docs/framework/wcf/feature-details/duplex-services.md)
- [Postupy: Přístup ke službám pomocí jednosměrných kontraktů a kontraktů požadavek-odpověď](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Postupy: Přístup ke službám pomocí duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Postupy: Přístup ke službě WSE 3.0](../../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Postupy: Používání ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
- [Postupy: Asynchronní volání operací služby](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [Klientské aplikace střední vrstvy](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)
