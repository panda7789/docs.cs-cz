---
title: Synchronní scénáře využívající HTTP, TCP nebo pojmenované kanály
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: 11a5d8f43d12d35728c65c7a60ad8a4fa2fc1b3a
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810171"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a>Synchronní scénáře využívající HTTP, TCP nebo pojmenované kanály
Toto téma popisuje aktivity a přenosy pro různé synchronní požadavek nebo odpověď scénáře s jedním podprocesem klienta, pomocí protokolu HTTP, TCP nebo pojmenovaného kanálu. V tématu [asynchronní scénáře použití HTTP, TCP nebo pojmenované kanály](../../../../../docs/framework/wcf/diagnostics/tracing/asynchronous-scenarios-using-http-tcp-or-named-pipe.md) Další informace o Vícevláknová požadavky.  
  
## <a name="synchronous-requestreply-without-errors"></a>Synchronní požadavek nebo odpověď bez chyb  
 Tato část popisuje aktivity a přenosy pro scénář platný synchronní požadavek nebo odpověď s jedním podprocesem klienta.  
  
### <a name="client"></a>Klient  
  
#### <a name="establishing-communication-with-service-endpoint"></a>Navazování komunikace se koncový bod služby  
 Klient je vytvořená a otevřít. Pro každý z těchto kroků vedlejším aktivity (A) přenesen na "Vytvořit klienta" (B) a "Otevřete klienta" (C) aktivitu v uvedeném pořadí. Pro každou aktivitu přenášení na vedlejším aktivity je pozastaven, dokud nedojde k převodu zpět, tedy dokud ServiceModel kód se spustí.  
  
#### <a name="making-a-request-to-service-endpoint"></a>Vytváření požadavku na koncový bod služby  
 Vedlejším aktivity je převede na aktivitu "ProcessAction" (D). V rámci této aktivity je odeslána zpráva požadavku a obdrží zprávu odpovědi. Aktivity skončí, když řízení vrátí do uživatelského kódu. Protože se jedná o žádost o synchronní, vedlejším aktivity pozastaví, dokud vrátí ovládací prvek.  
  
#### <a name="closing-communication-with-service-endpoint"></a>Zavřením komunikaci s koncovým bodem služby  
 Aktivity uzavření klienta (I) je vytvořen z vedlejším aktivity. Toto je stejný jako nové a otevřete.  
  
### <a name="server"></a>Server  
  
#### <a name="setting-up-a-service-host"></a>Nastavení hostitele služby  
 ServiceHost nové a otevřete aktivity (N a O) jsou vytvořeny z vedlejším aktivity (M).  
  
 Otevření ServiceHost pro každý naslouchací proces se vytvoří naslouchací proces aktivity (P). Aktivita naslouchací proces čeká na přijímat a zpracovávat data.  
  
#### <a name="receiving-data-on-the-wire"></a>Přijetí dat v drátové síti  
 Když data dorazí v drátové síti, vytvoří se aktivita "ReceiveBytes" Pokud již neexistuje (Q) ke zpracování přijatých dat. Tuto aktivitu můžete znovu použít pro více zpráv v rámci připojení a fronty.  
  
 ReceiveBytes aktivity spouští aktivitu ProcessMessage (R), pokud má dostatek dat na formuláři Akce zprávu protokolu SOAP.  
  
 V aktivitě R jsou zpracovávány záhlaví zprávy a bude ověřen hlavičku aktivity. Pokud tuto hlavičku je k dispozici, ID aktivity nastavená na aktivity ProcessAction; jinak se vytvoří nové ID.  
  
 Vytvoření aktivity ProcessAction (S) a přenášení na při volání je zpracovat. Tato aktivita končí po dokončení veškeré zpracování související s příchozí zprávy, včetně spuštění uživatelského kódu (T) a odešle zprávu odpovědi, pokud je k dispozici.  
  
#### <a name="closing-a-service-host"></a>Ukončování hostitele služby  
 Hostiteli služby zavřít aktivity (Z) je vytvořený z vedlejším aktivity.  
  
 ![Synchronní scénáře využívající HTTP&#47;TCP&#47; pojmenovaných kanálů](../../../../../docs/framework/wcf/diagnostics/tracing/media/sync.gif "synchronizace")  
  
 V \<A: název >, `A` je symbol zástupce, který popisuje aktivitu v předchozí textu a v tabulce 3. `Name` je zkrácený název aktivity.  
  
 Pokud `propagateActivity` = `true`, proces akce na klientovi a služby mají stejné ID aktivity.  
  
## <a name="synchronous-requestreply-with-errors"></a>Synchronní požadavek nebo odpověď s chybami  
 Jediným rozdílem s předchozím scénáři je, že zprávu o chybě protokolu SOAP se vrátí jako zprávu odpovědi. Pokud `propagateActivity` = `true`, ID aktivity zprávy požadavku se přidá do selhání zprávu protokolu SOAP.  
  
## <a name="synchronous-one-way-without-errors"></a>Synchronní jednosměrný bez chyb  
 První scénář jediným rozdílem je, že na server je vrácena žádná zpráva. Pro protokoly založené na protokolu HTTP, stav (platné nebo chyba) je stále vrácen do klienta. Je to proto, že je protokol pouze s sémantiku požadavků a odpovědí, který je součástí v zásobníku protokolů WCF HTTP. Protože zpracování protokolu TCP je skryta WCF, potvrzení je odeslán do klienta.  
  
## <a name="synchronous-one-way-with-errors"></a>Synchronní jednosměrný s chybami  
 Pokud dojde k chybě při zpracování zprávy (Q nebo novější), žádná oznámení je vrácen do klienta. Toto je stejný jako scénář "Synchronní One-Way bez chyby". Jednosměrný situaci byste neměli používat, pokud chcete zobrazit chybová zpráva.  
  
## <a name="duplex"></a>Duplex  
 Rozdíl oproti předchozím scénáře je, že klient funguje jako služba, ve kterém se vytvoří ReceiveBytes a ProcessMessage aktivity, podobně jako asynchronní scénáře.
