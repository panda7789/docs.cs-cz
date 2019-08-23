---
title: Přístup ke službám pomocí klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
ms.openlocfilehash: 0923fa70907a4846924395483c86e541cd88f284
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964981"
---
# <a name="accessing-services-using-a-client"></a>Přístup ke službám pomocí klienta
Klientské aplikace musí ke komunikaci se službami vytvářet, konfigurovat a používat objekty klienta nebo kanály WCF. Téma [Přehled klienta WCF](../../../../docs/framework/wcf/wcf-client-overview.md) poskytuje přehled o objektech a krocích při vytváření základních objektů klienta a kanálu a jejich použití.  
  
 V tomto tématu najdete podrobné informace o některých problémech s klientskými aplikacemi a objekty klienta a kanálu, které mohou být užitečné v závislosti na vašem scénáři.  
  
## <a name="overview"></a>Přehled  
 Toto téma popisuje chování a problémy týkající se:  
  
- Doba života kanálu a relace.  
  
- Zpracování výjimek.  
  
- Principy blokujících problémů.  
  
- Interaktivní inicializace kanálů  
  
### <a name="channel-and-session-lifetimes"></a>Doba života kanálu a relace  
 Aplikace Windows Communication Foundation (WCF) obsahují dvě kategorie kanálů, datagramů a relací.  
  
 Kanál *datagram* je kanál, ve kterém jsou všechny zprávy nekorelační. V případě, že dojde k chybě vstupní nebo výstupní operace pomocí kanálu datagram, je obvykle neovlivněná další operace a stejný kanál lze znovu použít. Z tohoto důvodu kanály datagramů nejsou obvykle chybné.  
  
 Kanály s relacemi jsou však kanály s připojením k druhému koncovému bodu. Zprávy v relaci na jedné straně jsou vždy ve vztahu ke stejné relaci na druhé straně. Kromě toho musí oba účastníci v relaci souhlasit s tím, že požadavky na jejich konverzaci byly splněné, aby se relace považovala za úspěšnou. Pokud nemohou souhlasit, může dojít k chybě kanálu relace.  
  
 Explicitně nebo implicitně otevřete klienty voláním první operace.  
  
