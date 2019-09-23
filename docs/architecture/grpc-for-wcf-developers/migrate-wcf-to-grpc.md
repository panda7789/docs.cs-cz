---
title: Migrace řešení WCF do gRPC-gRPC pro vývojáře WCF
description: Postup migrace různých typů služby WCF na ekvivalent v gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a9cfb87361194d998a3c4dfff4fe434be64f0d65
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184293"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a>Migrace řešení WCF do gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

V této kapitole se dozvíte, jak pracovat s projekty ASP.NET Core 3,0 gRPC a předvádíme migraci různých typů služeb WCF na gRPC ekvivalent:

- Vytvořte projekt ASP.NET Core 3,0 gRPC.
- Jednoduché operace požadavek-odpověď na gRPC unárního RPC.
- Jednosměrné operace pro gRPC streamování klientů RPC
- Plně duplexní služby pro gRPC obousměrného streamování RPC.

Existuje také porovnání používání služby streamování a opakujících se polí pro vracení datových sad a použití klientských knihoven na konci kapitoly.

Ukázková aplikace WCF je minimální zástupná procedura sady burzovních obchodních služeb s použitím open source knihovny kontejnerů IoC (inverze Control) s názvem *Autofac* pro vkládání závislostí. Zahrnuje tři služby, jeden pro každý typ služby WCF. V následujících částech jsou popsány podrobné informace o službách. Řešení je možné stáhnout z [RendleLabs/grpc-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) na GitHubu. Služby používají falešná data k minimalizaci externích závislostí.

Ukázky zahrnují implementace WCF a gRPC každé služby.

>[!div class="step-by-step"]
>[Předchozí](ws-protocols.md)
>[Další](create-project.md)
