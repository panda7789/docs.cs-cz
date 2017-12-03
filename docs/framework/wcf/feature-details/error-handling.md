---
title: "Zpracování chyb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 215fb30772e4f1b25e20303b3f83d6fe0c00ebae
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="error-handling"></a>Zpracování chyb
## <a name="error-handling-in-windows-communication-foundation"></a>Chyba při zpracování ve Windows Communication Foundation  
 Když služba dojde neočekávané výjimce nebo chyba, návrh řešení zpracování výjimek s několika způsoby. Pokud není žádná jedním "Opravit" nebo "nejlépe praxi" zpracování chyb řešení, existuje více cest platný pro jednu vzít v úvahu. Za normálních okolností se doporučuje, že jeden implementovat hybridní řešení, které se kombinuje několik přístupů ze seznamu níže, v závislosti na složitosti implementace WCF, typ a frekvenci výjimky, zpracovaná oproti neošetřené povaha výjimky a všechny související trasování, protokolování nebo požadavky zásad.  
  
 Tato řešení jsou vysvětleny hlubšímu ve zbývající části této části.  
  
### <a name="the-microsoft-enterprise-library"></a>Knihovna Microsoft Enterprise  
 Microsoft Enterprise knihovny výjimka zpracování aplikace bloku pomáhá implementovat obecné vzory návrhu a vytvořit konzistentní strategie pro zpracování výjimek, které se vyskytují ve všech architektury vrstev podniková aplikace. Je navržen pro podporu kód typické obsažené v příkazech catch v součásti aplikace. Místo opakující se tento kód (například kód, který zaznamenává informace o výjimce) ve stejné catch – bloky v celé aplikaci, bloku aplikace zpracování výjimky umožňuje vývojářům zapouzdření této logiky jako obslužné rutiny výjimek opakovaně použitelné.  
  
 Tato knihovna obsahuje out-of-the-box obslužná rutina výjimky kontrakt chyb. Tato obslužná rutina výjimky je určen k použití v hranice služby Windows® Communication Foundation (WCF) a vygeneruje nové smlouvy chyby z výjimku.  
  
 Zaměřte se na začlenit běžně používané osvědčené postupy a zadejte běžný postup pro zpracování v celé vaší aplikaci výjimek aplikace bloky. Na druhé straně obslužné rutiny vlastní chyby a selhání kontrakty vyvinuté v vlastního může být taky hodně užitečný. Vlastní chyba obslužné rutiny pro instanci nabízejí vynikající možnost automaticky podporovat všechny výjimky FaultExceptions a také pro přidání možností protokolování do vaší aplikace.  
  
 Další informace najdete v tématu [knihovna Microsoft Enterprise](http://msdn.microsoft.com/library/ff632023.aspx).  
  
### <a name="dealing-with-expected-exceptions"></a>Práci s očekávané výjimky  
 Správné během akce je catch očekávané výjimky v každé operace nebo bod relevantní rozšiřitelnosti, rozhodněte, zda lze obnovit z a vrátí správné vlastní chyby v FaultException\<T >  
  
### <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>Práci s neočekávané výjimky pomocí IErrorHandler  
 Jak nakládat s neočekávané výjimky, je "připojit" IErrorHandler během doporučené akce. Chyba obslužné rutiny pouze zachytávat výjimky na úrovni modulu runtime WCF (layer "model služby"), není ve vrstvě kanálu. Vytvořte vlastní kanál, nedoporučuje se ve většině scénářů je jediný způsob, jak připojit IErrorHandler na úrovni kanálu.  
  
 "Neočekávanou výjimku" je obecně výjimku nezotavitelné ani zpracování výjimky; je, místo toho výjimku neočekávané uživatele. Výjimku nezotavitelné (například k výjimce z důvodu nedostatku paměti) – jeden obecně provádí [obslužná rutina výjimky modelu služby](http://msdn.microsoft.com/library/system.servicemodel.dispatcher.exceptionhandler.aspx) automaticky – nelze obecně zpracovat řádně a z důvodu pouze pro zpracování takové výjimky může být vůbec proveďte další protokolování nebo pro návrat do klienta standardní výjimka. Došlo k výjimce zpracování ve zpracování zprávy – například v serializaci, kodér nebo formátování úroveň – obecně nelze zpracovat jako IErrorHandler, protože je obecně buď příliš brzké, nebo příliš pozdní pro obslužnou rutinu chyby zasáhnout podle čas, kdy dojde k tyto výjimky. Podobně nelze zpracovat výjimky přenosu IErrorHandler.  
  
 S IErrorHandler můžete řídit explicitně chování vaší aplikace, pokud je vyvolána výjimka. Můžete:  
  
1.  Rozhodněte, zda se má odeslat klientovi chybu  
  
2.  Nahraďte výjimku chybu  
  
3.  Nahraďte chybu jiné chyby  
  
4.  Provedení protokolování nebo trasování  
  
5.  Provedení dalších vlastních aktivit  
  
 Obslužná rutina vlastní chybové jeden můžete nainstalovat jeho přidáním do vlastnost ErrorHandlers dispečerů kanál pro vaši službu.  Je možné, že více než jeden obslužnou rutinu chyby a stejně jako v pořadí, ve kterém budou přidány do této kolekce.  
  
 IErrorHandler.ProvideFault řídí selhání zprávu, která je odeslána do klienta. Tato metoda je volána bez ohledu na typ výjimky vyvolané operace ve službě. Pokud žádná operace se zde provádí, WCF předpokládá jeho výchozí chování a bude pokračovat, jako kdyby nebyla žádná vlastní chybě obslužné rutiny na místě.  
  
 Jednou z oblastí, můžete případně použít tuto metodu je, když chcete vytvořit centrální místo pro výjimky převádění chyb před jejich odesláním do klienta (zajistit, aby instance není vyřazen a kanál není přesunut do stavu chybný).  
  
 Metoda IErrorHandler.HandleError se obvykle používá k implementaci chyba související chování, například protokolování, systémová oznámení, vypínání aplikace atd. IErrorHandler.HandleError lze volat na více místech uvnitř služby a v závislosti na tom, kde je vyvolána chyba, metoda HandleError může nebo nemusí být volána ve stejném vlákně, v jako operaci; v tomto ohledu jsou vytvářeny žádné záruky.  
  
### <a name="dealing-with-exceptions-outside-wcf"></a>Práci s výjimkami mimo WCF  
 Často, může dojít v kontextu aplikace WCF výjimek konfigurace, výjimky řetězec připojení databáze a další podobné výjimky, ale jsou sami nejsou výjimky způsobené modelu služby nebo samotnou webovou službu. Tyto výjimky jsou "Regulérní" výjimky externí k webové službě a měla by ji zpracovat, stejně jako ostatní externí výjimky v prostředí jsou zpracovávat.  
  
### <a name="tracing-exceptions"></a>Trasování výjimky  
 Trasování je pouze "pokrývající vše" místem, kde jeden může potenciálně sledovat všechny výjimky. Další informace o trasování a protokolování výjimky najdete v části protokolování a trasování.  
  
### <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>Chyby šablony URI při používání WebGetAttribute a WebInvokeAttribute  
 Atributy WebGet a WebInvoke umožňují zadejte identifikátor URI šablonu, která mapuje součástí adresu požadavek na operaci parametry. Například šablony URI "počasí / {stavu} / {města}" mapuje adresu požadavku do literálu tokeny, parametr s názvem stavu a parametr s názvem města. Tyto parametry mohou navázat poté podle názvu na některé formální parametry operace.  
  
 Parametry šablony se zobrazí ve formě řetězce v rámci identifikátoru URI při formální parametry typu kontraktu, může být typy jiné než řetězec. Převodu z je proto potřeba předtím, než může vyvolat operace. A [tabulku převod formátů](http://msdn.microsoft.com/library/bb412172.aspx) je k dispozici.  
  
 Ale pokud převod selže, pak neexistuje žádný způsob, jak v operaci vědět, že něco nepovede. Převod typu místo toho zobrazí ve formě selhání odesílání.  
  
 Odesílání chybu v převodu typů může být stejný jako u mnoha jiných typů chyb odesílání prověřovány nainstalováním obslužná rutina. Zpracování výjimek úrovně služeb se nazývá bod rozšiřitelnosti IErrorHandler. Z tohoto místa odpověď k odeslání zpět do volající – jako a proveďte vlastní úlohu a vytváření sestav – je možné zvolit.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování chyb základní WCF](http://msdn.microsoft.com/library/gg281715.aspx)
