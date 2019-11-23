---
title: Zpracování chyb
ms.date: 03/30/2017
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
ms.openlocfilehash: f6c0d676a37648678b2b726a46a6238ccc1b3331
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004885"
---
# <a name="error-handling-in-windows-communication-foundation-wcf"></a>Zpracování chyb v Windows Communication Foundation (WCF)

Když dojde k neočekávané výjimce nebo chybě služby, existuje několik způsobů, jak navrhnout řešení pro zpracování výjimek. I když není k dispozici žádný jediný "správný" nebo "osvědčený postup" řešení pro zpracování chyb, existuje několik platných cest pro jeden, který je třeba zvážit. Obvykle se doporučuje, aby jedna implementovala hybridní řešení, které kombinuje více přístupů ze seznamu níže v závislosti na složitosti implementace WCF, typu a četnosti výjimek, zpracovaných a nezpracovaných povaze. výjimky a všechny přidružené trasování, protokolování nebo požadavky zásad.

Tato řešení jsou podrobněji vysvětlena ve zbývající části tohoto oddílu.

## <a name="the-microsoft-enterprise-library"></a>Microsoft Enterprise Library

Blok aplikace pro zpracování výjimek Microsoft Enterprise Library pomáhá implementovat běžné vzory návrhu a vytvořit konzistentní strategii pro zpracování výjimek, ke kterým dochází ve všech vrstvách architektury podnikové aplikace. Je navržena tak, aby podporovala typický kód obsažený v příkazech catch v součástech aplikace. Místo opakování tohoto kódu (například kódu, který protokoluje informace o výjimce) ve stejných blocích catch v rámci aplikace, blok aplikace pro zpracování výjimek umožňuje vývojářům zapouzdřit tuto logiku jako opakovaně použitelné obslužné rutiny výjimek.

Tato knihovna obsahuje předem zastaralou obslužnou rutinu výjimky smlouvy o selhání. Tato obslužná rutina výjimky je navržena pro použití v hranicích služby WCF a generuje novou kontrakt chyby z výjimky.

Aplikační bloky mají za cíl zahrnovat běžně používané osvědčené postupy a poskytují společný přístup k zpracování výjimek v celé vaší aplikaci. Na druhé straně vlastní obslužné rutiny chyb a smlouvy o selhání vyvíjené na vlastní může být také velmi užitečné. Například vlastní obslužné rutiny chyb poskytují vynikající možnost automaticky propagovat všechny výjimky na FaultExceptions a také přidávat možnosti protokolování do aplikace.

