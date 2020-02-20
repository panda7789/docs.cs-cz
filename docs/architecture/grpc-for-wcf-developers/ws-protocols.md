---
title: WS-* Protocols – gRPC pro vývojáře WCF
description: Kontrola protokolů WS-* podporovaných službou WCF a alternativami, které jsou k dispozici v gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: c8c06a5e23a4d7859165e1c562032055d63d76f7
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503301"
---
# <a name="ws--protocols"></a>Protokoly WS-\*

Jednou ze skutečných výhod práce s Windows Communication Foundation (WCF) bylo, že se podporovalo mnoho existujících protokolů standardu _WS-\*_ . Tato část stručně popisuje, jak gRPC spravuje stejné protokoly WS-\* a pojednávají, jaké možnosti jsou k dispozici, pokud neexistuje žádná alternativa.

## <a name="metadata-exchange-ws-policy-ws-discovery-and-so-on"></a>Výměna metadat: WS-Policy, WS-Discovery atd.

Služby SOAP zveřejňují dokumenty schématu WSDL (Web Services Description Language) s informacemi, jako jsou formáty dat, operace nebo možnosti komunikace. Pomocí tohoto schématu můžete vygenerovat kód klienta.

gRPC funguje nejlépe, když se servery a klienti generují ze stejných `.proto` souborů, ale volitelné rozšíření reflexe serveru poskytuje způsob, jak vystavit dynamické informace z běžícího serveru. Další informace naleznete v článku balíček NuGet [Grpc. reflexe](https://nuget.org/packages/Grpc.Reflection) a [reflexe serveru Grpc C# ](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) .

Protokol WS-Discovery se používá k vyhledání služeb v místní síti. služby gRPC se obecně nacházejí v rámci služby DNS nebo registru služby, jako je Consul nebo ZooKeeper.

## <a name="security-ws-security-ws-federation-xml-encryption-and-so-on"></a>Zabezpečení: WS-Security, WS-Federation, šifrování XML atd.

Zabezpečení, ověřování a autorizace jsou podrobněji popsány v [kapitole 6](security.md). Je to ale znamenat si, že na rozdíl od WCF gRPC nepodporuje šifrování WS-Security, WS-Federation nebo XML. I tak gRPC poskytuje vynikající zabezpečení. Veškerý síťový provoz v gRPC se při použití HTTP/2 přes protokol TLS automaticky zašifruje. Certifikáty x509 můžete použít pro vzájemné ověřování mezi klientem a serverem.

## <a name="ws-reliablemessaging"></a>WS-ReliableMessaging

gRPC neposkytuje ekvivalent WS-ReliableMessaging. Sémantika opakování by měla být zpracována v kódu, pravděpodobně u knihovny, jako je [Polly](https://github.com/App-vNext/Polly). Když pracujete v Kubernetes nebo podobných prostředích orchestrace [, může vám také](service-mesh.md) pomáhat při poskytování spolehlivého zasílání zpráv mezi službami.

## <a name="ws-transaction-ws-coordination"></a>WS-Transaction, WS-koordinace

Implementace distribuovaných transakcí WCF používá Microsoft DTC (Distributed Transaction Coordinator) (MSDTC). Spolupracuje se správci prostředků, kteří ho konkrétně podporují, jako jsou SQL Server, MSMQ nebo systémy souborů Windows. V rámci moderních mikroslužeb v současnosti není žádný ekvivalent v rámci široké škály používaných technologií. Diskuzi o transakcích naleznete v [příloze a](appendix.md).

>[!div class="step-by-step"]
>[Předchozí](error-handling.md)
>[Další](migrate-wcf-to-grpc.md)
