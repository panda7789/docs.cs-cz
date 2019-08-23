---
title: Chyby odesílání a přijímání
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
ms.openlocfilehash: 096b56d720a7facce68111a0f46cf05687dc9a34
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945664"
---
# <a name="sending-and-receiving-faults"></a>Chyby odesílání a přijímání
Chyby protokolu SOAP vyjadřují informace chybové podmínky ze služby klientovi a v duplexovém případě od klienta ke službě v rámci interoperability. Služba obvykle definuje vlastní obsah chyby a určuje, které operace se můžou vrátit. (Další informace najdete v tématu [Definování a určení chyb](../../../docs/framework/wcf/defining-and-specifying-faults.md).) Toto téma popisuje, jak může služba nebo duplexní klient odesílat tyto chyby, když došlo k odpovídajícímu chybovému stavu a jak aplikace klienta nebo služby tyto chyby zpracovává. Přehled zpracování chyb v aplikacích Windows Communication Foundation (WCF) najdete v tématu [určení a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="sending-soap-faults"></a>Odesílání chyb protokolu SOAP  
 Deklarované chyby protokolu SOAP jsou ty, ve kterých operace má a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> určuje vlastní typ chyby SOAP. Nedeklarované chyby protokolu SOAP jsou ty, které nejsou ve kontraktu pro operaci zadané.  
  
### <a name="sending-declared-faults"></a>Odesílání deklarovaných chyb  
 Chcete-li odeslat deklarovanou chybu protokolu SOAP, zjistěte chybový stav, pro který je chyba protokolu SOAP vhodná, <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> a vyvolejte nový, kde parametr typu je nový objekt typu určeného v <xref:System.ServiceModel.FaultContractAttribute> poli pro tuto operaci. Následující příklad kódu ukazuje použití <xref:System.ServiceModel.FaultContractAttribute> pro určení `SampleMethod` , že operace může vracet chybu protokolu SOAP `GreetingFault`s typem podrobností.  
  
 [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
 [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
 Chcete-li `GreetingFault` předat informace o chybě klientovi, Zachyťte příslušný chybový stav a vyvolejte <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> nový typ `GreetingFault` s novým `GreetingFault` objektem jako argument, jak je uvedeno v následujícím příkladu kódu. Pokud klient je klientská aplikace WCF, dojde k tomu jako spravovaná výjimka, kde typ je <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> typu. `GreetingFault`  
  
 [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
 [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
### <a name="sending-undeclared-faults"></a>Odesílání nedeklarovaných chyb  
 Odesílání nedeklarovaných chyb může být velmi užitečné pro rychlé diagnostikování a ladění problémů v aplikacích WCF, ale jeho užitečnost jako ladicí nástroj je omezený. Obecně platí, že při ladění doporučujeme použít <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> vlastnost. Když nastavíte tuto hodnotu na true, klienti budou mít takové chyby jako <xref:System.ServiceModel.FaultException%601> výjimky typu. <xref:System.ServiceModel.ExceptionDetail>  
  
> [!IMPORTANT]
> Vzhledem k tomu, že spravované výjimky můžou vystavovat <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> interní `true` informace o aplikaci, nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nebo může povolit klientům WCF získávat informace o výjimkách interních operací služby, včetně osobních údajů. identifikovatelné nebo jiné citlivé informace.  
>   
>  Proto se nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> na `true` dá doporučit jenom jako způsob dočasného ladění aplikace služby. Kromě toho WSDL pro metodu, která vrací neošetřené spravované výjimky tímto způsobem, neobsahuje kontrakt pro <xref:System.ServiceModel.FaultException%601> typ. <xref:System.ServiceModel.ExceptionDetail> Aby klienti mohli správně získat informace o ladění, musí očekávat neznámou chybu SOAP <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> (vrácený klientům WCF jako objekty).  
  
 Chcete-li odeslat nedeklarovanou chybu protokolu SOAP <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> , vyvolejte objekt (tj. ne obecný <xref:System.ServiceModel.FaultException%601>typ) a předejte řetězec konstruktoru. To je zpřístupněno klientským aplikacím WCF jako vyvolaná <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> výjimka, kde je řetězec k dispozici <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> voláním metody.  
  
> [!NOTE]
> Pokud deklarujete chybu SOAP typu String a potom ji vyvoláte ve <xref:System.ServiceModel.FaultException%601> vaší službě jako parametr typu <xref:System.String?displayProperty=nameWithType> je <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> hodnota řetězce přiřazena vlastnosti a není k dispozici z <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType>.  
  
## <a name="handling-faults"></a>Zpracování chyb  
 V klientech WCF jsou chyby protokolu SOAP, ke kterým došlo během komunikace, které jsou důležité pro klientské aplikace, vyvolány jako spravované výjimky. I když existuje mnoho výjimek, ke kterým může dojít při provádění libovolného programu, aplikace používající programovací model klienta WCF mohou v důsledku komunikace očekávat výjimky následujících dvou typů.  
  
- <xref:System.TimeoutException>  
  
- <xref:System.ServiceModel.CommunicationException>  
  
 <xref:System.TimeoutException>objekty jsou vyvolány, když operace překročí zadané časové období.  
  
 <xref:System.ServiceModel.CommunicationException>objekty jsou vyvolány v případě, že dojde k určité opravitelné chybě komunikace v rámci služby nebo klienta.  
  
 Třída má dva důležité odvozené <xref:System.ServiceModel.FaultException> typy a obecný <xref:System.ServiceModel.FaultException%601> typ. <xref:System.ServiceModel.CommunicationException>  
  
 <xref:System.ServiceModel.FaultException>výjimky jsou vyvolány, když naslouchací proces obdrží chybu, která není očekávána nebo určena v kontraktu operace; obvykle k tomu dochází, když je aplikace Laděna a služba má <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> vlastnost nastavenou na. `true`  
  
 <xref:System.ServiceModel.FaultException%601>výjimky jsou vyvolány v klientovi, pokud je v reakci na obousměrnou operaci přijata chyba, která je zadána v kontraktu operace (tj. metodou s <xref:System.ServiceModel.OperationContractAttribute> <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> atributem nastaveným na `false`hodnotu).  
  
> [!NOTE]
> Pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> má služba WCF vlastnost nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nastavenou na `true` klientské prostředí, jedná se o nedeklaraci <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klienti mohou buď zachytit tuto konkrétní chybu, nebo zpracovat chybu v bloku catch pro <xref:System.ServiceModel.FaultException>.  
  
 Pro klienty a <xref:System.ServiceModel.FaultException%601>služby <xref:System.TimeoutException>jsou typicky <xref:System.ServiceModel.CommunicationException> důležité pouze výjimky, a.  
  
> [!NOTE]
> K dalším výjimkám samozřejmě dochází. Neočekávané výjimky zahrnují závažná <xref:System.OutOfMemoryException?displayProperty=nameWithType>selhání, jako je, obvykle by aplikace neměly tyto metody zachytit.  
  
### <a name="catch-fault-exceptions-in-the-correct-order"></a>Zachytit výjimky chyb ve správném pořadí  
 Vzhledem <xref:System.ServiceModel.FaultException%601> k tomu, <xref:System.ServiceModel.FaultException>že jsou <xref:System.ServiceModel.FaultException> odvozeny z <xref:System.ServiceModel.CommunicationException>a jsou odvozeny z, je důležité zachytit tyto výjimky ve správném pořadí. Pokud například máte blok try/catch, ve kterém jste nejprve zachytili <xref:System.ServiceModel.CommunicationException>, všechny zadané a nespecifikované chyby SOAP jsou zpracovávány. jakékoli následné bloky catch pro zpracování vlastní <xref:System.ServiceModel.FaultException%601> výjimky nejsou nikdy vyvolány.  
  
 Pamatujte, že jedna operace může vracet libovolný počet zadaných chyb. Každá chyba je jedinečného typu a musí se zpracovat samostatně.  
  
### <a name="handle-exceptions-when-closing-the-channel"></a>Zpracování výjimek při uzavírání kanálu  
 Většinu předchozí diskuze je třeba provést s chybami odeslanými v průběhu zpracování zpráv aplikace, tedy zpráv, které jsou explicitně odesílány klientem, když klientská aplikace volá operace na objektu klienta služby WCF.  
  
 I když místní objekty vyřazuje objekt, mohou buď vyvolat nebo maskovat výjimky, ke kterým dojde během procesu recyklace. K podobnému problému může dojít, když používáte objekty klienta WCF. Při volání operací, které odesíláte zprávy přes navázané připojení. Zavření kanálu může vyvolat výjimky, pokud připojení nelze vyčistit nebo je již uzavřeno, i když všechny operace vráceny správně.  
  
 Kanály klientského objektu jsou obvykle uzavřeny jedním z následujících způsobů:  
  
- Při recyklování objektu klienta služby WCF.  
  
- Když klientská aplikace volá <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>.  
  
- Když klientská aplikace volá <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>.  
  
- Když klientská aplikace zavolá operaci, která je ukončující operací pro relaci.  
  
 Ve všech případech uzavření kanálu instruuje kanál, aby začal uzavírat všechny základní kanály, které mohou odesílat zprávy pro podporu složitých funkcí na úrovni aplikace. Například Pokud kontrakt vyžaduje, aby se vazba pokusila vytvořit relaci výměnou zpráv s kanálem služby, dokud není vytvořena relace. Když je kanál uzavřený, podkladový kanál relace tuto službu upozorní, že se relace ukončí. V takovém případě, pokud je kanál již přerušený, uzavřený nebo jinak nepoužitelný (například pokud je síťový kabel odpojený), kanál klienta nemůže informovat kanál služby o ukončení relace a může dojít k výjimce.  
  
### <a name="abort-the-channel-if-necessary"></a>V případě potřeby přerušit kanál  
 Vzhledem k tomu, že uzavírání kanálu může také vyvolat výjimky, doporučuje se, aby kromě zachycení výjimek chyb ve správném pořadí bylo důležité přerušit kanál, který byl použit při volání v bloku catch.  
  
 Pokud chyba předává informace o chybě specifické pro určitou operaci a je možné, že ji mohou používat i ostatní, nemusíte kanál přerušit (i když jsou tyto případy vzácné). Ve všech ostatních případech se doporučuje kanál přerušit. Ukázku, která ukazuje všechny tyto body, naleznete v tématu [očekávané výjimky](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
 Následující příklad kódu ukazuje, jak zpracovat výjimky chyb protokolu SOAP v základní klientské aplikaci, včetně deklarované chyby a nedeklarované chyby.  
  
> [!NOTE]
> Tento vzorový kód nepoužívá `using` konstrukci. Vzhledem k tomu, že uzavírací kanály můžou vyvolat výjimky, doporučuje se nejprve vytvořit klienta WCF a pak otevřít, použít a zavřít klienta WCF ve stejném bloku try. Podrobnosti najdete v tématu [Přehled klientů WCF](../../../docs/framework/wcf/wcf-client-overview.md) a [použití funkcí zavřít a přerušit k vydání prostředků klienta WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultException%601>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- [Očekávané výjimky](../../../docs/framework/wcf/samples/expected-exceptions.md)
- [Použití funkcí zavřít a přerušit k vydání prostředků klienta WCF](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)
