---
title: Přístup ke službám pomocí klienta
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2138a412af30812b4ff443963604dda52eafea11
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="accessing-services-using-a-client"></a>Přístup ke službám pomocí klienta
Klientské aplikace musí vytvářet, konfigurovat a používat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta nebo kanál objektů komunikovat se službami. [Klienta WCF – přehled](../../../../docs/framework/wcf/wcf-client-overview.md) téma obsahuje přehled objektů a kroky při vytváření základní klienta a kanál objektů a jejich používání.  
  
 Toto téma obsahuje podrobné informace o některých problémech, s klientem aplikace a klienta a kanál objekty, které mohou být užitečné, v závislosti na vašem scénáři.  
  
## <a name="overview"></a>Přehled  
 Toto téma popisuje chování a otázky týkající se:  
  
-   Kanál a relace životnosti.  
  
-   Zpracování výjimek.  
  
-   Principy blokující problémy.  
  
-   Inicializace kanály interaktivně.  
  
### <a name="channel-and-session-lifetimes"></a>Kanál a trvání relace  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace zahrnuje dvě kategorie kanály, datagram a sessionful.  
  
 A *datagram* kanál je kanál, ve kterém jsou bez korelace nejsou všechny zprávy. S datagram kanál Pokud vstupních nebo výstupních operací nezdaří, je obvykle neovlivní další operace, a lze opětovně použít stejný kanál. Z toho důvodu datagram kanály obvykle není poruch.  
  
 *Sessionful* kanály, ale jsou kanály s připojením k jiný koncový bod. Zprávy v relaci na jedné straně jsou vždy korelační s stejné relace na druhé straně. Kromě toho jak účastníky v relaci musí souhlasit, jejich konverzace byly splnění požadavků pro danou relaci do považovat za úspěšné. Pokud nelze souhlasí, dojít k chybě kanálu relací.  
  
 Otevřete klienti explicitně nebo implicitně voláním první operaci.  
  
