---
title: "Šíření ID aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd1c1ae5-cc8a-4f51-90c9-f7b476bcfe70
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c61087102148688678d868ce25a9cb63315ed65
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="activity-id-propagation"></a>Šíření ID aktivity
Šíření se stane, když ServiceModel aktivity trasování povoleno (ServiceModel šíření) nebo zakázán (rozšíření aktivity uživatel-uživatel).  
  
## <a name="servicemodel-activity-tracing-is-enabled"></a>Je povoleno trasování aktivity ServiceModel  
 Pokud je povoleno ServiceModel ActivityTracing, dochází k šíření mezi ProcessAction aktivity.  
  
### <a name="server"></a>Server  
 Když `propagateActivity` je atribut nastaven na `true` na klientovi a serveru, ID `ProcessAction` aktivity na serveru je stejný jako Identifikátor v šířený `ActivityId` záhlaví zprávy.  
  
 Pokud ne `ActivityId` záhlaví se nachází ve zprávě (tedy `propagateActivity` = `false` na straně klienta), nebo když `propagateActivity` = `false` na serveru, server vygeneruje nové ID aktivity.  
  
### <a name="client"></a>Klient  
 Pokud klient je synchronně jednoho vlákna, klient ignoruje žádné nastavení `propagateActivity` na klienta nebo serveru. Místo toho je odpověď zpracována v aktivitu žádosti. Pokud je klient synchronní nebo asynchronní s více vlákny, `propagateActivity` = `true` v klientovi a je ve zprávě server odesílá hlavičku ID aktivity, klient načte ID aktivity ze zprávy a přenese Zpracovat aktivity akce, který obsahuje ID šířený aktivity. Klient se, jinak hodnota přenáší z aktivitu procesu zprávu novou aktivitu procesu akce. K tomuto navíc přenosu nová aktivita procesu akce se provádí pro konzistence. Uvnitř této aktivity klient načte ID aktivity BeginCall aktivity z kontextu místní vlákno při vlákno přidělení pro zpracování zprávy odpovědi. Pak přenese do počáteční aktivity procesu akce.  
  
 Pokud je klient duplexní, klient funguje jako server na danou zprávu přijala.  
  
### <a name="propagation-in-fault-messages"></a>Šíření v chybové zprávy  
 Není žádný rozdíl ve zpracování platný a chybové zprávy. Pokud `propagateActivity` = `true`, ID aktivity a přidá do hlavičky SOAP selhání zpráv je stejný jako vedlejším aktivity.  
  
## <a name="servicemodel-activity-tracing-is-disabled"></a>Trasování aktivit ServiceModel je zakázána.  
 Pokud ServiceModel ActivityTracing je zakázaná, dojde k šíření mezi aktivitami kód uživatele přímo bez ServiceModel aktivity. Uživatelem definované aktivity ID také šíří prostřednictvím záhlaví zprávy ID aktivity.  
  
 Pokud `propagateActivity` = `true` a `ActivityTracing` = `off` pro naslouchací ServiceModel (bez ohledu na to, jestli je povolené trasování na ServiceModel) následující dojít na straně klienta nebo serveru:  
  
-   Žádost o operaci nebo odeslání odpovědi ID aktivity v TLS rozšířena z uživatelského kódu, dokud je vytvořen zprávu. Hlavičku ID aktivity je rovněž vložen do zprávy před odesláním.  
  
-   Při přijímání požadavku nebo odpovědi přijímání, je ID aktivity načíst z záhlaví zprávy při vytvoření objektu přijaté zprávy. ID aktivity v TLS rozšířena také zpráva zmizí z oboru, dokud nebude dosaženo uživatelského kódu.  
  
 Tyto akce zaručit, že uživatel trasování se zobrazí v je jedna aktivita, pokud propagace je zapnutá. Lze však žádná záruka na ServiceModel trasování. Trasování ServiceModel dojít kód aktivitou uživatele jenom v případě, že zpracování těchto trasování se spustí ve stejném vlákně, kde byl nastaven kód aktivity uživatelů.  
  
 Obecně platí může být dodržen ServiceModel trasování na těchto místech:  
  
-   Pokud ServiceModel trasování je zakázáno, se zobrazí v uživatelské aktivity všech emitovaného trasování. Pokud je povoleno šíření na serveru a klienta, toto trasování bude ve stejné aktivitě.  
  
-   Pokud je povolené trasování ServiceModel, ale je zakázán ActivityTracing, zobrazí trasování uživatele ve stejné aktivitě, pokud je povoleno šíření na obou koncích. Nastávají ve stejném vlákně, v jako zpracování kód uživatele, kde aktivity je zpočátku nastavený v výchozí 0000 aktivita, zobrazen ServiceModel trasování.  
  
-   Pokud jsou povolené trasování ServiceModel a ActivityTracing, trasování uživatele zobrazeny v uživatelské aktivity a ServiceModel trasování zobrazeny v definované ServiceModel aktivity. Šíření se odehrává na úrovni ServiceModel.
