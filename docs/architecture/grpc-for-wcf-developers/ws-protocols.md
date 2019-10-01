---
title: WS-* Protocols – gRPC pro vývojáře WCF
description: Kontrola protokolů WS-* podporovaných službou WCF a alternativami, které jsou k dispozici v gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: cd9af401fc46297fc0c67f5b3e5d6b34177d6a87
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184027"
---
# <a name="ws--protocols"></a>\* Protokoly WS

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Jednou ze skutečných výhod práce s Windows Communication Foundation (WCF) bylo, že se podporovalo mnoho existujících protokolů _WS-\*_  Standard. Tato část stručně popisuje, jak gRPC spravuje stejné WS-\* Protocols a diskutuje, jaké možnosti jsou k dispozici, pokud neexistuje žádná alternativa.

## <a name="metadata-exchange---ws-policy-ws-discovery-and-so-on"></a>Výměna metadat – WS-Policy, WS-Discovery atd.

Služby SOAP zveřejňují dokumenty schématu WSDL (Web Services Description Language) s informacemi, jako jsou formáty dat, operace nebo možnosti komunikace. Toto schéma se dá použít k vygenerování kódu klienta.

gRPC funguje nejlépe, když se servery a klienti generují ze stejných `.proto` souborů, ale volitelné rozšíření reflexe serveru poskytuje způsob, jak vystavit dynamické informace z běžícího serveru. Další informace naleznete v článku balíček NuGet [Grpc. reflexe](https://nuget.org/packages/Grpc.Reflection) a [reflexe serveru Grpc C# ](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) .

Protokol WS-Discovery se používá k vyhledání služeb v místní síti. služby gRPC se obecně nacházejí v systému DNS nebo v registru služby, jako je Consul nebo ZooKeeper.

## <a name="security--ws-security-ws-federation-xml-encryption-and-so-on"></a>Zabezpečení – WS-Security, WS-Federation, šifrování XML atd.

Zabezpečení, ověřování a autorizace jsou podrobněji popsány v [kapitole 6](security.md). Ale tady se zaznamená, že na rozdíl od WCF gRPC nepodporuje šifrování WS-Security, WS Federation nebo XML. I tak gRPC poskytuje vynikající zabezpečení; veškerý síťový provoz v gRPC se při použití HTTP/2 přes protokol TLS automaticky zašifruje a certifikáty x509 se můžou použít pro vzájemné ověřování klientů a serverů.

## <a name="ws-reliablemessaging"></a>WS-ReliableMessaging

gRPC neposkytuje ekvivalent WS-ReliableMessaging. Sémantika opakování by měla být zpracována v kódu, pravděpodobně u knihovny, jako je [Polly](https://github.com/App-vNext/Polly). Při spuštění v Kubernetes nebo podobných prostředích orchestrace můžou [sítě](service-mesh.md) taky pomáhat zajistit spolehlivé zasílání zpráv mezi službami.

## <a name="ws-transaction-ws-coordination"></a>WS-Transaction, WS-koordinace

Implementace distribuovaných transakcí ve službě WCF používá Windows DTC (Distributed Transaction Coordinator) nebo MSDTC. Spolupracuje se správci prostředků, kteří ho konkrétně podporují, jako jsou SQL Server, MSMQ nebo systémy souborů Windows. V rámci moderních mikroslužeb na světě se v části kvůli širší škále používaných technologií nerovná. Diskuzi o transakcích naleznete v [příloze a](appendix.md).

>[!div class="step-by-step"]
>[Předchozí](error-handling.md)
>[Další](migrate-wcf-to-grpc.md)