> [!NOTE]
>  Pokusu explicitně zjistit chybný relacemi kanály není obvykle užitečné, protože když jsou upozorněni závisí na implementaci relace. Například protože <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> (s spolehlivé relace zakázán) poskytuje relace připojení TCP, pokud naslouchání na <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=nameWithType> událostí na službu nebo klienta, budete pravděpodobně rychle upozorněni v případě selhání sítě. Ale spolehlivé relace (vymezenému vazby, ve kterém <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> je povoleno) jsou navrženy pro izolovat služby selhání malou síť. Pokud relace můžete je znovu vytvořit v přiměřené době běhu stejnou vazbu – nakonfigurovaný pro spolehlivé relace – nemusí poruch dokud narušení chodu dál pro delší časové období.  
  
 Většina vazby poskytované systémem, (které vystavit kanály na aplikační vrstvu) používá relace ve výchozím nastavení, ale <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> neexistuje. Další informace najdete v tématu [pomocí relace](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="the-proper-use-of-sessions"></a>Správné použití relací  
 Relace poskytují způsob, jak vědět, pokud skončí exchange celou zprávu, a pokud na obou stranách považuje za úspěšnou. Doporučujeme volající aplikace otevřete kanál, použijte ji a zavřete kanál uvnitř bloku try jeden. Pokud kanál relace je otevřené a <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> metoda je volána jednou a že volání vrátí úspěšně a pak relace byla úspěšná. Úspěšné v tomto případě znamená, že všechny doručení zaručuje určená vazba byly splněny, a druhá strana nezavolalo <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=nameWithType> na kanálu před voláním <xref:System.ServiceModel.ICommunicationObject.Close%2A>.  
  
 Následující část obsahuje příklady tohoto přístupu klienta.  
  
### <a name="handling-exceptions"></a>Zpracování výjimek  
 Zpracování výjimek v klientských aplikacích je jednoduchá. Pokud kanál, který je otevřené, používat a uzavřen uvnitř bloku try, pak konverzace proběhla úspěšně, pokud je vyvolána výjimka. Obvykle Pokud je vyvolána výjimka konverzace byl přerušen.  
  
> [!NOTE]
>  Použití `using` – příkaz (`Using` v jazyce Visual Basic) se nedoporučuje. Důvodem je, že konci `using` příkaz může způsobit výjimky, které můžete maskování dalších výjimkách, budete muset vědět o. Další informace najdete v tématu [vyhnout problémům s příkazem Using](../../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 Následující příklad kódu ukazuje vzoru klienta doporučenou pomocí bloku try/catch a ne `using` příkaz.  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
>  Kontrola hodnotu <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=nameWithType> vlastnost je spor a nedoporučuje se používat k určení, jestli se má použít nebo zavřete kanál.  
  
 Kanály datagram nikdy poruch i v případě výjimky dojít, když jsou uzavřeny. Kromě toho-duplexní režim klientů, které se nepodařilo ověřit pomocí zabezpečenou konverzaci obvykle throw <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>. Ale pokud se ověření nezdaří duplexní klienta pomocí zabezpečenou konverzaci, klient přijme <xref:System.TimeoutException?displayProperty=nameWithType> místo.  
  
 Podrobnější informace o práci s informace o chybě na úrovni aplikace, najdete v části [zadání a zpracování chyb v kontraktech a službách](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). [Očekávané výjimky](../../../../docs/framework/wcf/samples/expected-exceptions.md) popisuje očekávané výjimky a ukazuje, jak k jejich zpracování. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] zpracování chyb při vývoji kanály najdete v tématu [zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
### <a name="client-blocking-and-performance"></a>Blokování klienta a výkonu  
 Když aplikace synchronně volá operaci požadavku a odpovědi, klientské bloky, dokud není přijata návratovou hodnotu nebo výjimku (například <xref:System.TimeoutException?displayProperty=nameWithType>) je vyvolána výjimka. Toto chování je podobné místní chování. Když aplikace synchronně vyvolá operace na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objekt klienta nebo kanálu klienta nevrací dokud vrstvy kanálu můžete zapsat data do sítě, nebo dokud je vyvolána výjimka. A při vzorce výměny zpráv jednosměrný (Zadaná operace s označením <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> nastavena na `true`) můžete provést některé klienty rychlejšího, Jednosměrná operace můžete taky zablokovat, v závislosti na vazby a co zprávy již byly Odeslat. Jednosměrná operace jsou pouze o zpráva systému exchange, ne další a ne menší. Další informace najdete v tématu [One-Way služby](../../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
 Bloky velkých objemů dat může zpomalit zpracování bez ohledu na to, co vzorce výměny zpráv na straně klienta. Chcete-li pochopit, jak zpracovávat tyto problémy, přečtěte si téma [velkého množství dat a Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Pokud vaše aplikace musí provést další práci při dokončení operace, měli byste vytvořit dvojici asynchronní metody na rozhraní kontraktu služby, vaše [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementuje klienta. Nejjednodušším způsobem je použití `/async` přepínač na [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Příklad, naleznete v části [postupy: asynchronní volání operací služby](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] zvýšení výkonu klienta, najdete v části [klientské aplikace střední vrstvy](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).  
  
### <a name="enabling-the-user-to-select-credentials-dynamically"></a>Povolení uživatelům dynamicky vyberte přihlašovací údaje  
 <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> Rozhraní umožňuje aplikacím, které chcete zobrazit uživatelské rozhraní, které umožňuje uživatelům vyberte přihlašovací údaje, pomocí kterých se vytvoří kanál před časovače časový limit spuštění.  
  
 Vývojáři aplikací můžete provést použití vložené <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> dvěma způsoby. Klientská aplikace můžete volat buď <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (nebo asynchronní verze) před otevření kanálu ( *explicitní* přístup), nebo volejte první operace ( *implicitní*přístup).  
  
 Pokud používáte implicitní přístup, aplikace musí volat první operaci na <xref:System.ServiceModel.ClientBase%601> nebo <xref:System.ServiceModel.IClientChannel> rozšíření. Pokud volá jakoukoli jinou hodnotu než první operace, je vyvolána výjimka.  
  
 Pokud používáte explicitní přístup, musí aplikace proveďte následující kroky v pořadí:  
  
1.  Volání buď <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (nebo asynchronní verzi).  
  
2.  Pokud máte vrátí inicializátory, volání buď <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu <xref:System.ServiceModel.IClientChannel> objektu nebo na <xref:System.ServiceModel.IClientChannel> objekt vrácený <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=nameWithType> vlastnost.  
  
3.  Volání operací.  
  
 Doporučuje se, že kvalitních aplikací řídit proces uživatelského rozhraní přijetí explicitní přístup.  
  
 Aplikace, které používají implicitní přístup vyvolání inicializátory uživatelského rozhraní, ale pokud uživatel aplikace přestane reagovat během časového limitu odesílání vazby, je vyvolána výjimka, když se vrátí uživatelské rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Duplexní služby](../../../../docs/framework/wcf/feature-details/duplex-services.md)  
 [Postupy: Přístup ke službám pomocí jednosměrných kontraktů a kontraktů žádost-odpověď](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)  
 [Postupy: Přístup ke službám pomocí duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [Postupy: Přístup ke službě WSE 3.0](../../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)  
 [Postupy: Použití objektu pro vytváření kanálů](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)  
 [Postupy: Asynchronní volání operací služby](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)  
 [Klientské aplikace střední vrstvy](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)
