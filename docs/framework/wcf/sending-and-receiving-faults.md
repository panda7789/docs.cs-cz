---
title: Chyby odesílání a přijímání
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
ms.openlocfilehash: 2757f98066931ca1b5e3ef147cee2c819ee22606
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195056"
---
# <a name="sending-and-receiving-faults"></a>Chyby odesílání a přijímání
Chyb SOAP sdělit podmínku informace o chybě ze služby do klienta a v případě duplexní z klienta ke službě interoperabilní způsobem. Obvykle služby definuje vlastní chyby obsah a určuje, které operace vrátit. (Další informace najdete v tématu [definiční a určení chyb](../../../docs/framework/wcf/defining-and-specifying-faults.md).) Toto téma popisuje, jak služba nebo duplexní klient může poslat tyto chyby došlo k odpovídající chybovou podmínku a způsob klienta nebo aplikace služby zpracovává tyto chyby. Přehled v aplikacích Windows Communication Foundation (WCF) pro zpracování chyb, naleznete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="sending-soap-faults"></a>Odesílání chyb SOAP  
 Deklarovat chyb SOAP jsou ty, ve kterých se má operace <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> , která určuje vlastního typu chybu protokolu SOAP. Nedeklarovaný chyb SOAP jsou ty, které nejsou uvedené ve smlouvě operace.  
  
