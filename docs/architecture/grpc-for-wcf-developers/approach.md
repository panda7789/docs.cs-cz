---
title: Jak gRPC přistupuje k RPC – gRPC pro vývojáře WCF
description: Porovnání klíčových funkcí WCF a gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 65d61c8246569d81dfec3aeb8e3df4bea26258dc
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184601"
---
# <a name="how-grpc-approaches-rpc"></a>Jak gRPC přistupuje k RPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Windows Communication Foundation (WCF) a gRPC jsou implementace vzoru *vzdáleného volání procedur* (RPC), jehož cílem je volat služby běžící na jiném počítači nebo v jiném procesu bez problémů pracovat, jako kdyby byly jen volání metod v klientské aplikaci. I když jsou cíle WCF a gRPC stejné, podrobnosti implementace se poměrně liší.

Následující tabulka obsahuje informace o tom, jak se klíčové funkce WCF vztahují k gRPC a kde najdete podrobnější vysvětlení ve zbývající části knihy.

| Funkce | WCF | gRPC |
| -------- | --- | ---- |
| Cíle | Oddělení podnikového kódu od implementace sítě | Oddělení obchodních kódů od definice rozhraní a implementace sítě |
| Definování služeb a zpráv (kapitola 3-4)  | Kontrakt služby, kontrakt operace a data kontraktu | K deklarování služeb a zpráv používá soubor. |
| Jazyk (kapitola 3-5) | Smlouvy napsané C# nebo Visual Basic | Jazyk vyrovnávací paměti protokolu |
| Formát vedení (kapitola 3) | Konfigurovatelné, včetně SOAP/XML, prostého formátu XML, JSON, .NET binary a tak dále. | Binární formát vyrovnávací paměti protokolu (i když je možné použít jiné formáty).
| Interoperabilita (kapitola 4) | Při použití protokolu SOAP přes protokol HTTP | Oficiální podpora: .NET, Java, Python, JavaScript, C/C++, přejít, Rust, Ruby, SWIFT, DART, php. Neoficiální podpora jiných jazyků od komunity. |
| Sítě (kapitola 4) | Nakonfigurováno za běhu. Přepínejte mezi protokoly TCP, HTTP, MSMQ atd. | Vždycky HTTP/2 |
| Přístup (kapitola 4) | Generování/Deserialization serializace a kódu sítě v základních třídách za běhu | Generování serializace/Deserialization a kódu sítě v základních třídách během sestavení |
| Zabezpečení (kapitola 6) | Ověřování, WS-Security, šifrování zpráv | Přihlašovací údaje, ASP.NET Core zabezpečení, sítě TLS |

>[!div class="step-by-step"]
>[Předchozí](grpc-overview.md)
>[Další](interface-definition-language.md)