> [!NOTE]
> Pokus o explicitní detekci chybně generovaných kanálů není obvykle užitečný, protože když obdržíte oznámení, záleží na implementaci relace. Například vzhledem k tomu, <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> že se (s nespolehlivou relací zakáže) rozsvítí relaci připojení TCP, pokud naslouchajíte <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=nameWithType> události ve službě nebo klientovi, který bude pravděpodobně v případě selhání sítě rychlejší, obdržíte oznámení. Ale spolehlivé relace (vytvořené vazbami, ve kterých <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> je povolená), jsou navržené tak, aby nedošlo k izolaci služeb při malých selháních sítě. Pokud může být relace znovu navázána v rozumné době, stejné vazby, která je nakonfigurována pro spolehlivé relace, nemusí být chyba, dokud přerušení nebude trvat delší dobu.  
  
 Většina vazeb poskytovaných systémem (které zpřístupňují kanály pro aplikační vrstvu) používá ve výchozím nastavení relace, ale <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> ne. Další informace najdete v tématu [použití relací](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="the-proper-use-of-sessions"></a>Správné použití relací  
 Relace poskytují způsob, jak zjistit, zda je celý výměna zpráv dokončena, a zda obě strany považovat za úspěšné. Doporučuje se, aby volající aplikace otevřela kanál, používal ho a zavřeli kanál uvnitř jednoho testovaného bloku. Pokud je kanál relace otevřený a <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> metoda se volá jednou a volání se úspěšně vrátí, relace byla úspěšná. V tomto případě to znamená, že všechna doručení zaručují splnění zadané vazby a druhá strana před voláním <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ICommunicationObject.Close%2A>nevolala na kanál.  
  
 V následující části najdete příklad tohoto přístupu klienta.  
  
### <a name="handling-exceptions"></a>Zpracování výjimek  
 Zpracování výjimek v klientských aplikacích je jednoduché. Pokud je kanál otevřen, použit a uzavřen uvnitř bloku try, konverzace byla úspěšná, pokud není vyvolána výjimka. Obvykle Pokud je vyvolána výjimka, konverzace je přerušena.  
  
> [!NOTE]
> Použití příkazu (`Using` v Visual Basic) se nedoporučuje. `using` Důvodem je, že konec `using` příkazu může způsobit výjimky, které mohou maskovat jiné výjimky, o které může být nutné znát. Další informace najdete v tématu [použití funkcí zavřít a přerušit k vydání prostředků klienta WCF](../../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 Následující příklad kódu ukazuje doporučený vzor klienta pomocí bloku try/catch a nikoli `using` příkazu.  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
> Kontrola hodnoty <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=nameWithType> vlastnosti je podmínka časování a nedoporučuje se určit, jestli se má kanál znovu použít nebo zavřít.  
  
 V případě, že dojde k výjimkám při jejich zavření, kanály datagramů nikdy nechybí. Kromě toho neduplexní klienti, kteří se nedaří ověřit pomocí zabezpečené konverzace, obvykle vyvolají <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>. Pokud se však duplexní klient používající zabezpečenou konverzaci nedokáže ověřit, klient obdrží <xref:System.TimeoutException?displayProperty=nameWithType> místo toho.  
  
 Další informace o tom, jak pracovat s informacemi o chybě na úrovni aplikace, najdete v tématu [určení a zpracování chyb v kontraktech a službách](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). [Očekávané výjimky](../../../../docs/framework/wcf/samples/expected-exceptions.md) popisují očekávané výjimky a ukazují, jak je zpracovat. Další informace o tom, jak zpracovávat chyby při vývoji kanálů, najdete v tématu [zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
### <a name="client-blocking-and-performance"></a>Blokování a výkon klienta  
 Když aplikace synchronně volá operaci požadavek-odpověď, klient zablokuje, dokud není obdržena návratová hodnota, nebo je vyvolána výjimka (například <xref:System.TimeoutException?displayProperty=nameWithType>). Toto chování je podobné místnímu chování. Když aplikace synchronně vyvolá operaci na objektovém objektu nebo kanálu WCF, klient nevrátí, dokud vrstva kanálu nebude zapisovat data do sítě nebo dokud nebude vyvolána výjimka. A i když se jednosměrná vzorová výměna zpráv (určená označením operace s <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> nastavením na `true`) může určit, že někteří klienti budou reagovat, jednosměrné operace mohou také blokovat v závislosti na vazbě a tom, které zprávy již byly odeslané. Jednosměrné operace se týkají pouze výměny zpráv, ne více a méně. Další informace najdete v tématu [jednosměrné služby](../../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
 Velké objemy dat mohou zpomalit zpracování klienta bez ohledu na to, jaký je vzor výměny zpráv. Další informace o tom, jak tyto problémy zvládnout, najdete v tématu [velké objemy dat a streamování](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Pokud vaše aplikace musí provádět více práce, zatímco operace skončí, měli byste vytvořit dvojici asynchronních metod na rozhraní kontraktu služby, které implementuje klient služby WCF. Nejjednodušší způsob, jak to provést, je použít `/async` přepínač v nástroji pro nástroj pro [metadata ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Příklad naleznete v tématu [How to: Asynchronní volání operací služby](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Další informace o zvýšení výkonu klientů najdete v tématu [klientské aplikace střední vrstvy](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).  
  
### <a name="enabling-the-user-to-select-credentials-dynamically"></a>Povolení dynamického výběru přihlašovacích údajů uživatelem  
 <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> Rozhraní umožňuje aplikacím zobrazit uživatelské rozhraní, které uživateli umožňuje zvolit přihlašovací údaje, se kterými se vytvoří kanál, než se spustí časovač časových limitů.  
  
 Vývojáři aplikací mohou použít vložené <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> dva způsoby. Klientská aplikace může před otevřením <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> kanálu ( *explicitní* přístup) zavolat buď <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> nebo (nebo asynchronní), nebo zavolat první operaci ( *implicitní* přístup).  
  
 Při použití implicitního přístupu musí aplikace zavolat první operaci na <xref:System.ServiceModel.ClientBase%601> rozšíření nebo. <xref:System.ServiceModel.IClientChannel> Pokud volá cokoli jiného než první operace, je vyvolána výjimka.  
  
 Pokud používáte explicitní přístup, aplikace musí v uvedeném pořadí provést následující kroky:  
  
1. Zavolejte buď <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (nebo asynchronní verzi).  
  
2. Po vrácení <xref:System.ServiceModel.ICommunicationObject.Open%2A> inicializátorů volejte buď metodu <xref:System.ServiceModel.IClientChannel> objektu, nebo <xref:System.ServiceModel.IClientChannel> objektu vráceného z <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=nameWithType> vlastnosti.  
  
3. Operace volání.  
  
 Doporučujeme, aby aplikace s produkčním prostředím řídí proces uživatelského rozhraní tím, že budou přijímat explicitní přístup.  
  
 Aplikace, které používají implicitní přístup, vyvolávají Inicializátory uživatelského rozhraní, ale pokud uživatel aplikace nemůže odpovědět v časovém limitu odeslání vazby, je vyvolána výjimka, když se uživatelské rozhraní vrátí.  
  
## <a name="see-also"></a>Viz také:

- [Duplexní služby](../../../../docs/framework/wcf/feature-details/duplex-services.md)
- [Postupy: Přístup ke službám pomocí jednosměrných kontraktů a kontraktů požadavek-odpověď](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Postupy: Přístup ke službám pomocí duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Postupy: Přístup ke službě WSE 3,0](../../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Postupy: Použití třídy ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
- [Postupy: Asynchronní volání operací služby](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [Klientské aplikace střední vrstvy](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)
