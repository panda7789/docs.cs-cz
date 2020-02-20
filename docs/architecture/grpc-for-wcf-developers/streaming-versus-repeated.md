---
title: Služby streamování vs. opakující se pole – gRPC pro vývojáře WCF
description: Porovnejte opakující se pole se službami streamování jako způsoby předávání kolekcí dat pomocí gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 0e717df57ba2bb52d63a063072d8a45bf0f7e395
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503381"
---
# <a name="grpc-streaming-services-vs-repeated-fields"></a>služby streamování gRPC vs. opakující se pole

služby gRPC poskytují dva způsoby vrácení datových sad nebo seznamů objektů. Specifikace zprávy vyrovnávací paměti protokolu používá klíčové slovo `repeated` pro deklarování seznamů nebo polí zpráv v rámci jiné zprávy. Specifikace služby gRPC používá klíčové slovo `stream` k deklaraci dlouhotrvajícího trvalého připojení. Přes toto připojení se posílá více zpráv a dají se zpracovat individuálně. 

Můžete také použít funkci `stream` pro dlouhodobě běžící dočasná data, jako jsou například oznámení nebo zprávy protokolu. Ale tato kapitola bude uvažovat o použití pro vrácení jedné datové sady.

Které byste měli použít, závisí na faktorech, jako jsou:

- Celková velikost datové sady.
- Čas potřebný k vytvoření datové sady buď na straně klienta, nebo na straně serveru.
- Určuje, zda příjemce datové sady může na něm začít pracovat, jakmile bude první položka k dispozici, nebo potřebuje kompletní datovou sadu, aby provedla cokoli užitečnost.

## <a name="when-to-use-repeated-fields"></a>Kdy použít pole `repeated`

Pro libovolnou datovou sadu, která má omezení velikosti a která se dá v celém rozsahu generovat v krátkém čase – řekněme, že v rámci jedné sekundy byste měli v běžné Protobuf zprávě použít pole `repeated`. Například v systému elektronického obchodování je sestavení seznamu položek v rámci objednávky pravděpodobně rychlé a seznam nebude velmi velký. Vrácení jedné zprávy s `repeated`ovým polem je pořadí větší než při použití `stream` a dojde k menšímu zatížení sítě.

Pokud klient potřebuje všechna data před zahájením zpracování a datová sada je dostatečně malá, aby mohla vytvořit paměť, pak zvažte použití pole `repeated`. Vezměte ho i v případě, že je vytváření datové sady v paměti na serveru pomalejší.

## <a name="when-to-use-stream-methods"></a>Kdy použít metody `stream`

Když jsou objekty zpráv v datových sadách potenciálně velmi velké, je vhodné je přenést pomocí požadavků na streamování nebo odpovědí. Je efektivnější vytvořit rozsáhlý objekt v paměti, zapsat ho do sítě a pak uvolnit prostředky. Tento přístup vám pomůže zlepšit škálovatelnost vaší služby.

Podobně byste měli odeslat datové sady s neomezenou velikostí prostřednictvím datových proudů, abyste se vyhnuli nedostatku paměti při sestavování.

U datových sad, kde příjemce může samostatně zpracovat každou položku, byste měli zvážit použití datového proudu, pokud to znamená, že může být pro uživatele zjištěn průběh. Použití datového proudu může zlepšit rychlost odezvy aplikace, ale měli byste ho vyvážit proti celkovému výkonu aplikace.

Další scénář, ve kterém mohou být datové proudy užitečné, je zpracování zprávy napříč více službami. Pokud každá služba v řetězci vrátí datový proud, pak může Terminálová služba (tj. poslední v řetězu) začít vracet zprávy. Tyto zprávy lze zpracovat a předat zpět původnímu žadateli. Žadatel může buď vrátit datový proud, nebo agregovat výsledky do jediné zprávy odpovědi. Tento přístup se dobře hodí ke vzorům, jako je MapReduce.

>[!div class="step-by-step"]
>[Předchozí](migrate-duplex-services.md)
>[Další](client-libraries.md)
