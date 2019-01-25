---
title: Zpracování chyb
ms.date: 03/30/2017
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
ms.openlocfilehash: 396ad7ba6f690cedf783adcf180c92a88427a959
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695553"
---
# <a name="error-handling"></a>Zpracování chyb
## <a name="error-handling-in-windows-communication-foundation"></a>Zpracování chyb v Windows Communication Foundation  
 Když služba dojde k neočekávané výjimce nebo chyba, existuje více způsobů návrhu řešení typu zpracování výjimek. Když neexistuje žádné jedno "Opravit" nebo "co nejlépe praxi" zpracování chyb řešení, existuje více cest platná pro jeden vzít v úvahu. Obvykle je vhodné, že jedna implementace hybridní řešení, která kombinuje několik přístupů ze seznamu níže, v závislosti na složitosti implementace WCF, typ a frekvenci výjimek, zpracováván vs. neošetřené povaze výjimky a všechny související požadavky zásad, trasování a protokolování.  
  
 Tato řešení jsou vysvětleny hlouběji ve zbytku této části.  
  
### <a name="the-microsoft-enterprise-library"></a>Microsoft Enterprise Library  
 Microsoft Enterprise Library výjimka Handling Application Block pomáhá implementovat běžné vzory návrhu a vytvořit konzistentní strategie pro zpracování výjimek, ke kterým dochází v všechny vrstvy architektury podnikové aplikace. Je určená pro podporu typické kód obsažený v příkazech catch v součásti aplikace. Výjimka Handling Application Block namísto tento kód (například kód, který zaznamenává informace o výjimce) v blocích catch stejné v celé aplikaci, umožňuje vývojářům k zapouzdření tuto logiku jako obslužné rutiny výjimek opakovaně použitelné.  
  
 Tato knihovna obsahuje out-of-the-box obslužnou rutinu výjimky selhání kontraktu. Této obslužné rutiny výjimky je určen k použití na hranicích mezi službami Windows® Communication Foundation (WCF) a vygeneruje nový kontrakt chyby z výjimky.  
  
 Bloky aplikace cílem začlenění běžně používaných osvědčené postupy a poskytují běžný postup pro zpracování v rámci aplikace výjimek. Na druhé straně obslužné rutiny vlastních chyb a selhání kontraktů vyvinuté v vlastního může také být velmi užitečné. Například obslužné rutiny vlastních chyb poskytuje skvělou příležitost se automaticky zvýšit úroveň všech výjimek FaultExceptions a také pro přidání možností protokolování do vaší aplikace.  
  
 Další informace najdete v tématu [Microsoft Enterprise Library](https://msdn.microsoft.com/library/ff632023.aspx).  
  
### <a name="dealing-with-expected-exceptions"></a>Práce s očekávané výjimky  
 Správný kurz akce má zachytit očekávané výjimky v každé operace nebo bod relevantní rozšiřitelnosti, rozhodnout, zda je možné obnovit z a vrátí správné vlastní chyby v FaultException\<T >  
  
### <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>Řešení pomocí IErrorHandler neočekávané výjimky  
 Řešit neočekávané výjimky, je "spojit" IErrorHandler doporučené kurz akce. Obslužné rutiny chyb pouze zachytit výjimky na úrovni modulu runtime WCF (vrstva "model služby"), ne ve vrstvě kanálu. Jediný způsob, jak se připojit IErrorHandler na úrovni kanálu je vytvořte vlastní kanál, který se ve většině scénářů nedoporučuje.  
  
 "Neočekávanou výjimku" není obecně neobnovitelné výjimce ani zpracování výjimek; je místo toho uživatel neočekávané výjimky. Neobnovitelné výjimce (například výjimku paměti) – jedna obecně provádí [obslužná rutina výjimky modelu služby](xref:System.ServiceModel.Dispatcher.ExceptionHandler) automaticky – nelze obecně zpracovat bez výpadku a jediným důvodem pro zpracování takových výjimky vůbec může být dodatečné protokolování nebo se vraťte do klienta standardní výjimka. Dojde k výjimce zpracování v zpracování zprávy – například serializace, kodér nebo úroveň formátovací modul – obecně nelze zpracovat v IErrorHandler, protože je obecně buď příliš brzy, nebo příliš pozdě pro obslužnou rutinu chyb zasáhnout podle čas, kdy dojde k tyto výjimky. Podobně nelze zpracovat výjimky přenosu IErrorHandler.  
  
 S IErrorHandler můžete explicitně řídit chování aplikace, když dojde k výjimce. Můžete:  
  
1.  Rozhodněte, jestli se mají odeslat klientovi chybu  
  
2.  Nahraďte výjimku chybu  
  
3.  Nahraďte jinou chybu selhání  
  
4.  Provádět protokolování nebo trasování  
  
5.  Provést jiné vlastní aktivity  
  
 Obslužné rutiny vlastních chyb jeden můžete nainstalovat tak, že přidáte na vlastnost ErrorHandlers dispečerů kanálu pro vaši službu.  Je možné mít víc než jedna obslužná rutina chyb a jsou volány v pořadí, ve kterém jsou přidané do této kolekce.  
  
 IErrorHandler.ProvideFault řídí chybová zpráva, která je odeslána do klienta. Tato metoda je volána bez ohledu na typ výjimky vyvolané operace ve službě. Pokud žádná operace se zde provádí, WCF předpokládá jeho výchozí chování a pokračuje, jako by nebyly žádné obslužné rutiny vlastních chyb na místě.  
  
 Jednu oblast, můžete případně použít tento přístup je, když chcete vytvořit centrální místo pro převod výjimky na chyby, před jejich odesláním do klienta (zajistí, že instance není uvolněn a kanál nebyl přesunut do stavu chyba).  
  
 Metoda IErrorHandler.HandleError se obvykle používá k implementaci chyba související chování jako je například protokolování, chyba systému oznámení, vypínání aplikace atd. IErrorHandler.HandleError lze volat na více místech ve službě, a v závislosti na tom, kde je vyvolána chyba, metoda HandleError můžou nebo nelze volat ve stejném vlákně jako operace; v tomto ohledu nebudou provedeny žádné záruky.  
  
### <a name="dealing-with-exceptions-outside-wcf"></a>Práce s výjimkami mimo WCF  
 Často, může dojít v rámci kontextu aplikace WCF konfigurace výjimek, výjimky připojovací řetězec databáze a další podobné výjimky, ale představují samy o sobě nejsou výjimek způsobených modelu služby nebo samotnou webovou službu. Tyto výjimky jsou externí vzhledem k webové službě "regulární" výjimky a by měly být zpracovány stejně jako ostatní externí výjimky v prostředí mají zpracovat.  
  
### <a name="tracing-exceptions"></a>Sledování výjimek  
 Trasování je pouze "pokrývající vše" místem, kde jeden může potenciálně sledovat všechny výjimky. Další informace o trasování a protokolování výjimek naleznete v tématu trasování a protokolování.  
  
### <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>Identifikátor URI šablony chyby při použitím WebGetAttribute i WebInvokeAttribute  
 Atributy WebGet a WebInvoke vám umožňují určit šablona identifikátoru URI, který mapuje součástí adresu požadavek na parametry operace. Například šablona identifikátoru URI "počasí / {state} / {Město}" mapuje adresu požadavek na literálové tokeny, parametr s názvem stavu a parametr s názvem Město. Tyto parametry může pak být vázána podle názvu k některým formálních parametrů operace.  
  
 Parametry šablony se zobrazí ve formě řetězce v rámci identifikátoru URI při typy jiné než řetězec může být formální parametry typu kontraktu. Převod je proto potřeba předtím, než může vyvolat operaci. A [tabulku převod formátů](wcf-web-http-programming-model-overview.md) je k dispozici.  
  
 Nicméně pokud převod selže, pak se nedají v operaci vědět, že se něco nepovedlo. Převod typu místo toho poskytuje informace o ve formě selhání odeslání.  
  
 Chyba odeslání převodu typu může být stejně jako mnoho dalších typů zpracování chyb zkontroloval nainstalováním obslužná rutina chyby. Bod rozšiřitelnosti IErrorHandler je volána pro zpracování výjimek na úrovni služby. Odtud odpověď k odeslání zpět do volajícího – a také jako provádět jakékoli vlastní úlohy vytváření sestav – je možné zvolit.  
  
## <a name="see-also"></a>Viz také:
- [Základní programování WCF](../basic-wcf-programming.md)
