---
title: Synchronní scénáře využívající HTTP, TCP nebo pojmenované kanály
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: 662067fc5564c9421ce24b28b291d06690b129ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589181"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a>Synchronní scénáře využívající HTTP, TCP nebo pojmenované kanály
Toto téma popisuje aktivity a převody různých scénářů synchronních požadavků a odpovědí s jedním vláknovým klientem pomocí protokolu HTTP, TCP nebo pojmenovaného kanálu. Další informace o požadavcích s více vlákny najdete v tématu [asynchronní scénáře pomocí protokolu HTTP, TCP nebo pojmenovaného kanálu](asynchronous-scenarios-using-http-tcp-or-named-pipe.md) .  
  
## <a name="synchronous-requestreply-without-errors"></a>Synchronní požadavek nebo odpověď bez chyb  
 Tato část popisuje aktivity a přenosy pro platný scénář synchronních požadavků a odpovědí s jedním vláknovým klientem.  
  
### <a name="client"></a>Klient  
  
#### <a name="establishing-communication-with-service-endpoint"></a>Navazování komunikace s koncovým bodem služby  
 Klient je vytvořen a otevřen. Pro každý z těchto kroků se okolní aktivita (A) přenáší do aktivity "konstrukce klienta" (B) a "otevřít klienta" (C). U každé aktivity přenesené do se okolní aktivita pozastaví, dokud nedojde k přenosu zpět, tedy až po provedení kódu ServiceModel.  
  
#### <a name="making-a-request-to-service-endpoint"></a>Vytvoření žádosti na koncový bod služby  
 Okolní aktivita se přenáší na aktivitu "ProcessAction (D)". V rámci této aktivity je odeslána zpráva požadavku a přijata zpráva odpovědi. Aktivita končí, když se ovládací prvek vrátí do uživatelského kódu. Vzhledem k tomu, že se jedná o synchronní požadavek, okolní aktivity se pozastaví, dokud řízení nevrátí.  
  
#### <a name="closing-communication-with-service-endpoint"></a>Uzavírání komunikace s koncovým bodem služby  
 Aktivita ukončení klienta (I) se vytvoří z okolní aktivity. To je stejné jako nové a otevřené.  
  
### <a name="server"></a>Server  
  
#### <a name="setting-up-a-service-host"></a>Nastavení hostitele služby  
 Nové a otevřené aktivity hostitele ServiceHost (N a O) se vytvářejí z okolní aktivity (M).  
  
 Aktivita naslouchacího procesu (P) je vytvořena z otevření třídy ServiceHost pro každý naslouchací proces. Aktivita naslouchacího procesu čeká na příjem a zpracování dat.  
  
#### <a name="receiving-data-on-the-wire"></a>Příjem dat na lince  
 Když data dorazí na kabel, vytvoří se aktivita ReceiveBytes, pokud ještě neexistuje (Q) pro zpracování přijatých dat. Tuto aktivitu lze znovu použít pro více zpráv v rámci připojení nebo fronty.  
  
 Aktivita ReceiveBytes spustí aktivitu ProcessMessage (R), pokud má dostatek dat pro vytvoření zprávy akce SOAP.  
  
 V aktivitě R se zpracují záhlaví zpráv a ověří se záhlaví activityID. Pokud je tato hlavička k dispozici, ID aktivity je nastaveno na aktivitu ProcessAction; v opačném případě se vytvoří nové ID.  
  
 Aktivity ProcessAction se vytváří a přenášejí do, při zpracování volání. Tato aktivita skončí po dokončení veškerého zpracování souvisejícího s příchozími zprávami, včetně provádění kódu uživatele (T) a odeslání zprávy s odpovědí, pokud je to možné.  
  
#### <a name="closing-a-service-host"></a>Uzavírání hostitele služby  
 Aktivita ukončení hostitele ServiceHost (Z) se vytvoří z okolní aktivity.  
  
 ![Diagram znázorňující synchronní scénáře: HTTP, TCP nebo pojmenované kanály.](./media/synchronous-scenarios-using-http-tcp-or-named-pipe/synchronous-scenario-http-tcp-named-pipes.gif)  
  
 V \<A: name> `A` je symbol zástupce, který popisuje aktivitu v předchozím textu a v tabulce 3. `Name`je zkrácený název aktivity.  
  
 V případě `propagateActivity` = `true` , že akce procesu u klienta i služby má stejné ID aktivity.  
  
## <a name="synchronous-requestreply-with-errors"></a>Synchronní požadavek/odpověď s chybami  
 Jediným rozdílem v předchozím scénáři je, že se jako zpráva odpovědi vrátí zpráva o chybě protokolu SOAP. Pokud `propagateActivity` = `true` je ID aktivity zprávy požadavku přidáno do zprávy o chybě protokolu SOAP.  
  
## <a name="synchronous-one-way-without-errors"></a>Synchronní jednosměrné bez chyb  
 Jediným rozdílem s prvním scénářem je, že na server se nevrátí žádná zpráva. U protokolů založených na protokolu HTTP je stav (platný nebo chyba) stále vrácen klientovi. Důvodem je to, že HTTP je jediným protokolem se sémantikou požadavek-odpověď, která je součástí zásobníku protokolu WCF. Vzhledem k tomu, že zpracování protokolu TCP je v rámci služby WCF skryté, není klientovi odesíláno žádné potvrzení.  
  
## <a name="synchronous-one-way-with-errors"></a>Synchronní jednosměrné s chybami  
 Pokud při zpracování zprávy dojde k chybě (Q nebo mimo), nevrátí se klientovi žádné oznámení. To je stejné jako scénář "synchronní jednosměrné bez chyb". Pokud chcete zobrazit chybovou zprávu, neměli byste používat jednosměrný scénář.  
  
## <a name="duplex"></a>Duplex  
 Rozdíl s předchozími scénáři je, že klient funguje jako služba, ve které vytvoří aktivity ReceiveBytes a ProcessMessage, podobně jako asynchronní scénáře.
