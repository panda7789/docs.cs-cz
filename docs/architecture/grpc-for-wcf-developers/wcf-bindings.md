---
title: WCF vazby a přenosy - gRPC pro vývojáře WCF
description: Zjistěte, jak různé WCF vazby a přenosy v porovnání s gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 3a295268b486578c70c2c98f1d05f89070daaeb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147721"
---
# <a name="wcf-bindings-and-transports"></a>Vazby a přenosy WCF

Windows Communication Foundation (WCF) má integrované *vazby,* které určují různé síťové protokoly, formáty drátu a další podrobnosti implementace. gRPC má efektivně pouze jeden síťový protokol a jeden drátový formát. (Technicky *si můžete* přizpůsobit formát drátu, ale to je nad rámec této knihy.) Pravděpodobně zjistíte, že gRPC nabízí ve většině případů nejlepší řešení.

Co bude následovat, je krátká diskuse o nejdůležitější WCF vazby a jak se porovnávají s jejich ekvivalenty v gRPC.

## <a name="nettcp"></a>Protokol NetTCP

WCF nettcp vazby umožňuje trvalé připojení, malé zprávy a obousměrné zasílání zpráv. Ale funguje pouze mezi klienty .NET a servery. gRPC umožňuje stejné funkce, ale je podporován napříč více programovacími jazyky a platformami.

gRPC má mnoho funkcí WCF NetTCP vazby, ale nejsou vždy implementovány stejným způsobem. Například v WCF šifrování je řízenprostřednictvím konfigurace a zpracovány v rámci. V gRPC je šifrování dosaženo na úrovni připojení přes HTTP/2 přes TLS.

## <a name="http"></a>HTTP

WCF vazby s názvem BasicHttpBinding je obvykle založen na textu a používá SOAP jako formát drátu. Je to pomalé ve srovnání s NetTCP vazby. Obvykle se používá k zajištění interoperability napříč platformami nebo připojení přes internetovou infrastrukturu.

Ekvivalent v gRPC používá HTTP/2 jako základní transportní vrstvu s binárním formátem Protobuf drátu pro zprávy. Takže může nabídnout výkon na úrovni služeb NetTCP a plnou interoperabilitu napříč platformami se všemi moderními programovacími jazyky a frameworky.

## <a name="named-pipes"></a>Pojmenované kanály

WCF za *předpokladu, pojmenované kanály* vazby pro komunikaci mezi procesy na stejném fyzickém počítači. První vydání ASP.NET Core gRPC nepodporuje pojmenované kanály. Přidání podpory klienta a serveru pro pojmenované kanály (a sokety domény Unix) je cílem pro budoucí verzi.

## <a name="msmq"></a>MSMQ

Služba MSMQ je proprietární fronta zpráv systému Windows. WCF je vazba na službu MSMQ umožňuje "požární a zapomenout" požadavky od klientů, které mohou být zpracovány kdykoli v budoucnu. gRPC neposkytuje nativně žádné funkce fronty zpráv.

Nejlepší alternativou je přímé použití systému zasílání zpráv, jako je Azure Service Bus, RabbitMQ nebo Kafka. Můžete implementovat s klientem umístění zpráv přímo do fronty nebo gRPC klienta streamování služby, která zařadí zprávy.

## <a name="webhttpbinding"></a>Vazba na webhttp

WebHttpBinding (také známý jako WCF `WebGet` `WebInvoke` REST), s atributy a, umožnil ovývojit RESTful rozhraní API, která by mohla mluvit JSON v době, kdy to bylo méně časté. Pokud máte restful rozhraní API vytvořené s WCF REST, zvažte migraci do běžné ASP.NET aplikace Core MVC Web API. Tato migrace by poskytovala stejné funkce jako převod na gRPC.

>[!div class="step-by-step"]
>[Předchozí](wcf-endpoints-grpc-methods.md)
>[další](rpc-types.md)
