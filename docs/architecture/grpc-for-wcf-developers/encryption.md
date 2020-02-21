---
title: Šifrování a zabezpečení sítě – gRPC pro vývojáře WCF
description: Některé poznámky k zabezpečení sítě a šifrování v gRPC
ms.date: 09/02/2019
ms.openlocfilehash: f8a7aeaf2a65e4ff56ac33d728e40f09a436f7a6
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542765"
---
# <a name="encryption-and-network-security"></a>Šifrování a zabezpečení sítě

Model zabezpečení sítě pro Windows Communication Foundation (WCF) je rozsáhlý a složitý. Zahrnuje zabezpečení na úrovni přenosu pomocí protokolu HTTPS nebo TLS-over-TCP a zabezpečení na úrovni zpráv pomocí specifikace WS-Security k šifrování jednotlivých zpráv.

gRPC ponechá zabezpečené sítě k základnímu protokolu HTTP/2, který můžete zabezpečit pomocí certifikátů TLS.

Webové prohlížeče zachází s používáním připojení TLS pro HTTP/2, ale u většiny programových klientů, včetně. `HttpClient`netto můžou používat HTTP/2 přes nešifrovaná připojení. `HttpClient` vyžaduje šifrování ve výchozím nastavení, ale můžete ho přepsat pomocí přepínače <xref:System.AppContext>.

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

U veřejných rozhraní API byste měli vždycky používat připojení TLS a poskytovat platné certifikáty pro vaše služby od správné autority SSL. [LetsEncrypt](https://letsencrypt.org) poskytuje bezplatné, automatizované certifikáty SSL a většina hostování infrastruktury dnes podporuje standard LetsEncrypt s běžnými moduly plug-in a rozšířeními.

Pro interní služby v podnikové síti byste měli i nadále zvážit použití protokolu TLS k zabezpečení síťového provozu do a z vašich služeb gRPC.

Pokud potřebujete použít explicitní protokol TLS mezi službami běžícími v Kubernetes, zvažte použití certifikační autority v clusteru a řadiče správce certifikátů, jako je například [správce](https://docs.cert-manager.io/en/latest/)certifikátů. Pak můžete automaticky přiřadit certifikáty ke službám v době nasazení.

>[!div class="step-by-step"]
>[Předchozí](channel-credentials.md)
>[Další](grpc-in-production.md)
