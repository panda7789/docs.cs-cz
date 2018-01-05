---
title: "Asynchronní scénáře použití HTTP, TCP nebo pojmenovaného kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76c4c225b333af6d376fa409a05ea5727ede6e8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>Asynchronní scénáře použití HTTP, TCP nebo pojmenovaného kanálu
Toto téma popisuje aktivity a přenosy pro různé Asynchronní požadavek nebo odpověď scénáře s více vlákny požadavky pomocí protokolu HTTP, TCP nebo pojmenovaného kanálu.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Asynchronní požadavek nebo odpověď bez chyb  
 Tato část popisuje aktivity a přenosy Asynchronní požadavek nebo odpověď scénář s více vlákny klienty.  
  
 Volající aktivity ukončí při `beginCall` vrátí, a `endCall` vrátí. Pokud je volána zpětné volání, vrátí zpětné volání.  
  
 Ukončí volané aktivity, kdy `beginCall` vrátí, `endCall` vrátí, nebo když zpětné volání vrátí, pokud byla volána z aktivity.  
  
### <a name="asynchronous-client-without-callback"></a>Asynchronní klienta bez zpětného volání  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>Bylo povoleno šíření na obou stranách, pomocí protokolu HTTP  
 ![Asynchronní scénáře](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")  
  
 Obrázek 1. Asynchronní klienta, bez zpětného volání, `propagateActivity` = `true` na obou stranách HTTP  
  
 Pokud `propagateActivity` = `true`, ProcessMessage označuje, která ProcessAction aktivita se má přenést do.  
  
 Pro scénáře založené na protokolu HTTP, je vyvolána ReceiveBytes na první zprávu k odeslání a pro dobu životnosti požadavku existuje.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>Propagace je zakázána na buď stranách, pomocí protokolu HTTP  
 Pokud `propagateActivity` = `false` na obou stranách ProcessMessage neindikuje která ProcessAction aktivita se má přenést do. Proto nové dočasné ProcessAction aktivitu se nové ID vyvolání. Pokud požadavek na ServiceModel kód je nalezena shoda asynchronní odpovědi, ID aktivity lze načíst z lokální kontext. Skutečné aktivity ProcessAction lze přesunout do s ID tohoto.  
  
 ![Asynchronní scénáře použití HTTP &#47; TCP &#47; Pojmenovaný kanál](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")  
  
 Obrázek 2. Asynchronní klienta, bez zpětného volání, `propagateActivity` = `false` na obou stranách HTTP  
  
 Pro scénáře založené na protokolu HTTP, je vyvolána ReceiveBytes na první zprávu k odeslání a pro dobu životnosti požadavku existuje.  
  
 Vytvoření procesu akce aktivity na asynchronní klienta při `propagateActivity` = `false` na volající nebo volaný a zprávu odpovědi nezahrnuje hlavičku akce.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>Bylo povoleno šíření na obou stranách, pomocí TCP nebo pojmenované kanály  
 ![Asynchronní scénáře použití HTTP &#47; TCP &#47; Pojmenovaný kanál](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")  
  
 Obrázek 3. Asynchronní klienta, bez zpětného volání, `propagateActivity` = `true` na obou stranách pojmenovaný kanál/TCP  
  
 Pro scénář založený na TCP nebo pojmenované kanály ReceiveBytes je volána, když klient je otevřena a existuje pro životnost připojení.  
  
 Podobně jako obrázek 1, pokud `propagateActivity` = `true`, ProcessMessage označuje, která ProcessAction aktivita se má přenést do.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>Propagace je zakázána na buď stranách, pomocí TCP nebo pojmenované kanály  
 Pro scénář založený na TCP nebo pojmenované kanály ReceiveBytes je volána, když klient je otevřena a existuje pro životnost připojení.  
  
 Podobně jako Fig.2, pokud `propagateActivity` = `false` na obou stranách ProcessMessage neindikuje která ProcessAction aktivita se má přenést do. Proto nové dočasné ProcessAction aktivitu se nové ID vyvolání. Pokud požadavek na ServiceModel kód je nalezena shoda asynchronní odpovědi, ID aktivity lze načíst z lokální kontext. Skutečné aktivity ProcessAction lze přesunout do s ID tohoto.  
  
 ![Asynchronní scénáře použití HTTP &#47; TCP &#47; Pojmenované kanály](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")  
  
 Obrázek 4. Asynchronní klienta, bez zpětného volání, `propagateActivity` = `false` na obou stranách pojmenovaný kanál/TCP  
  
### <a name="asynchronous-client-with-callback"></a>Asynchronní klienta s zpětného volání  
 Tento scénář přidá aktivity G a A', pro zpětné volání a `endCall`a jejich přenosy vstup/výstup.  
  
 V této části ukážeme pouze pomocí protokolu HTTP s `propragateActivity` = `true`. Však další aktivity a přenosy se rovněž vztahují na ostatních případech (tedy `propagateActivity` = `false`, pomocí TCP nebo pojmenované kanály).  
  
 Zpětné volání vytvoří novou aktivitu (G), když klient zavolá kód uživatele upozornit, že výsledky jsou připraveny. Uživatelský kód pak zavolá `endCall` v rámci zpětného volání (jak je znázorněno na obrázku 5), nebo mimo zpětného volání (obrázek 6). Protože není známo, která aktivita uživatele `endCall` je volána, tato aktivita označené `A’`. Je možné, že A, může být stejný jako nebo liší od A.  
  
 ![Asynchronní scénáře](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")  
  
 Obrázek 5. Asynchronní klienta se zpětné volání, `endCall` v zpětného volání  
  
 ![Asynchronní scénáře](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")  
  
 Obrázek 6. Asynchronní klienta se zpětné volání, `endCall` mimo zpětného volání  
  
### <a name="asynchronous-server-with-callback"></a>Asynchronní Server s zpětného volání  
 ![Asynchronní scénáře použití HTTP &#47; TCP &#47; S názvem & č. 45; Kanál](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")  
  
 Na obrázku 7. Asynchronní server s zpětného volání  
  
 Kanál zásobníku volání zpět klientovi na příjem zpráv: trasování pro zpracování jsou vygenerované v aktivitě ProcessRequest sám sebe.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Asynchronní požadavek nebo odpověď s chybami  
 Přijme chybový zpráva chyby během `endCall`. Jinak aktivity a přenosy jsou podobná předchozí scénáře.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Asynchronní jednosměrný s nebo bez chyby  
 Žádná odpověď nebo selhání je vrácen do klienta.
