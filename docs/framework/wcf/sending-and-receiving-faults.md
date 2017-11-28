---
title: "Chyby odesílání a přijímání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b7a97ef253431b5519de2b3e45485a15ca3f5ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sending-and-receiving-faults"></a>Chyby odesílání a přijímání
Chyb SOAP popisným podmínku ze služby pro klienta a v případě duplexní z klienta ke službě umožňuje vzájemnou spolupráci způsobem. Obvykle služby definuje vlastní chyby obsahu a určuje, které operace vrátit. (Další informace najdete v tématu [definiční a určení chyb](../../../docs/framework/wcf/defining-and-specifying-faults.md).) Toto téma popisuje, jak služba nebo duplexní klienta může poslat tyto chyby při odpovídající chybový stav a jak klienta nebo aplikace služby zpracovává tyto chyby. Přehled zpracování chyb v [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikace, najdete v části [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="sending-soap-faults"></a>Odesílání chyb SOAP  
 Deklarovaný chyb SOAP jsou ty, ve kterých se operace <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> určující vlastního typu chybu protokolu SOAP. Nedeklarovaný chyb SOAP jsou ty, které nejsou uvedené ve smlouvě operace.  
  
### <a name="sending-declared-faults"></a>Odesílání deklarované chyb  
 Pokud chcete odeslat deklarované chybu protokolu SOAP, zjistit chybový stav, pro které je vhodné chybu protokolu SOAP a throw novou <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> kde parametr typu je vytvoření nového objektu s typem zadaným v <xref:System.ServiceModel.FaultContractAttribute> pro tuto operaci. Následující příklad kódu ukazuje použití <xref:System.ServiceModel.FaultContractAttribute> určíte, že `SampleMethod` operace může vrátit chybu protokolu SOAP s typem podrobností `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
 [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
 Pro vyjádření `GreetingFault` informace o chybě klient zachytit příslušné chybový stav a vyvolat novou <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> typu `GreetingFault` s novou `GreetingFault` objektu jako argument, jako v následujícím příkladu kódu. Pokud je klient [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klientská aplikace ho vyskytne to jako spravované výjimky, kde je typ <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> typu `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
 [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
### <a name="sending-undeclared-faults"></a>Odesílání chyb nebyla deklarována  
 Odesílání nedeklarované chyb může být velmi užitečná rychle diagnostikovat a ladit problémy v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace, ale jeho použití jako ladicí nástroj je omezená. Obecně platí, když ho ladění je doporučeno používat <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> vlastnost. Když tuto hodnotu nastavíte na hodnotu true, klienti prostředí takové chyby jako <xref:System.ServiceModel.FaultException%601> výjimky typu <xref:System.ServiceModel.ExceptionDetail>.  
  
> [!IMPORTANT]
>  Protože spravované výjimky mohou být informace o interní aplikace, nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> k `true` můžete povolit [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klientům získat informace o operaci výjimky interní služby, včetně osobní osobní a dalších citlivých informací.  
>   
>  Proto nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> k `true` doporučujeme použít pouze jako způsob dočasně ladění aplikace služby. Kromě toho schématu WSDL pro metodu, která vrátí neošetřené se spravovanými výjimkami tímto způsobem neobsahuje kontrakt <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klienti měli očekávat možnost neznámé chybě protokolu SOAP (vrátí [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klientů jako <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objekty) získat informace o ladění správně.  
  
 Pokud chcete odeslat nedeklarované chybu protokolu SOAP, throw <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objektu (tedy ne obecný typ <xref:System.ServiceModel.FaultException%601>) a předejte řetězec do konstruktoru. To je vystaven [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klientské aplikace jako vyvolané <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> výjimky, kde řetězec je k dispozici při volání <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> metoda.  
  
> [!NOTE]
>  Pokud deklarace chybu protokolu SOAP typu řetězec a poté to vyvolat ve službě jako <xref:System.ServiceModel.FaultException%601> kde parametr typu je <xref:System.String?displayProperty=nameWithType> je přiřazena hodnota řetězce <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> vlastnost a není k dispozici z <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType>.  
  
## <a name="handling-faults"></a>Zpracování chyb  
 V [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klientů protokolu SOAP chyb, ke kterým došlo během komunikace, které jsou důležité pro klientské aplikace jsou vyvolány jako spravované výjimky. Existuje mnoho výjimky, které se můžou vyskytnout během provádění žádné program aplikací pomocí [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] očekávat klienta programovací model zpracování výjimek následující dva typy v důsledku komunikace.  
  
-   <xref:System.TimeoutException>  
  
-   <xref:System.ServiceModel.CommunicationException>  
  
 <xref:System.TimeoutException>objekty jsou vyvolány, když překročí zadaný časový limit operace.  
  
 <xref:System.ServiceModel.CommunicationException>objekty jsou vyvolány po nějaké chyby použitelná pro obnovení komunikace na službu nebo klienta.  
  
 <xref:System.ServiceModel.CommunicationException> Třída má dva důležité odvozené typy <xref:System.ServiceModel.FaultException> a Obecné <xref:System.ServiceModel.FaultException%601> typu.  
  
 <xref:System.ServiceModel.FaultException>jsou výjimky vyvolány, když naslouchací proces obdrží chybu, která není očekávané nebo uvedených ve smlouvě operace; obvykle proběhne, když je laděné aplikace a služby má <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> vlastnost nastavena na hodnotu `true`.  
  
 <xref:System.ServiceModel.FaultException%601>Při obdržení chybu, která je zadána v operaci kontraktu v reakci na obousměrný operace jsou výjimky vyvolány v klientovi (to znamená, metoda s <xref:System.ServiceModel.OperationContractAttribute> atribut s <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> nastavena na `false`).  
  
> [!NOTE]
>  Když [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služba má <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> vlastnost nastavena na hodnotu `true` klienta vyskytne to jako nedeklarované <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klienti můžou catch této konkrétní chyby nebo zpracování chyb v bloku catch pro <xref:System.ServiceModel.FaultException>.  
  
 Obvykle pouze <xref:System.ServiceModel.FaultException%601>, <xref:System.TimeoutException>, a <xref:System.ServiceModel.CommunicationException> výjimky jsou důležité pro klienty a služby.  
  
> [!NOTE]
>  Samozřejmě, ostatní výjimky dojít. Neočekávané výjimky patří závažné chyby jako <xref:System.OutOfMemoryException?displayProperty=nameWithType>; obvykle aplikace by neměl catch těchto metod.  
  
### <a name="catch-fault-exceptions-in-the-correct-order"></a>Zachytit výjimky selhání ve správném pořadí  
 Protože <xref:System.ServiceModel.FaultException%601> je odvozena z <xref:System.ServiceModel.FaultException>, a <xref:System.ServiceModel.FaultException> je odvozena z <xref:System.ServiceModel.CommunicationException>, je důležité k zachycení tyto výjimky ve správném pořadí. Pokud například máte try/catch – blok, ve kterém jste nejdřív catch <xref:System.ServiceModel.CommunicationException>neurčené chyb SOAP jsou zpracovávány není; všechny bloky catch následné zpracování vlastní, a všechny zadané <xref:System.ServiceModel.FaultException%601> se nikdy vyvolána výjimka.  
  
 Mějte na paměti, že jednu operaci může vracet libovolný počet zadaný chyb. Každý selhání je typu jedinečný a musí být zpracován samostatně.  
  
### <a name="handle-exceptions-when-closing-the-channel"></a>Při zavření v kanálu zpracování výjimek  
 Většina výše uvedené informace má dělat s chyb odeslaných v průběhu zpracování zpráv s aplikací, který je zprávy explicitně klientem po klientská aplikace volání operací na [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] objekt klienta.  
  
 I s místní objekty uvolnění objektu můžete zvýšit nebo maskování výjimky, ke kterým došlo během recyklace procesu. Něco podobného může dojít, když používáte [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] objekty klienta. Při volání operací odesíláte zprávy přes navázané připojení. Zavření kanálu může vyvolat výjimky Pokud připojení nelze zavřít, řádně nebo již byl uzavřen, i v případě, že všechny operace se vrátila správně.  
  
 Kanály objekt klienta jsou obvykle uzavřeny v jednom z následujících způsobů:  
  
-   Když [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] objekt klienta je recykluje.  
  
-   Když klientské aplikace volá <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>.  
  
-   Když klientské aplikace volá <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>.  
  
-   Když klientské aplikace volá operaci, je ukončující operace pro relaci.  
  
 Ve všech případech zavření kanálu dá pokyn kanál pro ukončení všechny základní kanály, které může být odesílání zpráv pro podporu komplexní funkcí na úrovni aplikace. Například pokud kontraktu vyžaduje relací vazbu se pokusí vytvořit relaci výměnou zpráv s kanálem služby, dokud nebude navázáno relaci. Při zavření kanálu základní kanál relace upozorní službu a ukončení relace. V takovém případě pokud kanál již přerušena, zavřená, nebo je jinak nepoužitelná (například když je odpojen síťový kabel), nelze informujte kanálem klienta služby kanálu, který relace je ukončena a může vést k výjimce.  
  
### <a name="abort-the-channel-if-necessary"></a>Abort kanál v případě potřeby  
 Protože zavření kanálu můžete také vyvolat výjimky, pak se doporučuje, aby kromě zachytávání výjimek chyby ve správném pořadí, je důležité k přerušení kanálu, který byl použitý při vytvoření volání v bloku catch.  
  
 Pokud selhání přenese tak informace o chybě specifické pro operace a zůstane možné, že jiné můžete použít, není třeba k přerušení kanál (i když tyto případy vyskytují jen vzácně). Ve všech ostatních případech se doporučuje, že můžete přerušit kanál. Ukázka, všechny tyto body, najdete v části [očekává výjimky](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
 Následující příklad kódu ukazuje, jak zpracování výjimek chybu protokolu SOAP v základní klientskou aplikaci, včetně deklarované chybu a nedeklarované selhání.  
  
> [!NOTE]
>  Tento ukázkový kód nepoužívá `using` vytvořit. Protože zavřením kanály můžete vyvolat výjimky, doporučuje se, že aplikace vytvořit [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta první a pak otevřete, používání a zavřít [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta do stejného bloku try. Podrobnosti najdete v tématu [klienta WCF – přehled](../../../docs/framework/wcf/wcf-client-overview.md) a [vyhnout problémům s příkazem Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 [!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.FaultException>  
 <xref:System.ServiceModel.FaultException%601>  
 <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>  
 [Očekávané výjimky](../../../docs/framework/wcf/samples/expected-exceptions.md)  
 [Vyhnout se tak problémům s příkazem Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)
