---
title: Určování a zpracování chyb v kontraktech a službách
ms.date: 03/30/2017
helpviewer_keywords:
- handling faults [WCF]
ms.assetid: a9696563-d404-4905-942d-1e0834c26dea
ms.openlocfilehash: 95797bd341aa7051107209d6cd26097458661e5c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922947"
---
# <a name="specifying-and-handling-faults-in-contracts-and-services"></a>Určování a zpracování chyb v kontraktech a službách
Aplikace Windows Communication Foundation (WCF) zpracovávají chybové situace mapováním spravovaných objektů výjimek na objekty selhání SOAP a objekty selhání SOAP na spravované objekty výjimek. Témata v této části popisují, jak navrhovat smlouvy, aby se chybové stavy vystavoval jako vlastní chyby protokolu SOAP, jak tyto chyby vracet jako součást implementace služby a jak tyto chyby zachytí klienti.  
  
## <a name="error-handling-overview"></a>Přehled zpracování chyb  
 Ve všech spravovaných aplikacích jsou chyby zpracování reprezentovány <xref:System.Exception> objekty. V aplikacích založených na protokolu SOAP, jako jsou aplikace WCF, metody služeb sdělují informace o chybě zpracování pomocí zpráv o chybách protokolu SOAP. Chyby protokolu SOAP jsou typy zpráv, které jsou zahrnuty v metadatech pro operaci služby. proto je možné vytvořit kontrakt selhání, který mohou klienti použít k zajištění robustnější nebo interaktivní operace. Vzhledem k tomu, že chyby protokolu SOAP jsou vyjádřeny klientům ve formátu XML, je vysoce interoperabilní systém typů, který mohou klienti na libovolné platformě SOAP použít a zvyšují dosah vaší aplikace WCF.  
  
 Vzhledem k tomu, že aplikace WCF běží v obou typech chybových systémů, všechny spravované informace o výjimce, které se odesílají do klienta, musí být převedeny z výjimek na chyby protokolu SOAP ve službě, odeslány a převedeny z chyb protokolu SOAP na výjimky chyb v klientech WCF. V případě duplexních klientů můžou kontrakty klienta také odesílat chyby protokolu SOAP zpátky do služby. V obou případech můžete použít výchozí chování výjimky služby nebo můžete explicitně řídit, jestli – a jak jsou výjimky namapované na chybové zprávy.  
  
 Je možné odeslat dva typy chyb SOAP: *deklarovaný* a nedeklarovaný. Deklarované chyby protokolu SOAP jsou ty, ve kterých operace má <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> atribut, který určuje vlastní typ chyby SOAP. *Nedeklarovaný* V kontraktu pro operaci nejsou zadány chyby protokolu SOAP.  
  
 Důrazně se doporučuje, aby operace služby deklarovaly své chyby pomocí <xref:System.ServiceModel.FaultContractAttribute> atributu pro vytvoření všech chyb protokolu SOAP, které může klient očekávat při běžném průběhu operace. Také se doporučuje vrátit se do chyby protokolu SOAP pouze informace, které musí klient znát, aby bylo možné minimalizovat vyzrazení informací.  
  
 Služby (a duplexní klienti) obvykle procházejí následujícími kroky, které úspěšně integrují zpracování chyb do svých aplikací:  
  
- Namapujte podmínky výjimky na vlastní chyby protokolu SOAP.  
  
- Klienti a služby odesílají a přijímají chyby protokolu SOAP jako výjimky.  
  
 Kromě toho mohou klienti a služby WCF používat nedeklarované chyby protokolu SOAP pro účely ladění a mohou rozšířit chování výchozí chyby. Následující části popisují tyto úlohy a koncepty.  
  
## <a name="map-exceptions-to-soap-faults"></a>Mapování výjimek na chyby protokolu SOAP  
 Prvním krokem při vytváření operace, která zpracovává chybové stavy, je určit, za jakých podmínek by měla být klientská aplikace informována o chybách. Některé operace mají chybové podmínky specifické pro jejich funkce. Například `PurchaseOrder` operace může vracet konkrétní informace zákazníkům, kteří již nejsou oprávněni iniciovat nákupní objednávku. V jiných případech, jako je `Calculator` například služba, může být `MathFault` obecnější Chyba protokolu SOAP popsána v rámci celé služby. Jakmile se identifikují chybové stavy klientů vaší služby, může být vytvořena vlastní chyba protokolu SOAP a operace může být označena jako vracená Chyba protokolu SOAP, když dojde k odpovídajícímu chybovému stavu.  
  
 Další informace o tomto kroku vývoje služby nebo klienta najdete v tématu [Definování a určení chyb](../../../docs/framework/wcf/defining-and-specifying-faults.md).  
  
