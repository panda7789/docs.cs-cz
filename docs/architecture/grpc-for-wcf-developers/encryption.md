---
title: Šifrování a zabezpečení sítě – gRPC pro vývojáře WCF
description: Některé poznámky k zabezpečení sítě a šifrování v gRPC
ms.date: 09/02/2019
ms.openlocfilehash: fd993a2d75e97011c6c92cee02c24c5358a211ad
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967776"
---
# <a name="encryption-and-network-security"></a>Šifrování a zabezpečení sítě

Model zabezpečení sítě WCF je rozsáhlý a složitý, včetně zabezpečení na úrovni přenosu pomocí protokolu HTTPS nebo TLS-over-TCP a zabezpečení na úrovni zpráv pomocí specifikace WS-Security k šifrování jednotlivých zpráv.

gRPC ponechá zabezpečenou síť k základnímu protokolu HTTP/2, který je možné zabezpečit pomocí běžných certifikátů TLS.

Webové prohlížeče zachází s používáním připojení TLS pro HTTP/2, ale u většiny programových klientů, včetně. `HttpClient`netto můžou používat HTTP/2 přes nešifrovaná připojení. `HttpClient` *vyžaduje* šifrování ve výchozím nastavení, ale můžete ho přepsat pomocí přepínače <xref:System.AppContext>.

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

U veřejných rozhraní API byste měli vždycky používat připojení TLS a poskytovat platné certifikáty pro vaše služby od správné autority SSL. [LetsEncrypt](https://letsencrypt.org) poskytují bezplatné, automatizované certifikáty SSL a většina hostování infrastruktury dnes podporuje standard LetsEncrypt s běžnými moduly plug-in a rozšířeními.

Pro interní služby v podnikové síti byste měli i nadále zvážit použití protokolu TLS k zabezpečení síťového provozu do a z vašich služeb gRPC.

Komunikace mezi mikroslužbami v clusteru, jako je Kubernetes nebo Docker Swarm, je obecně automaticky šifrovaná pomocí síťové vrstvy kontejneru, takže implementace TLS v službách, které běží výhradně v takovém clusteru, není nutná. V části "síť služby" v další kapitole bude tento předmět další.

Pokud potřebujete použít explicitní protokol TLS mezi službami běžícími v Kubernetes, zvažte použití certifikační autority v clusteru a řadiče správce certifikátů, jako je například [správce](https://docs.cert-manager.io/en/latest/) certifikátů k přiřazení automatických certifikátů službám v době nasazení.

>[!div class="step-by-step"]
>[Předchozí](channel-credentials.md)
>[Další](grpc-in-production.md)