Další informace najdete v tématu [Microsoft Enterprise Library](https://docs.microsoft.com/previous-versions/msp-n-p/ff632023(v=pandp.10)).

## <a name="dealing-with-expected-exceptions"></a>Zvládnutí očekávaných výjimek

Správným postupem je zachytit očekávaná výjimka v každé operaci nebo v příslušném bodu rozšiřitelnosti, rozhodnout, zda je lze obnovit z a vrátit správnou vlastní chybu v FaultException\<T >.
  
## <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>Zvládnutí neočekávaných výjimek pomocí IErrorHandler

Pokud se chcete zabývat s neočekávanými výjimkami, doporučuje se postupovat "připojit" k IErrorHandler. Obslužné rutiny chyb zachytí pouze výjimky na úrovni modulu runtime WCF ("vrstva modelu služby"), nikoli ve vrstvě kanálu. Jediným způsobem, jak připojit IErrorHandler na úrovni kanálu, je vytvořit vlastní kanál, který se ve většině scénářů nedoporučuje.

"Nečekaná výjimka" není obecně výjimka nezotavitelné ani výjimka zpracování; místo toho se jedná o neočekávanou výjimku uživatele. Výjimka nezotavitelné (například výjimka z důvodu nedostatku paměti) – jedna všeobecně zpracovaná [obslužnou rutinou výjimky modelu služby](xref:System.ServiceModel.Dispatcher.ExceptionHandler) – nelze obecně zpracovat a jediný důvod, jak tuto výjimku zpracovat, může být další protokolování nebo vrácení standardní výjimky klientovi. Při zpracování zprávy dojde k výjimce zpracování – například na úrovni serializace, kodér nebo formátovacího modulu – obecně nelze zpracovat na IErrorHandler, protože je všeobecně příliš nebo příliš pozdě, než se obslužná rutina chyby zavede čas, kdy dochází k těmto výjimkám. Podobně je možné zpracovat výjimky přenosu na IErrorHandler.

Pomocí IErrorHandler můžete explicitně řídit chování aplikace, když je vyvolána výjimka. Možná:  

1. Rozhodněte, zda chcete klientovi odeslat chybu.

2. Nahraďte výjimku chybou.

3. Nahraďte chybu jinou chybou.

4. Proveďte protokolování nebo trasování.

5. Proveďte další vlastní aktivity.

Jedna z nich může nainstalovat vlastní obslužnou rutinu chyb přidáním do vlastnosti ErrorHandlers pro odeslání kanálu pro vaši službu.  Je možné mít více než jednu obslužnou rutinu chyb a jsou volány v pořadí, v jakém jsou přidány do této kolekce.

IErrorHandler. ProvideFault řídí zprávu o chybě, která je odeslána klientovi. Tato metoda je volána bez ohledu na typ výjimky vyvolané operací ve vaší službě. Pokud zde není provedena žádná operace, WCF předpokládá své výchozí chování a pokračuje, jako kdyby nebyly na svém místě žádné vlastní obslužné rutiny chyb.

Jednou z oblastí, které byste mohli použít tento přístup, je, že chcete vytvořit centrální místo pro převod výjimek na chyby předtím, než jsou odesílány klientovi (zajištění, že instance není uvolněna a kanál není přesunut do stavu selhání).

Metoda IErrorHandler. HandleError se obvykle používá k implementaci chování souvisejícího s chybami, jako je protokolování chyb, systémová oznámení, ukončení aplikace atd. IErrorHandler. HandleError lze volat na více místech uvnitř služby a v závislosti na tom, kde je chyba vyvolána, metoda HandleError může nebo nemusí být volána stejným vláknem jako operace. v tomto ohledu se nevedou žádné záruky.

## <a name="dealing-with-exceptions-outside-wcf"></a>Obchodování s výjimkami mimo WCF

V kontextu aplikace WCF se často můžou vyskytovat výjimky konfigurace, výjimky připojovacích řetězců k databázi a jiné podobné výjimky, ale samy nejsou výjimky způsobené modelem služby nebo samotnými webovými službami. Tyto výjimky jsou "standardními" výjimkami externími pro webovou službu a měly by být zpracovány stejně jako jiné externí výjimky v prostředí.

## <a name="tracing-exceptions"></a>Trasování výjimek

Trasování je jediné místo "catch-All", kde jeden může potenciálně Zobrazit všechny výjimky. Další informace o trasování a protokolování výjimek najdete v tématu trasování a protokolování.

## <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>Chyby šablon identifikátoru URI při použití funkce WebGetAttribute a WebInvokeAttribute

Atributy WebGet a WebInvoke umožňují zadat šablonu identifikátoru URI, která mapuje součásti adresy požadavku na parametry operace. Například šablona identifikátoru URI "počasí/{State}/{City}" mapuje adresu žádosti na literálové tokeny, parametr s názvem State a parametr s názvem City. Tyto parametry je pak možné svázat podle názvu s některými formálními parametry operace.

Parametry šablony se zobrazí ve formě řetězců v identifikátoru URI, zatímco formální parametry typové kontraktu mohou být typy bez řetězců. Proto je třeba provést převod, aby bylo možné operaci vyvolat. [Tabulka formátů převodu](wcf-web-http-programming-model-overview.md) je k dispozici.

Pokud však převod neproběhne úspěšně, neexistuje žádný způsob, jak dát této operaci jistotu, že došlo k nějakému problému. Převod typu se místo povrchů ve formě chyby odeslání.

Selhání odeslání převodu typu lze zkontrolovat stejně jako u mnoha dalších typů selhání odeslání instalací obslužné rutiny chyby. Bod rozšiřitelnosti IErrorHandler se volá za účelem zpracování výjimek na úrovni služby. Odtud se dá odpověď odeslat volajícímu a také provádět jakékoli vlastní úkoly a vytváření sestav – může být zvolena.

## <a name="see-also"></a>Viz také:

- [Základní programování WCF](../basic-wcf-programming.md)