## <a name="clients-and-services-handle-soap-faults-as-exceptions"></a>Klienti a služby zpracovávají chyby protokolu SOAP jako výjimky.  
 Identifikují se chybové podmínky operace, definování vlastních chyb protokolu SOAP a označení operací, jako je vrácení těchto chyb, jsou první kroky při úspěšném zpracování chyb v aplikacích WCF. Dalším krokem je správné implementace odesílání a přijímání těchto chyb. Služby obvykle odesílají chyby, které upozorňují klientské aplikace na chybové podmínky, ale duplexní klienti mohou také odesílat chyby protokolu SOAP službám.  
  
 Další informace najdete v tématu [odesílání a příjem chyb](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="undeclared-soap-faults-and-debugging"></a>Nedeklarované chyby protokolu SOAP a ladění  
 Deklarované chyby protokolu SOAP jsou velmi užitečné pro vytváření robustních, interoperabilních a distribuovaných aplikací. V některých případech je však užitečné, aby služba (nebo duplexní klienti) odesílala nedeklarovanou chybu protokolu SOAP, kterou nezmiňuje jazyk WSDL (Web Services Description Language) pro tuto operaci. Například při vývoji služby může dojít k neočekávaným situacím, kdy je užitečné pro účely ladění pro odeslání informací zpět klientovi. Kromě toho můžete nastavit <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nebo vlastnost na `true` , aby klienti WCF mohli získat informace o výjimkách interní operace služby. Posílání jednotlivých chyb a nastavení vlastností chování ladění jsou popsány v tématu [odesílání a příjem chyb](../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
> [!IMPORTANT]
> Vzhledem k tomu, že spravované výjimky můžou vystavovat <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> interní `true` informace o aplikaci, nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nebo může povolit klientům WCF získávat informace o výjimkách interních operací služby, včetně osobních údajů. identifikovatelné nebo jiné citlivé informace.  
>   
>  Proto se nastavení <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> nebo <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> na `true` doporučuje jenom jako způsob, jak dočasně ladit aplikaci služby. Kromě toho WSDL pro metodu, která vrací neošetřené spravované výjimky tímto způsobem, neobsahuje kontrakt pro <xref:System.ServiceModel.FaultException%601> typ. <xref:System.ServiceModel.ExceptionDetail> Aby klienti mohli správně získat informace o ladění, musí očekávat neznámou chybu SOAP <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> (vrácený klientům WCF jako objekty).  
  
## <a name="customizing-error-handling-with-ierrorhandler"></a>Přizpůsobení zpracování chyb pomocí IErrorHandler  
 Pokud máte zvláštní požadavky pro přizpůsobení zprávy odpovědi klientovi, když dojde k výjimce na úrovni aplikace nebo provedení určitého vlastního zpracování po vrácení zprávy s odpovědí, implementujte <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> rozhraní.  
  
## <a name="fault-serialization-issues"></a>Problémy serializace chyby  
 Při deserializaci kontraktu selhání se WCF nejdříve pokusí vyhledat název kontraktu chyby ve zprávě SOAP s typem kontraktu selhání. Pokud nemůže najít přesnou shodu, vyhledá kompatibilní typ v seznamu dostupných kontraktů selhání v abecedním pořadí. Pokud jsou dvě kontrakty selhání kompatibilní typy (jedna je podtřídou jiného, například), je možné použít špatný typ k deserializaci chyby. K tomu dochází pouze v případě, že smlouva o selhání neurčuje název, obor názvů a akci. Chcete-li zabránit výskytu tohoto problému, vždy plně kvalifikované smlouvy o selhání zadáním názvu, oboru názvů a atributů akce. Pokud jste navíc definovali řadu souvisejících kontraktů selhání odvozených ze sdílené základní třídy, nezapomeňte označit všechny nové členy pomocí `[DataMember(IsRequired=true)]`. Další informace o tomto `IsRequired` atributu <xref:System.Runtime.Serialization.DataMemberAttribute>naleznete v tématu. Tím zabráníte, aby základní třída byla kompatibilního typu, a vynutíte deserializaci chyby do správného odvozeného typu.  
  
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
