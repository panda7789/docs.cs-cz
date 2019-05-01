---
title: Šíření ID aktivity
ms.date: 03/30/2017
ms.assetid: cd1c1ae5-cc8a-4f51-90c9-f7b476bcfe70
ms.openlocfilehash: e51970f693d9ca2d2f81bf4efc97969896de4828
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998046"
---
# <a name="activity-id-propagation"></a>Šíření ID aktivity
Šíření se stane, když ServiceModel aktivity sledování je povoleno (ServiceModel šíření) nebo jsou zakázaná (šíření aktivity uživatele-uživatel).  
  
## <a name="servicemodel-activity-tracing-is-enabled"></a>Je povoleno trasování činnosti ServiceModel  
 Pokud je povolené ServiceModel ActivityTracing, dochází k šíření mezi ProcessAction aktivity.  
  
### <a name="server"></a>Server  
 Když `propagateActivity` atribut je nastaven na `true` na klienta a serveru, ID `ProcessAction` aktivity na serveru je stejný jako ID v rozšíří `ActivityId` záhlaví zprávy.  
  
 Pokud ne `ActivityId` záhlaví je zpráva (to znamená, `propagateActivity` = `false` na straně klienta), nebo když `propagateActivity` = `false` na serveru, na serveru vytvoří nové ID aktivity.  
  
### <a name="client"></a>Klient  
 Pokud klient je synchronně jeden zřetězený, klient ignoruje jakékoli nastavení `propagateActivity` na klienta nebo serveru. Místo toho se v aktivitu žádosti o zpracovává odpověď. Pokud je klient synchronní nebo asynchronní s více vlákny, `propagateActivity` = `true` v klientovi a není identifikační záhlaví činnosti zpráva odeslaná server, klient načte ID aktivity ze zprávy a přenese Aktivitu procesu akce, která obsahuje ID rozšíří aktivity. Klient se v opačném případě přenáší z aktivity zpracovat zprávu novou aktivitu procesu akce. K tomuto navíc přenosu novou aktivitu akce. proces se provádí pro zajištění konzistence. Uvnitř této aktivity klient získá ID aktivity BeginCall činnosti z kontextu místního vlákna při přidělení vlákno pro zpracování zpráv odpovědí. Pak přenese na počáteční aktivitu procesu akce.  
  
 Pokud klient není duplexní, klient funguje jako server na příjem zprávy.  
  
### <a name="propagation-in-fault-messages"></a>Šíření chybové zprávy  
 Není žádný rozdíl v zpracování platný a chybové zprávy. Pokud `propagateActivity` = `true`, ID aktivity, které jsou přidány do záhlaví zprávy protokolu SOAP selhání je stejný jako okolí aktivity.  
  
## <a name="servicemodel-activity-tracing-is-disabled"></a>ServiceModel aktivity trasování je zakázáno.  
 Pokud ServiceModel ActivityTracing je zakázaná, dojde k šíření mezi aktivitami kód uživatele přímo bez nutnosti kontaktovat ServiceModel aktivity. ID uživatelské aktivity je také šířena přes identifikační záhlaví činnosti zprávy.  
  
 Pokud `propagateActivity` = `true` a `ActivityTracing` = `off` pro trasovacího posluchače ServiceModel (bez ohledu na to, zda je povoleno trasování na ServiceModel), následující provádělo na klienta nebo serveru:  
  
- Na žádost o operaci nebo odeslání odpovědi ID aktivity v protokolu TLS rozšířena z uživatelského kódu, dokud je vytvořen zprávu. Identifikační záhlaví činnosti je také vloží do zprávy před odesláním.  
  
- Na přijetí požadavku a příjem odpovědí, ID aktivity získaných záhlaví zprávy, jakmile je vytvořen objekt přijaté zprávy. ID aktivity v protokolu TLS se šíří jako zpráva zmizí z oboru, dokud nebude dosaženo uživatelského kódu.  
  
 Tyto akce zaručit, že uživatel trasování se objeví do aktivity, pokud propagace je zapnutá. Vytváří, ale žádná záruka na ServiceModel trasování. Trasování ServiceModel dojde v aktivitě s kódem uživatele, pouze v případě, že zpracování těchto trasování je spuštěn ve stejném vlákně, ve kterém byl nastaven kód aktivity uživatelů.  
  
 Obecně platí může být dodržen ServiceModel trasování na následujících místech:  
  
- Pokud ServiceModel trasování je zakázáno, všechna emitovaný trasování zobrazit v uživatelských aktivit. Pokud šíření je povoleno na serveru a klienta, trasování bude do stejné aktivity.  
  
- Pokud je povoleno trasování ServiceModel, ale ActivityTracing je zakázaná, zobrazí trasování uživatele do aktivity, pokud šíření je povolena na obou koncích. ServiceModel trasování se zobrazí v aktivitě 0000 výchozí, pokud se objeví ve stejném vlákně jako zpracování kódu uživatele, kde aktivity je zpočátku nastavený.  
  
- Pokud je povoleno trasování ServiceModel i ActivityTracing, trasování uživatel zobrazí v uživatelské aktivity a ServiceModel trasování zobrazí v definované ServiceModel aktivity. Šíření se odehrává na úrovni ServiceModel.
