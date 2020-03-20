---
title: Asynchronní scénáře použití HTTP, TCP nebo pojmenovaného kanálu
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 6ae96c0aac5010adf37eb78ed57d1549885ece58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185788"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>Asynchronní scénáře použití HTTP, TCP nebo pojmenovaného kanálu
Toto téma popisuje aktivity a přenosy pro různé scénáře asynchronní požadavek/odpověď s vícevláknové požadavky pomocí HTTP, TCP nebo pojmenované kanálu.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Asynchronní požadavek/odpověď bez chyb  
 Tato část popisuje aktivity a přenosy pro scénář asynchronní požadavek/odpověď s vícevláknovými klienty.  
  
 Volající aktivita ukončí, `beginCall` když `endCall` vrátí a vrátí. Pokud je voláno zpětné volání, vrátí zpětné volání.  
  
 Volaná aktivita `beginCall` končí, když vrátí, `endCall` vrátí nebo když zpětné volání vrátí, pokud byla volána z této aktivity.  
  
### <a name="asynchronous-client-without-callback"></a>Asynchronní klient bez zpětného volání  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>Šíření je povoleno na obou stranách pomocí protokolu HTTP  
 ![Asynchronní klient bez zpětného volání, kde je propagateActivity nastavena na hodnotu true na obou stranách.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 If `propagateActivity=true`, ProcessMessage označuje, které ProcessAction aktivity k přenosu.  
  
 Pro scénáře založené na protokolu HTTP ReceiveBytes je vyvolána na první zprávu odeslat a existuje po dobu životnosti požadavku.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>Šíření je zakázáno na obou stranách pomocí protokolu HTTP  
 Pokud `propagateActivity=false` na obou stranách ProcessMessage neoznačuje, které ProcessAction aktivity k přenosu. Proto je vyvolána nová dočasná aktivita ProcessAction s novým ID. Pokud je asynchronní odpověď spárována s požadavkem v kódu ServiceModel, id aktivity lze načíst z místního kontextu. Skutečná aktivita ProcessAction může být převedena na s tímto ID.  
  
 ![Asynchronní klient bez zpětného volání, kde je propagateActivity nastavena na false na obou stranách.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 Pro scénáře založené na protokolu HTTP ReceiveBytes je vyvolána na první zprávu odeslat a existuje po dobu životnosti požadavku.  
  
 Aktivita akce procesu je vytvořena na `propagateActivity=false` asynchronního klienta, když na volajícího nebo volaný, a když zpráva odpovědi neobsahuje hlavičku akce.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>Šíření je povoleno na obou stranách pomocí protokolu TCP nebo pojmenovaného kanálu  
 ![Asynchronní klient bez zpětného volání, kde je propagateActivity nastavena na hodnotu true na obou stranách a pojmenovaný kanál/TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 Pro scénář založený na pojmenovaném kanálu nebo TCP receivebytes je vyvolána při otevření klienta a existuje po dobu životnosti připojení.  
  
 Podobně jako první obrázek, if `propagateActivity=true`, ProcessMessage označuje, které ProcessAction aktivity k přenosu.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>Šíření je zakázáno na obou stranách pomocí protokolu TCP nebo pojmenovaného kanálu.  
 Pro scénář založený na pojmenovaném kanálu nebo TCP receivebytes je vyvolána při otevření klienta a existuje po dobu životnosti připojení.  
  
 Podobně jako druhý obrázek, pokud `propagateActivity=false` na obou stranách ProcessMessage neoznačuje, které ProcessAction aktivity k přenosu. Proto je vyvolána nová dočasná aktivita ProcessAction s novým ID. Pokud je asynchronní odpověď spárována s požadavkem v kódu ServiceModel, id aktivity lze načíst z místního kontextu. Skutečná aktivita ProcessAction může být převedena na s tímto ID.  
  
 ![Asynchronní klient bez zpětného volání, kde je propagateActivity nastavena na false na obou stranách a pojmenované kanálu/TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a>Asynchronní klient s zpětným voláním  
 Tento scénář přidá aktivity G a A', pro zpětné volání a `endCall`, a jejich převody dovnitř / ven.  
  
 Tato část ukazuje pouze `propagateActivity` = `true`pomocí protokolu HTTP s . Další aktivity a převody se však vztahují `propagateActivity` = `false`také na ostatní případy (tj. pomocí protokolu TCP nebo pojmenovaného kanálu).  
  
 Zpětné volání vytvoří novou aktivitu (G), když klient volá uživatelský kód upozornit, že výsledky jsou připraveny. Uživatelský kód `endCall` pak volá v rámci zpětného volání (jak je znázorněno na obrázku 5) nebo mimo zpětné volání (obrázek 6). Vzhledem k tomu, `endCall` že není známo, ze které `A’`aktivity uživatele je volána, je tato aktivita označena . Je možné, že A' může být totožný nebo odlišný od A.  
  
 ![Zobrazuje asynchronního klienta s zpětným voláním, endcall v zpětném volání.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![Zobrazuje asynchronního klienta s zpětným voláním, endcall mimo zpětné volání.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a>Asynchronní server s zpětným voláním  
 ![Zobrazuje asynchronní server s zpětným voláním.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 Zásobník kanálu volá zpět klienta na přijetí zprávy: trasování pro toto zpracování jsou emitovány v samotné aktivitě ProcessRequest.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Asynchronní požadavek/odpověď s chybami  
 Během souboru jsou `endCall`přijímány chyby chyb V opačném případě aktivity a převody jsou podobné předchozím scénářům.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Asynchronní jednosměrný s chybami nebo bez chyb  
 Klientovi není vrácena žádná odpověď ani chyba.
