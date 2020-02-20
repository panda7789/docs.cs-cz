---
title: Vazby a přenosy WCF – gRPC pro vývojáře WCF
description: Přečtěte si, jak se liší vazby WCF a přenosy na gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: ebe324eace8f5f418b920c59f6d72eaaa686ef02
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503353"
---
# <a name="wcf-bindings-and-transports"></a>Vazby a přenosy WCF

Windows Communication Foundation (WCF) obsahuje předdefinované *vazby* , které určují různé síťové protokoly, formáty drátů a další podrobnosti implementace. gRPC má efektivně jenom jeden síťový protokol a jeden formát drátu. (Technicky můžete *přizpůsobit formát* drátu, ale to je nad rámec této knihy.) Pravděpodobně zjistíte, že gRPC nabízí nejlepší řešení ve většině případů. 

Níže je Stručná diskuze o nejrelevantnějších vazbách WCF a jejich porovnání s jejich ekvivalenty v gRPC.

## <a name="nettcp"></a>NetTCP

NetTCP vazba WCF umožňuje trvalá připojení, malé zprávy a obousměrné zasílání zpráv. Ale funguje jenom mezi klienty rozhraní .NET a servery. gRPC umožňuje stejné funkce, ale podporuje se v různých programovacích jazycích a platformách. 

gRPC má mnoho funkcí vazby NetTCP WCF, ale nejsou vždy implementovány stejným způsobem. Například v technologii WCF je šifrování řízeno prostřednictvím konfigurace a zpracovává se v rámci rozhraní. V gRPC se šifrování dosahuje na úrovni připojení prostřednictvím protokolu HTTP/2 přes TLS.

## <a name="http"></a>HTTP

Vazba WCF s názvem BasicHttpBinding je obvykle založená na textu a používá protokol SOAP jako formát drátu. V porovnání s vazbou NetTCP je pomalé. Obecně se používá k zajištění vzájemné funkční spolupráce mezi platformami nebo připojení přes internetovou infrastrukturu. 

Ekvivalent v gRPC používá protokol HTTP/2 jako podkladovou přenosovou vrstvu pro zprávy ve formátu binárního Protobuf. Takže může nabízet výkon na úrovni služby NetTCP a celou spolupráci mezi platformami se všemi moderními programovacími jazyky a rozhraními.

## <a name="named-pipes"></a>Pojmenované kanály

Technologie WCF poskytovala vazbu *pojmenovaných kanálů* pro komunikaci mezi procesy na stejném fyzickém počítači. První verze ASP.NET Core gRPC nepodporuje pojmenované kanály. Přidání podpory klienta a serveru pro pojmenované kanály (a doménové sokety systému UNIX) je cílem budoucí verze.

## <a name="msmq"></a>MSMQ

MSMQ je proprietární fronta zpráv Windows. Vazba WCF na službu MSMQ umožňuje "požární a zapomenuté" žádosti od klientů, které mohou být zpracovány kdykoli později. gRPC nativně neposkytuje žádné funkce fronty zpráv. 

Nejlepší alternativou je přímé použití systému zasílání zpráv, jako je Azure Service Bus, RabbitMQ nebo Kafka. To můžete implementovat pomocí klienta, který přímo do fronty umísťuje zprávy, nebo služby streamování klienta gRPC, která zprávy zařadí do fronty.

## <a name="webhttpbinding"></a>WebHttpBinding

WebHttpBinding (označované také jako služba WCF REST) s atributy `WebGet` a `WebInvoke` umožňují vyvíjet rozhraní API RESTful, která by mohla mluvit JSON v době, kdy to bylo méně běžné. Pokud máte rozhraní API RESTful vytvořené pomocí WCF REST, zvažte jeho migraci na běžnou ASP.NET Core aplikaci webového rozhraní API MVC. Tato migrace by poskytovala stejné funkce jako převod na gRPC.

>[!div class="step-by-step"]
>[Předchozí](wcf-endpoints-grpc-methods.md)
>[Další](rpc-types.md)
