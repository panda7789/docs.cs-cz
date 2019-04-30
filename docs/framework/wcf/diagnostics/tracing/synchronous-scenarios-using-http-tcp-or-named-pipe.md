---
title: Synchronní scénáře využívající HTTP, TCP nebo pojmenované kanály
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: 28e612b190f4993e1ce7da0d1083c4e55f827d4a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784860"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a>Synchronní scénáře využívající HTTP, TCP nebo pojmenované kanály
Toto téma popisuje aktivity a přenosy pro různé synchronní požadavku/odpovědi scénáře pomocí klienta s jedním vláknem, pomocí protokolu HTTP, TCP nebo pojmenovaného kanálu. Zobrazit [asynchronní scénáře využívající HTTP, TCP nebo pojmenované kanály](../../../../../docs/framework/wcf/diagnostics/tracing/asynchronous-scenarios-using-http-tcp-or-named-pipe.md) Další informace o vícevláknových požadavky.  
  
## <a name="synchronous-requestreply-without-errors"></a>Synchronní požadavku/odpovědi bez chyb  
 Tato část popisuje aktivity a přenosy pro scénář platný synchronní požadavek/odpověď s klientem s jedním vláknem.  
  
### <a name="client"></a>Klient  
  
#### <a name="establishing-communication-with-service-endpoint"></a>Navázání komunikace s koncový bod služby  
 Klient je vytvořen a otevřen. Pro každý z těchto kroků okolí aktivity (A) je předány "Vytvoření klienta" (B) a "Otevřít klienta" (C) aktivitu v uvedeném pořadí. Pro každou aktivitu přenášejí do okolí aktivity je pozastaveno, dokud se nepřenášejí zpět, to znamená, dokud je provedena ServiceModel kódu.  
  
#### <a name="making-a-request-to-service-endpoint"></a>Požadavku na koncový bod služby  
 Ambientní aktivity se přenesou do činnosti "ProcessAction" (D). V rámci této aktivity je žádost odeslána zpráva a obdrží zprávu odpovědi. Aktivita končí, když ovládací prvek se vrátí do uživatelského kódu. Protože to je požadavek na synchronní, okolí aktivity pozastaví, dokud se ovládací prvek vrátí.  
  
#### <a name="closing-communication-with-service-endpoint"></a>Zavření komunikaci s koncovým bodem služby  
 Zavřít aktivitu klienta, (I) se vytvoří v okolí aktivity. To je stejný jako nový a otevřete.  
  
### <a name="server"></a>Server  
  
#### <a name="setting-up-a-service-host"></a>Nastavení hostitele služby  
 V rámci ambientní aktivity (M) jsou vytvořeny ServiceHost nový a otevřete aktivity (N a O).  
  
 Otevírání ServiceHost pro každý naslouchací proces vytvoření naslouchacího procesu aktivity (P). Aktivita naslouchací proces čeká na příjem a zpracování dat.  
  
#### <a name="receiving-data-on-the-wire"></a>Příjem dat na lince  
 Po přijetí dat na lince, vytvoření aktivity "ReceiveBytes" Pokud již neexistuje (Q) ke zpracování přijatá data. Tuto aktivitu lze znovu použít pro více zpráv v rámci připojení nebo fronty.  
  
 Aktivita ReceiveBytes spustí aktivitu ProcessMessage (R), pokud má dostatek dat k vytvoření zprávy akce SOAP.  
  
 V aktivitě R se zpracují záhlaví zpráv a hlavičku activityID je ověřený. Pokud toto záhlaví je k dispozici, ID aktivity nastavená na aktivitu ProcessAction; v opačném případě se vytvoří nové ID.  
  
 Vytvoření aktivity ProcessAction (S) a přenášejí do, když volání se zpracovává. Tato aktivita končí po dokončení veškeré zpracování související s příchozí zprávy, včetně spouštění uživatelského kódu (T) a odesílá zprávy s odpovědí, pokud je k dispozici.  
  
#### <a name="closing-a-service-host"></a>Zavření hostitele služby  
 Hostitel služby Zavřít aktivitu (Z) se vytvoří v okolí aktivity.  
  
 ![Diagram znázorňující synchronní scénáře: HTTP, TCP nebo pojmenované kanály.](./media/synchronous-scenarios-using-http-tcp-or-named-pipe/synchronous-scenario-http-tcp-named-pipes.gif)  
  
 V \<A: název >, `A` je místní symbol, který popisuje aktivitu v předchozí text a v tabulce 3. `Name` je zkrácený název aktivity.  
  
 Pokud `propagateActivity` = `true`, akce proces na klienta a služby mají stejné ID aktivity.  
  
## <a name="synchronous-requestreply-with-errors"></a>Synchronní požadavek/odpověď s chybami  
 S předchozím scénáři jediným rozdílem je, že se jako odpověď vrátí zprávu o chybě protokolu SOAP. Pokud `propagateActivity` = `true`, ID aktivity požadavku se přidá do chybová zpráva SOAP.  
  
## <a name="synchronous-one-way-without-errors"></a>Synchronní jednosměrné bez chyb  
 První scénář jediným rozdílem je, že žádná zpráva je vrácen do serveru. Pro protokoly založené na protokolu HTTP, stav (platné nebo chyba) je stále vrácen do klienta. Toto je vzhledem k tomu je jediný protokol se sémantikou typu žádost odpověď, který je součástí WCF zásobník protokolu HTTP. Vzhledem k tomu, že zpracování protokolu TCP je skrytá WCF, bez potvrzení posílá do klienta.  
  
## <a name="synchronous-one-way-with-errors"></a>Synchronní jednosměrné s chybami  
 Pokud dojde k chybě při zpracování zprávy (Q nebo novější), žádná oznámení je vrácen do klienta. To je stejný jako scénáře "Synchronních One-Way bez chyb". Jednosměrná scénáři byste neměli používat, pokud chcete zobrazit chybová zpráva.  
  
## <a name="duplex"></a>Duplex  
 Rozdíl oproti předchozím scénáře je, že klient funguje jako služba, ve kterém se vytvoří aktivity ReceiveBytes a ProcessMessage, podobně jako asynchronní scénáře.
