---
title: služby streamování gRPC versus opakující se pole – gRPC pro vývojáře WCF
description: Porovnávání opakujících se polí se službami streamování jako způsob předávání kolekcí dat pomocí gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7dc3c8f5bf2efc304da7d50661ba47db500e67a0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184069"
---
# <a name="grpc-streaming-services-versus-repeated-fields"></a>služby streamování gRPC versus opakující se pole

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

služby gRPC poskytují dva způsoby vrácení datových sad nebo seznamů objektů. Specifikace zprávy vyrovnávací paměti protokolu používá `repeated` klíčové slovo k deklaraci seznamů nebo polí zpráv v rámci jiné zprávy. Specifikace služby gRPC používá `stream` klíčové slovo k deklaraci dlouhotrvajícího trvale běžícího připojení, přes které se odesílá více zpráv, a dá se zpracovat jednotlivě. `stream` Funkci lze také použít pro dlouhotrvající dočasná data, jako jsou oznámení nebo zprávy protokolu, ale tato kapitola bude uvažovat o použití pro vrácení jedné datové sady.

Které byste měli použít, závisí na různých faktorech, jako je celková velikost datové sady, čas potřebný k vytvoření datové sady na konci klienta nebo serveru a na to, zda může příjemce datové sady na něm začít pracovat, jakmile bude k dispozici první položka. nebo potřebuje kompletní datovou sadu k provedení cokoli užitečného.

## <a name="when-to-use-repeated-fields"></a>Kdy použít `repeated` pole

Pro libovolnou datovou sadu, která má omezení velikosti a která se dá v celém rozsahu generovat v krátkém čase – řekněme, že v rámci jedné sekundy byste měli použít `repeated` pole v běžné Protobuf zprávě. Například v systému elektronického obchodování je sestavení seznamu položek v rámci objednávky pravděpodobně rychlé a seznam nebude velmi velký. Vrácení jedné zprávy s `repeated` polem je pořadí, které je rychlejší, než `stream` použití a způsobí méně zatížení sítě.

Pokud klient potřebuje všechna data před zahájením zpracování a datová sada je dostatečně malá, aby mohla vytvořit paměť, pak zvažte použití `repeated` pole, a to i v případě, že skutečným vytvořením datové sady v paměti na serveru je pomalejší.

## <a name="when-to-use-stream-methods"></a>Kdy použít `stream` metody

Datové sady, kde jsou objekty zpráv potenciálně velmi velké, jsou nejlépe převáděny pomocí požadavků na streamování nebo odpovědí. Je efektivnější vytvořit rozsáhlý objekt v paměti, zapsat ho do sítě a pak uvolnit prostředky. Tento přístup vám pomůže zlepšit škálovatelnost vaší služby.

Podobně by měly být datové sady bez omezení velikosti odesílány přes proudy, aby při sestavování nedocházelo k vynechání paměti.

U datových sad, kde je možné každou jednotlivou položku zpracovat odděleně od příjemce, byste měli zvážit použití datového proudu, pokud to znamená, že je možné určit jeho průběh koncovému uživateli. To může zlepšit zdánlivou odezvu aplikace, i když by se to mělo vyrovnávat s celkovým výkonem aplikace.

Další scénář, ve kterém mohou být datové proudy užitečné, je zpracování zprávy napříč více službami. Pokud každá služba v řetězci vrátí datový proud, pak Terminálová služba (tj. poslední v řetězu) může začít vracet zprávy, které je možné zpracovat a předat zpátky v rámci řetězce původnímu žadateli, který může buď vrátit datový proud nebo agregovat výsledky do jediné zprávy odpovědi. Tento přístup se dobře hodí ke vzorům, jako je mapa nebo zmenšení.

>[!div class="step-by-step"]
>[Předchozí](migrate-duplex-services.md)
>[Další](client-libraries.md)