### <a name="sending-declared-faults"></a>Odesílání chyb deklarovaný  
 K odeslání deklarované nastala chyba protokolu SOAP, detekovat chybový stav, pro které je vhodné chybu protokolu SOAP a vyvolat nový <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> kde je vytvoření nového objektu na typ určený v parametru typu <xref:System.ServiceModel.FaultContractAttribute> pro danou operaci. Následující příklad kódu ukazuje použití <xref:System.ServiceModel.FaultContractAttribute> určit, že `SampleMethod` operace může vrátit chybu protokolu SOAP s typem podrobností `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
 [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
 K předání `GreetingFault` klienta, informace o chybě zachytit příslušné chybový stav a vyvolat nový <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> typu `GreetingFault` s novou `GreetingFault` objektu jako argument, jako v následujícím příkladu kódu. Pokud klienta je klientská aplikace WCF, je to prostředí jako spravované výjimky, kde je typ <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> typu `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
 [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
### <a name="sending-undeclared-faults"></a>Odesílání chyb nebyla deklarována  
 Odesílání nedeklarovaný chyby může být velmi užitečné pro rychlá Diagnostika a ladění problémů v aplikací služby WCF, ale jeho užitečnost jako nástroj pro ladění je omezený. Obecně platí, pokud její ladění je doporučeno používat <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> vlastnost. Když nastavíte tuto hodnotu na hodnotu true, klientů docházet k takové chyby jako <xref:System.ServiceModel.FaultException%601> výjimky typu <xref:System.ServiceModel.ExceptionDetail>.  
  
> [!IMPORTANT]
>  Vzhledem k tomu, že spravované výjimky můžete zveřejnit informace o interní aplikace, nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> k `true` můžete povolit WCF klientům získat informace o výjimkách operace vnitřní chybě služby, včetně osobně identifikovat nebo další citlivé informace.  
>   
>  Proto nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> k `true` se doporučuje jen jako způsob, jak dočasně ladění aplikace služby. Kromě toho rozhraní jazyka WSDL pro metodu, která vrátí nezpracované se spravovanými výjimkami tímto způsobem neobsahuje smlouvu pro <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klienti musí očekávat možnost Neznámá chyba protokolu SOAP (klientům WCF jako <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objekty) správně získat informace o ladění.  
  
 K odeslání nebyla deklarována chybu protokolu SOAP, throw <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objektu (to znamená, není generický typ <xref:System.ServiceModel.FaultException%601>) a předat řetězec konstruktoru. To je přístupný klientských aplikací WCF jako vyvolané výjimce <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> výjimky, kde je k dispozici řetězec voláním <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> metody.  
  
> [!NOTE]
>  Pokud deklarujete řetězcového typu nastala chyba protokolu SOAP a to poté vyvolají ve své službě jako <xref:System.ServiceModel.FaultException%601> kde je parametr typu <xref:System.String?displayProperty=nameWithType> přiřazena hodnota řetězce <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> vlastnost a není k dispozici <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType>.  
  
## <a name="handling-faults"></a>Zpracování chyb  
 Klienti WCF SOAP chyb, ke kterým dochází při komunikaci, které jsou zajímavé pro klientské aplikace jsou vyvolány jako spravované výjimky. I když existují mnoho výjimek, které se mohou vyskytnout při spuštění libovolné aplikace, pomocí programovacího modelu WCF klientské aplikace můžou očekávat pro zpracování výjimek z následujících dvou typů v důsledku komunikace.  
  
-   <xref:System.TimeoutException>  
  
-   <xref:System.ServiceModel.CommunicationException>  
  
 <xref:System.TimeoutException> objekty jsou vyvolány, když překročí zadaný časový limit operace.  
  
 <xref:System.ServiceModel.CommunicationException> objekty jsou vyvolány, když určitý chybový stav obnovit komunikaci na službu nebo klienta.  
  
 <xref:System.ServiceModel.CommunicationException> Třída má dvě důležité odvozené typy <xref:System.ServiceModel.FaultException> a Obecné <xref:System.ServiceModel.FaultException%601> typu.  
  
 <xref:System.ServiceModel.FaultException> výjimky jsou vyvolány při naslouchací proces obdrží chybu, která není očekáván nebo se musí zadat v kontrakt; obvykle k tomu dochází při ladění aplikace a že má služba <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nastavenou na `true`.  
  
 <xref:System.ServiceModel.FaultException%601> vyvolávání výjimek na straně klienta při přijetí chybu, která je uvedené ve smlouvě operace v reakci na operaci obousměrný (to znamená, metoda se <xref:System.ServiceModel.OperationContractAttribute> atributem <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> nastavena na `false`).  
  
> [!NOTE]
>  Pokud má služby WCF <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> vlastnost nastavena na hodnotu `true` klienta toto prostředí jako nedeklarovaný <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klienty můžete zachytit toto specifické selhání nebo zpracování chyb v bloku catch pro <xref:System.ServiceModel.FaultException>.  
  
 Obvykle pouze <xref:System.ServiceModel.FaultException%601>, <xref:System.TimeoutException>, a <xref:System.ServiceModel.CommunicationException> výjimky jsou zajímavé pro klienty a služby.  
  
> [!NOTE]
>  Jiné, samozřejmě, dojít k výjimkám. Neočekávané výjimky zahrnují katastrofických selhání jako <xref:System.OutOfMemoryException?displayProperty=nameWithType>; obvykle aplikace, neměli byste zachytit tyto metody.  
  
### <a name="catch-fault-exceptions-in-the-correct-order"></a>Zachytit výjimky selhání ve správném pořadí  
 Protože <xref:System.ServiceModel.FaultException%601> je odvozena z <xref:System.ServiceModel.FaultException>, a <xref:System.ServiceModel.FaultException> je odvozena z <xref:System.ServiceModel.CommunicationException>, je důležité k zachytávání těchto výjimek ve správném pořadí. Pokud například máte try/catch blok, ve kterém při prvním zachycení <xref:System.ServiceModel.CommunicationException>neurčené chyb SOAP jsou zpracovávány existuje; všechny bloky catch následné zpracování vlastní, a všechny zadané <xref:System.ServiceModel.FaultException%601> nikdy vyvolají výjimku.  
  
 Mějte na paměti, že jedna operace může vracet libovolný počet zadaný chyb. Každá chyba je jedinečný typ a musí být zpracovány samostatně.  
  
### <a name="handle-exceptions-when-closing-the-channel"></a>Zpracování výjimek při zavření kanálu  
 Většina předchozím diskusí souvisí se chyby odeslané během zpracování zpráv s aplikací, to znamená, zprávy explicitně odeslané klientem, když klientská aplikace volá operace u objektu klienta WCF.  
  
 I přes místní objekty uvolnění objektu můžete zvýšit nebo maskovat výjimky, které se vyskytují během recyklace procesu. Podobně může dojít, když používáte objekty klienta WCF. Při volání operací odesílají zprávy přes navázané připojení. Zavření kanálu může vyvolat výjimky Pokud připojení nelze zavřít, čistě nebo je už zavřený, i v případě, že všechny operace vrátila správně.  
  
 Obvykle kanály klientů objektů jsou uzavřeny v jednom z následujících způsobů:  
  
-   Pokud objekt klienta WCF recykluje.  
  
-   Když klientská aplikace volá <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>.  
  
-   Když klientská aplikace volá <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>.  
  
-   Když klientská aplikace volá operaci, která je ukončující operace pro relaci.  
  
 Ve všech případech zavření kanálu nastaví kanál pro ukončení všechny základní kanály, které mohou být odesílání zpráv komplexní funkci na úrovni aplikace. Například pokud kontrakt vyžaduje relace vazbu se pokusí navázat relaci výměnou zpráv pomocí služby kanálu, dokud se relace. Při zavření kanálu základním kanálu relace upozorní službu, že je relace ukončena. V takovém případě pokud kanál již přerušena, zavřeno, nebo je jinak nepůjdou použít (například, když je odpojen síťový kabel), nelze informovat kanálu klienta služby kanál, který je relace ukončena a může dojít k výjimce.  
  
### <a name="abort-the-channel-if-necessary"></a>Přerušení kanálu v případě potřeby  
 Protože zavření kanálu, může vyvolat výjimky, pak se doporučuje, že kromě zachycování výjimek chyby ve správném pořadí, je důležité pro přerušení kanál, který byl použitý při vytvoření volání v bloku catch.  
  
 Pokud se dá pořád, aby ho ostatní mohli používat v době přenáší informace o chybě specifické pro operace, není nutné pro přerušení kanálu (i když se tyto případy vyskytují jen vzácně). Ve všech ostatních případech se doporučuje, aby abort kanálu. Příklad, který předvádí všechny tyto body, naleznete v tématu [očekávané výjimky](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
 Následující příklad kódu ukazuje, jak zpracování výjimek chyby SOAP ve základní klientskou aplikaci, včetně chybu deklarované a nedeklarované selhání.  
  
> [!NOTE]
>  Tento ukázkový kód nepoužívá `using` vytvořit. Protože zavření kanály může vyvolat výjimky, je doporučeno, že aplikace vytvořte klienta WCF použití první a potom otevřete a zavřít klienta WCF ve stejném blok try. Podrobnosti najdete v tématu [přehled klientů WCF](../../../docs/framework/wcf/wcf-client-overview.md) a [použití zavřít a Abort k uvolnění prostředků klienta WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultException%601>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- [Očekávané výjimky](../../../docs/framework/wcf/samples/expected-exceptions.md)
- [Použít zavřít a přerušení k uvolnění prostředků klienta WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)
