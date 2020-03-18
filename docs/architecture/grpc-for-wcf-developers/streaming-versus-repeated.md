---
title: Streamovací služby vs. opakovaná pole - gRPC pro vývojáře WCF
description: Porovnejte opakovaná pole se streamovacími službami jako způsoby předávání kolekcí dat pomocí gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 542ebc393f9c9c1ad717d02d01fab33d85c18917
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147747"
---
# <a name="grpc-streaming-services-vs-repeated-fields"></a>gRPC streamingové služby vs. opakovaná pole

gRPC služby poskytují dva způsoby vrácení datových sad nebo seznamy objektů. Specifikace zprávy vyrovnávací paměti `repeated` protokolu používá klíčové slovo pro deklarování seznamů nebo polí zpráv v rámci jiné zprávy. Specifikace služby gRPC `stream` používá klíčové slovo k deklarování dlouhotrvajícího trvalého připojení. Přes toto připojení je odesíláno více zpráv a může být zpracováno jednotlivě.

`stream` Tuto funkci můžete také použít pro dlouhotrvající časová data, jako jsou oznámení nebo zprávy protokolu. Ale tato kapitola bude zvažovat jeho použití pro vrácení jedné datové sady.

Který byste měli použít, závisí na faktorech, jako jsou:

- Celková velikost datové sady.
- Čas, který trvalo vytvoření datové sady na konci klienta nebo serveru.
- Zda spotřebitel datové sady může začít na něm reagovat, jakmile je k dispozici první položka, nebo potřebuje úplnou datovou sadu, aby udělal něco užitečného.

## <a name="when-to-use-repeated-fields"></a>Kdy použít `repeated` pole

Pro všechny datové sady, které jsou omezeny na velikost a které mohou být generovány v plném rozsahu `repeated` v krátkém čase - řekněme, pod jednu sekundu - měli byste použít pole v běžné zprávě Protobuf. Například v systému elektronického obchodování je vytvoření seznamu položek v objednávce pravděpodobně rychlé a seznam nebude příliš velký. Vrácení jedné zprávy s `repeated` polem je řádově `stream` rychlejší než při použití a vznikne nižší zatížení sítě.

Pokud klient potřebuje všechna data před zahájením jejich zpracování a datová sada je dostatečně `repeated` malá, aby se vytvořila v paměti, zvažte použití pole. Zvažte to i v případě, že vytvoření datové sady v paměti na serveru je pomalejší.

## <a name="when-to-use-stream-methods"></a>Kdy použít `stream` metody

Pokud jsou objekty zpráv v datových sadách potenciálně velmi velké, je nejlepší je přenést pomocí požadavků na streamování nebo odpovědí. Je efektivnější vytvořit velký objekt v paměti, zapsat do sítě a uvolnit prostředky. Tento přístup zlepší škálovatelnost vaší služby.

Podobně byste měli odesílat datové sady bez omezení velikosti přes datové proudy, aby se zabránilo vyčerpání paměti při jejich vytváření.

Pro datové sady, kde spotřebitel může samostatně zpracovat každou položku, měli byste zvážit použití datového proudu, pokud to znamená, že průběh může být indikován uživateli. Použití datového proudu může zlepšit odezvu aplikace, ale měli byste jej vyvážit s celkovým výkonem aplikace.

Dalším scénářem, kde mohou být užitečné datové proudy, je, kde se zpracovává zpráva ve více službách. Pokud každá služba v řetězci vrátí datový proud, pak terminálová služba (to znamená poslední v řetězci) můžete začít vracet zprávy. Tyto zprávy mohou být zpracovány a předány zpět v řetězci původnímu žadateli. Žadatel může vrátit datový proud nebo agregovat výsledky do jedné zprávy odpovědi. Tento přístup se hodí dobře vzory jako MapReduce.

>[!div class="step-by-step"]
>[Předchozí](migrate-duplex-services.md)
>[další](client-libraries.md)
