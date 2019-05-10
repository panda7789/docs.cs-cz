---
title: Určování a zpracování chyb v kontraktech a službách
ms.date: 03/30/2017
helpviewer_keywords:
- handling faults [WCF]
ms.assetid: a9696563-d404-4905-942d-1e0834c26dea
ms.openlocfilehash: b9d6a4e2bb6b7e5c750ff7dad92934c4337c0083
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605948"
---
# <a name="specifying-and-handling-faults-in-contracts-and-services"></a>Určování a zpracování chyb v kontraktech a službách
Aplikace Windows Communication Foundation (WCF) zpracovávat chybové situace mapování objektů spravovaných výjimek na SOAP chyb a selhání objekty SOAP pro objekty spravované výjimky. Témata v této části popisují postup návrhu smlouvy ke zveřejnění chyba podmínek jako vlastní chyb SOAP, jak vracet tyto chyby jako součást implementace služby a jak klienti zachytit tyto chyby.  
  
## <a name="error-handling-overview"></a>Přehled zpracování chyb  
 Ve všech spravovaných aplikací, jsou reprezentovány chyby zpracování <xref:System.Exception> objekty. V aplikacích založených na protokolu SOAP jako jsou třeba aplikace WCF komunikovat metod služby informace o chybě zpracování pomocí chybové zprávy protokolu SOAP. Typy zpráv, které jsou zahrnuty v metadatech pro operaci služby a proto vytvořit selhání kontrakt, který můžou klienti používat pro své operace zkontrolujte robustní nebo interaktivní jsou chyby SOAP. Navíc protože chyb SOAP jsou vyjádřeny klientům v podobě XML, je vysoce interoperabilní typu systému, který můžete použít klientů na libovolné platformě SOAP, zvyšuje dosah aplikaci WCF.  
  
 Protože WCF aplikace spouští v rámci oba typy systémů chyba, žádné informace o spravované výjimce, která je odeslána do klienta musí být převést z výjimky na chyby SOAP ve službě, odeslání a převedeny na výjimky selhání u klientů WCF z chyb SOAP. V případě duplexní klientů můžete klienta kontrakty také odeslat chyb SOAP zpět do služby. V obou případech můžete použít výchozí chování služby výjimky, nebo můžete explicitně určit, zda – a jak – výjimky jsou mapovány na chybové zprávy.  
  
 Je možné odeslat dva druhy chyb SOAP: *deklarované* a *nedeklarovaný*. Deklarovat chyb SOAP jsou ty, ve kterých se má operace <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> atribut, který určuje vlastní typ chybu protokolu SOAP. *Nedeklarovaný* chyb SOAP nejsou zadány v kontraktu pro operaci.  
  
 Důrazně doporučujeme, aby operace služby deklarace jejich chyb s použitím <xref:System.ServiceModel.FaultContractAttribute> atributy formálně všech chyb SOAP, které klient můžete očekávat při běžném průběhu operace. Doporučuje se také, že vrátíte v rámci nastala chyba protokolu SOAP pouze informace, které klient musí vědět, chcete-li minimalizovat zpřístupnění informací.  
  
 Obvykle služby (a klienty s duplexní) proveďte následující kroky úspěšně integrovat do svých aplikací pro zpracování chyb:  
  
- Podmínky výjimek namapujte na vlastní chyby SOAP.  
  
- Služby a klienti odesílat a přijímat SOAP chyby jako výjimky.  
  
 Kromě toho klienti WCF a služeb můžete použít chyb nedeklarovaný soap pro účely ladění a můžete rozšířit výchozí chování chyby. Následující části popisují tyto úkoly a koncepty.  
  
## <a name="map-exceptions-to-soap-faults"></a>Mapování výjimky na chyby SOAP  
 Prvním krokem při vytváření operace, která zpracovává chybové stavy se rozhodnout, za jakých podmínek klientská aplikace by měla být informována o chybách. Některé operace mít chybové stavy, které jsou specifické pro jejich funkce. Například `PurchaseOrder` operace může vrátit konkrétní informace pro zákazníky, kteří se už nepovolují k zahájení nákupní objednávky. V ostatních případech, jako `Calculator` služby obecnějšího `MathFault` nastala chyba protokolu SOAP pravděpodobně možné popsat všechny chybové stavy napříč celou služby. Po chybové stavy klientů služby jsou označeny, lze sestavit vlastní chybu protokolu SOAP a operace může být označený jako vracející tuto chybu protokolu SOAP, když nastane jeho odpovídající chybový stav.  
  
 Další informace o tomto kroku vývoje služby ani klienta najdete v tématu [definiční a určení chyb](../../../docs/framework/wcf/defining-and-specifying-faults.md).  
  
