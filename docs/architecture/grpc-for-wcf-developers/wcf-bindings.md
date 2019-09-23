---
title: Vazby a přenosy WCF – gRPC pro vývojáře WCF
description: Přečtěte si, jak se liší vazby WCF a přenosy na gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 50bac73ee68d7156fc5fed55dfffb3ba7f2de924
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184055"
---
# <a name="wcf-bindings-and-transports"></a>Vazby a přenosy WCF

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

WCF má spoustu různých předdefinovaných *vazeb* , které určují různé síťové protokoly, formáty drátů a další podrobnosti implementace. gRPC má efektivně jenom jeden síťový protokol a jeden telegrafický formát (technicky *může* být přizpůsobený síťový formát, ale je nad rámec této knihy). Pravděpodobně zjistíte, že gRPC nabízí nejlepší řešení ve většině případů. Níže je Stručná diskuze o nejdůležitějších vazbách WCF a jejich porovnání s jejich ekvivalentem v gRPC.

## <a name="nettcp"></a>NetTCP

NetTCP vazba WCF umožňuje trvalá připojení, malé zprávy a obousměrné zasílání zpráv, ale funguje jenom mezi klienty a servery .NET. gRPC umožňuje stejné funkce, ale podporuje se v různých programovacích jazycích a platformách. gRPC má mnoho funkcí vazby WCF NetTCP, i když není vždy implementováno stejným způsobem. Například v technologii WCF je šifrování řízeno prostřednictvím konfigurace a zpracovává se v rámci rozhraní. V gRPC se šifrování dosahuje na úrovni připojení pomocí protokolu HTTP/2 přes TLS.

## <a name="http"></a>HTTP

BasicHttpBinding WCF je všeobecně založené na textu, používá protokol SOAP jako formát drátu a je velmi pomalé standardy moderních síťových aplikací. Používá se jenom k zajištění interoperability mezi platformami nebo připojení přes internetovou infrastrukturu. Ekvivalent v gRPC – protože používá protokol HTTP/2 jako podkladovou transportní vrstvu s binárním formátem Protobuf pro zprávy, může nabízet NetTCP výkon na úrovni služby, ale s plnou interoperabilitou mezi platformami a všemi moderními programovacími jazyky. rozhraní.

## <a name="named-pipes"></a>Pojmenované kanály

Technologie WCF poskytovala vazbu pojmenovaných kanálů pro komunikaci mezi procesy na stejném fyzickém počítači. Pojmenované kanály nejsou v první verzi ASP.NET Core gRPC podporovány.

Mimo Windows jsou funkce poskytované pojmenovanými kanály místo toho obecně poskytovány pomocí soketů domény systému UNIX. Tyto sokety jsou běžné TCP jako sokety, které představují adresy souborového systému, `/var/run/docker.sock`například, které gRPC můžou pracovat s klientem i serverem. Pokud ve Windows potřebujete použít funkci s pojmenovanými kanály, další aktualizace Windows 10 a Windows serveru ve 2019.4. čtvrtletí přidá doménové sokety jako plně podporovanou nativní funkci v systému Windows. Proto můžou služby gRPC běžící na těchto a novějších verzích Windows (nebo na Linux) používat k používání doménových soketů místo pojmenovaných kanálů. Pokud ale tým není schopen aktualizovat na nejnovější verzi systému Windows, bude nutné použít hostitele TCP Sockets. Bezpečnostní informace týkající se používání místních soketů TCP lze řešit pomocí ověřování certifikátů mezi klientem a serverem.

## <a name="msmq"></a>MSMQ

MSMQ je proprietární fronta zpráv Windows. Vazba WCF na službu MSMQ umožňuje "požární a zapomenuté" žádosti od klientů, které mohou být zpracovány kdykoli později. gRPC nativně neposkytuje žádné funkce fronty zpráv. Nejlepší alternativou je přímé použití systému zasílání zpráv, jako je Azure Service Bus, RabbitMQ nebo Kafka. To může být implementováno pomocí klienta, který umísťuje zprávy přímo do fronty, nebo služby streamování klienta gRPC, která zprávy zařadí do fronty.

## <a name="webhttpbinding"></a>WebHttpBinding

WebHttpBinding (označované také jako WCF ReST) s `WebGet` atributy a `WebInvoke` umožňují vyvíjet ReSTful rozhraní API, která by mohla mluvit JSON v čase, kdy to bylo méně běžné než nyní. Proto pokud máte rozhraní API RESTful vytvořené pomocí WCF REST, zvažte jeho migraci do běžné ASP.NET Core aplikace webového rozhraní API MVC, která by poskytovala ekvivalentní funkce namísto převodu na gRPC.

>[!div class="step-by-step"]
>[Předchozí](wcf-endpoints-grpc-methods.md)
>[Další](rpc-types.md)
