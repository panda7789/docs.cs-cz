---
title: Asynchronní scénáře použití HTTP, TCP nebo pojmenovaného kanálu
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: d08f70186a59b8717c4441167ee720ba1c20b9dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998247"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>Asynchronní scénáře použití HTTP, TCP nebo pojmenovaného kanálu
Toto téma popisuje činnosti a přenosy pro jiné Asynchronní požadavek/odpověď scénáře s více vlákny požadavky pomocí protokolu HTTP, TCP, nebo pojmenovaného kanálu.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Asynchronní požadavek/odpověď bez chyb  
 Tato část popisuje aktivity a přenosy pro scénáři Asynchronní požadavek/odpověď s klienty s více vlákny.  
  
 Aktivita volající skončí, když `beginCall` vrací, a `endCall` vrátí. Pokud zpětné volání je volána, zpětné volání vrátí.  
  
 Volané aktivity skončí, když `beginCall` návratu `endCall` vrátí, nebo když zpětného volání vrátí, pokud byla volána z aktivity.  
  
### <a name="asynchronous-client-without-callback"></a>Asynchronní klienta bez zpětného volání  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>Šíření je povoleno na obou stranách pomocí protokolu HTTP  
 ![Asynchronní scénáře](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")  
  
 Obrázek 1. Asynchronní klienta, bez zpětného volání `propagateActivity` = `true` na obou stranách HTTP  
  
 Pokud `propagateActivity` = `true`, ProcessMessage indikuje aktivitu které ProcessAction přenést do.  
  
 Pro scénáře založené na protokolu HTTP, je vyvolána ReceiveBytes na první zprávu odeslat a existuje po dobu platnosti požadavku.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>Šíření je zakázáno na buď stranách, pomocí protokolu HTTP  
 Pokud `propagateActivity` = `false` na obou stranách ProcessMessage neindikuje, které aktivita ProcessAction přenést do. Proto je vyvolána nová dočasná ProcessAction aktivita s novým ID. Pokud asynchronní odpověď je nalezena shoda, požadavek na ServiceModel kódu, ID aktivity mohou být načteny z místního kontextu. Skutečné ProcessAction aktivity lze přenést do tohoto ID.  
  
 ![Asynchronní scénáře využívající HTTP&#47;TCP&#47;pojmenovaného kanálu](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")  
  
 Obrázek 2. Asynchronní klienta, bez zpětného volání `propagateActivity` = `false` na obou stranách HTTP  
  
 Pro scénáře založené na protokolu HTTP, je vyvolána ReceiveBytes na první zprávu odeslat a existuje po dobu platnosti požadavku.  
  
 Vytvoření akce proces aktivity na asynchronního klientského při `propagateActivity` = `false` volající nebo volaný a zprávy s odpovědí neobsahuje hlavičku akce.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>Šíření je povoleno na obou stranách pomocí protokolu TCP nebo pojmenovaného kanálu  
 ![Asynchronní scénáře využívající HTTP&#47;TCP&#47;pojmenovaného kanálu](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")  
  
 Obr. 3. Asynchronní klienta, bez zpětného volání `propagateActivity` = `true` na obou stranách pojmenovaného kanálu/TCP  
  
 Pro scénář založené na TCP nebo pojmenované kanály ReceiveBytes je voláno, když klient je otevřený a existuje po dobu životnosti připojení.  
  
 Podobně jako na obrázku 1, pokud `propagateActivity` = `true`, ProcessMessage indikuje aktivitu které ProcessAction přenést do.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>Šíření je zakázáno na buď stranách, TCP nebo pojmenovaného kanálu  
 Pro scénář založené na TCP nebo pojmenované kanály ReceiveBytes je voláno, když klient je otevřený a existuje po dobu životnosti připojení.  
  
 Podobně jako Fig.2, pokud `propagateActivity` = `false` na obou stranách ProcessMessage neindikuje, které aktivita ProcessAction přenést do. Proto je vyvolána nová dočasná ProcessAction aktivita s novým ID. Pokud asynchronní odpověď je nalezena shoda, požadavek na ServiceModel kódu, ID aktivity mohou být načteny z místního kontextu. Skutečné ProcessAction aktivity lze přenést do tohoto ID.  
  
 ![Asynchronní scénáře využívající HTTP&#47;TCP&#47; pojmenovaných kanálů](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")  
  
 Obrázek 4. Asynchronní klienta, bez zpětného volání `propagateActivity` = `false` na obou stranách pojmenovaného kanálu/TCP  
  
### <a name="asynchronous-client-with-callback"></a>Asynchronní zpětné volání klienta  
 Tento scénář přidá aktivity G a A ", zpětného volání a `endCall`a jejich přenosy vstup a výstup.  
  
 V této části ukážeme pouze pomocí protokolu HTTP s `propragateActivity` = `true`. Však další aktivity a přenosy platí také pro další případy (to znamená `propagateActivity` = `false`, TCP nebo pojmenované kanály).  
  
 Zpětné volání vytvoří novou aktivitu (G), když klient volá kód uživatele upozornit, že jsou výsledky připraveny. Uživatelský kód zavolá `endCall` v rámci zpětného volání (jak je znázorněno na obrázku 5) nebo mimo zpětného volání (obrázek 6). Protože není známo, které aktivity uživatelů `endCall` je volána z, je tato aktivita označená `A’`. Je možné, A "může být stejný jako nebo liší od A.  
  
 ![Asynchronní scénáře](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")  
  
 Obr. 5. Asynchronní klienta zpětné volání, `endCall` ve zpětném volání  
  
 ![Asynchronní scénáře](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")  
  
 Obrázek 6. Asynchronní klienta zpětné volání, `endCall` mimo zpětného volání  
  
### <a name="asynchronous-server-with-callback"></a>Asynchronní serveru pomocí zpětného volání  
 ![Asynchronní scénáře využívající HTTP&#47;TCP&#47; pojmenované&#45;kanálu](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")  
  
 Obrázek 7. Asynchronního serverového pomocí zpětného volání  
  
 Kanál zásobníku volání zpět klienta na přijetí zprávy: trasování pro zpracování jsou zaznamenávány do aktivity ProcessRequest samotný.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Asynchronní požadavek/odpověď s chybami  
 Zpráva chyby selhání přijme během `endCall`. V opačném případě aktivity a přenosy jsou podobné předchozího scénáře.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Asynchronní jednosměrné s nebo bez chyb  
 Žádná odpověď nebo selhání je vrácen do klienta.