## <a name="clients-and-services-handle-soap-faults-as-exceptions"></a>Klienti a služba zpracovává SOAP chyby jako výjimky  
 Identifikace operace chybové stavy, definování vlastních chyb SOAP a označení tyto operace jako vracející tyto chyby jsou první kroky v úspěšné zpracování chyb v aplikací služby WCF. Dalším krokem je správně implementovat, odesílání a příjem těchto chyb. Obvykle služby odeslat chyby k informování o chybové stavy klientských aplikací, ale duplexní klientů můžete také odeslat chyb SOAP služby.  
  
 Další informace najdete v tématu [odesílání a příjem chyb](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="undeclared-soap-faults-and-debugging"></a>Nedeklarovaný SOAP chyby a ladění  
 Deklarovaný chyb SOAP jsou velmi užitečné pro vytváření robustních a interoperabilní distribuované aplikace. V některých případech je užitečné pro službu (nebo duplexní klienta) k odeslání nebyla deklarována chybu protokolu SOAP, ten, který není zmíněn v na webové služby WSDL (Description Language) pro danou operaci. Například při vytváření služby neočekávané situace může dojít, ve kterých se hodí při ladění účely odesílat informace zpět do klienta. Kromě toho můžete nastavit <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> vlastnost nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> vlastnost `true` tak, aby povolovala WCF klientům získat informace o výjimkách operace vnitřní chybě služby. Odesílání chyb jednotlivých i nastavení ladění vlastnosti chování, které jsou popsány v [odesílání a příjem chyb](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
> [!IMPORTANT]
>  Vzhledem k tomu, že spravované výjimky můžete zveřejnit informace o interní aplikace, nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> k `true` můžete povolit WCF klientům získat informace o výjimkách operace vnitřní chybě služby, včetně osobně identifikovat nebo další citlivé informace.  
>   
>  Proto nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> k `true` se doporučuje jenom jako způsob, jak dočasně ladit aplikaci služby. Kromě toho rozhraní jazyka WSDL pro metodu, která vrátí nezpracované se spravovanými výjimkami tímto způsobem neobsahuje smlouvu pro <xref:System.ServiceModel.FaultException%601> typu <xref:System.ServiceModel.ExceptionDetail>. Klienti musí očekávat možnost Neznámá chyba protokolu SOAP (klientům WCF jako <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objekty) správně získat informace o ladění.  
  
## <a name="customizing-error-handling-with-ierrorhandler"></a>Přizpůsobení zpracování chyb pomocí IErrorHandler  
 Pokud nemáte speciální požadavky, které chcete přizpůsobit zprávu odpovědi klientovi, když dojde k výjimce úrovni aplikace nebo provádět některé vlastní zpracování po vrácení zprávy s odpovědí, implementujte <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> rozhraní.  
  
## <a name="fault-serialization-issues"></a>Chyby serializace problémy  
 Při deserializaci kontrakt chyby, poprvé pokusí shodovat s názvem kontraktu selhání ve zprávě SOAP s typem odolnosti kontraktu WCF. Pokud nemůže najít přesnou shodu, kterou pak vyhledá seznam v abecedním pořadí pro kompatibilní typ smlouvy k dispozici selhání. Pokud dvě selhání kontrakty jsou nekompatibilní typy (je podtřídou třídy, například) nesprávného typu lze deserializovat chyby. K tomu dochází pouze pokud kontrakt chyby neurčuje název, obor názvů a akce. K tomuto problému zabránit, vždy plně kvalifikujte kontrakty selhání tak, že zadáte jméno, obor názvů a atributů akce. Kromě toho pokud jste definovali počet chybu související s kontrakty odvozen ze sdíleného základní třídy, ujistěte se, že pro všemi novými členy s označení `[DataMember(IsRequired=true)]`. Další informace o to `IsRequired` viz atribut <xref:System.Runtime.Serialization.DataMemberAttribute>. Se základní třídy brání kompatibilní typ a vynutit chyby a lze deserializovat do správné odvozeného typu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.FaultException>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.CommunicationException>
- <xref:System.ServiceModel.FaultContractAttribute.Action%2A>
- <xref:System.ServiceModel.FaultException.Code%2A>
- <xref:System.ServiceModel.FaultException.Reason%2A>
- <xref:System.ServiceModel.FaultCode.SubCode%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- [Definice a určení chyb](../../../docs/framework/wcf/defining-and-specifying-faults.md)
