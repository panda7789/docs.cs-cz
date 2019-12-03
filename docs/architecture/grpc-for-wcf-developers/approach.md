---
title: Jak gRPC přistupuje k RPC – gRPC pro vývojáře WCF
description: Porovnání klíčových funkcí WCF a gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: b924d2f20b54de2d6476a0b27626d5dd7fd0986f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711482"
---
# <a name="how-grpc-approaches-rpc"></a>Přístup gRPC k RPC

Windows Communication Foundation (WCF) a gRPC jsou implementace vzoru *vzdáleného volání procedur* (RPC). Tento model má za cíl volat služby, které běží na jiném počítači nebo v jiném procesu, bez problémů pracovat, například volání metod v klientské aplikaci. I když jsou cíle WCF a gRPC stejné, podrobnosti implementace se poměrně liší.

Následující tabulka obsahuje informace o tom, jak se klíčové funkce WCF vztahují k gRPC a kde najdete podrobnější vysvětlení.

| Funkce | WCF | gRPC |
| -------- | --- | ---- |
| Cíle | Oddělení podnikového kódu od implementace sítě. | Oddělení obchodních kódů od definice rozhraní a implementace sítě |
| Definování služeb a zpráv (kapitoly 3-4)  | Kontrakt služby, kontrakt operace a data kontraktu. | K deklarování služeb a zpráv používá soubor. |
| Jazyk (kapitoly 3-5) | Smlouvy napsané C# nebo Visual Basic. | Jazyk vyrovnávací paměti protokolu. |
| Formát vedení (kapitola 3) | Konfigurovatelné, včetně SOAP/XML, obyčejného kódu XML, JSON a binárního souboru .NET. | Binární formát vyrovnávací paměti protokolu (i když je možné použít jiné formáty).
| Interoperabilita (kapitola 4) | Při použití protokolu SOAP přes protokol HTTP. | Oficiální podpora: .NET, Java, Python, JavaScript, C/C++, přejít, Rust, Ruby, SWIFT, DART, php. Neoficiální podpora jiných jazyků od komunity. |
| Sítě (kapitola 4) | Nakonfigurováno za běhu. Přepínání mezi NetTCP, HTTP a MSMQ. | HTTP/2, aktuálně přes protokol TCP, s ASP.NET Core gRPC. |
| Přístup (kapitola 4) | Generování za běhu serializace, deserializace a kód sítě v základních třídách. | Generování serializace, deserializace a kódu sítě v základních třídách v době sestavení. |
| Zabezpečení (kapitola 6) | Ověřování, WS-Security a šifrování zpráv. | Přihlašovací údaje, ASP.NET Core zabezpečení, sítě TLS. |

>[!div class="step-by-step"]
>[Předchozí](grpc-overview.md)
>[Další](interface-definition-language.md)
